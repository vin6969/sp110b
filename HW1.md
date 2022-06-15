<p class="has-line-data" data-line-start="0" data-line-end="2">#include &lt;assert.h&gt;<br>
#include “compiler.h”</p>
<p class="has-line-data" data-line-start="3" data-line-end="7">int E();<br>
void STMT();<br>
void IF();<br>
void BLOCK();</p>
<p class="has-line-data" data-line-start="8" data-line-end="9">int tempIdx = 0, labelIdx = 0;</p>
<p class="has-line-data" data-line-start="10" data-line-end="13">#define nextTemp() (tempIdx++)<br>
#define nextLabel() (labelIdx++)<br>
#define emit printf</p>
<p class="has-line-data" data-line-start="14" data-line-end="20">int isNext(char *set) {<br>
char eset[SMAX], etoken[SMAX];<br>
sprintf(eset, &quot; %s &quot;, set);<br>
sprintf(etoken, &quot; %s &quot;, tokens[tokenIdx]);<br>
return (tokenIdx &lt; tokenTop &amp;&amp; strstr(eset, etoken) != NULL);<br>
}</p>
<p class="has-line-data" data-line-start="21" data-line-end="24">int isEnd() {<br>
return tokenIdx &gt;= tokenTop;<br>
}</p>
<p class="has-line-data" data-line-start="25" data-line-end="29">char *next() {<br>
// printf(“token[%d]=%s\n”, tokenIdx, tokens[tokenIdx]);<br>
return tokens[tokenIdx++];<br>
}</p>
<p class="has-line-data" data-line-start="30" data-line-end="36">char *skip(char *set) {<br>
if (isNext(set)) {<br>
return next();<br>
} else {<br>
printf(“skip(%s) got %s fail!\n”, set, next());<br>
assert(0);</p>
<p class="has-line-data" data-line-start="37" data-line-end="39">}<br>
}</p>
<p class="has-line-data" data-line-start="40" data-line-end="54">// F = (E) | Number | Id<br>
int F() {<br>
int f;<br>
if (isNext(&quot;(&quot;)) { // ‘(’ E ‘)’<br>
next(); // (<br>
f = E();<br>
next(); // )<br>
} else { // Number | Id<br>
f = nextTemp();<br>
char *item = next();<br>
emit(“t%d = %s\n”, f, item);<br>
}<br>
return f;<br>
}</p>
<p class="has-line-data" data-line-start="55" data-line-end="67">// E = F (op E)*<br>
int E() {<br>
int i1 = F();<br>
while (isNext(&quot;+ - * / &amp; | ! &lt; &gt; =&quot;)) {<br>
char *op = next();<br>
int i2 = E();<br>
int i = nextTemp();<br>
emit(“t%d = t%d %s t%d\n”, i, i1, op, i2);<br>
i1 = i;<br>
}<br>
return i1;<br>
}</p>
<p class="has-line-data" data-line-start="68" data-line-end="76">// ASSIGN = id ‘=’ E;<br>
void ASSIGN() {<br>
char *id = next();<br>
skip(&quot;=&quot;);<br>
int e = E();<br>
skip(&quot;;&quot;);<br>
emit(&quot;%s = t%d\n&quot;, id, e);<br>
}</p>
<p class="has-line-data" data-line-start="77" data-line-end="91">// WHILE = while (E) STMT<br>
void WHILE() {<br>
int whileBegin = nextLabel();<br>
int whileEnd = nextLabel();<br>
emit(&quot;(L%d)\n&quot;, whileBegin);<br>
skip(“while”);<br>
skip(&quot;(&quot;);<br>
int e = E();<br>
emit(“if not t%d goto L%d\n”, e, whileEnd);<br>
skip(&quot;)&quot;);<br>
STMT();<br>
emit(“goto L%d\n”, whileBegin);<br>
emit(&quot;(L%d)\n&quot;, whileEnd);<br>
}</p>
<p class="has-line-data" data-line-start="92" data-line-end="107">void dow() {<br>
int dowBegin = nextLabel();<br>
int dowEnd = nextLabel();<br>
emit(&quot;(L%d)\n&quot;, dowBegin);<br>
skip(“do”);<br>
STMT();<br>
skip(“while”);<br>
skip(&quot;(&quot;);<br>
int e = E();<br>
emit(“if not t%d goto L%d\n”, e, dowEnd);<br>
skip(&quot;)&quot;);<br>
skip(&quot;;&quot;);<br>
emit(“goto L%d\n”, dowBegin);<br>
emit(&quot;(L%d)\n&quot;, dowEnd);<br>
}</p>
<p class="has-line-data" data-line-start="108" data-line-end="119">// STMT = WHILE | BLOCK | ASSIGN<br>
void STMT() {<br>
if (isNext(“while”))<br>
WHILE();<br>
else if (isNext(“do”))<br>
dow();<br>
else if (isNext(&quot;{&quot;))<br>
BLOCK();<br>
else<br>
ASSIGN();<br>
}</p>
<p class="has-line-data" data-line-start="120" data-line-end="126">// STMTS = STMT*<br>
void STMTS() {<br>
while (!isEnd() &amp;&amp; !isNext(&quot;}&quot;)) {<br>
STMT();<br>
}<br>
}</p>
<p class="has-line-data" data-line-start="127" data-line-end="133">// BLOCK = { STMTS }<br>
void BLOCK() {<br>
skip(&quot;{&quot;);<br>
STMTS();<br>
skip(&quot;}&quot;);<br>
}</p>
<p class="has-line-data" data-line-start="134" data-line-end="138">// PROG = STMTS<br>
void PROG() {<br>
STMTS();<br>
}</p>
<p class="has-line-data" data-line-start="139" data-line-end="144">void parse() {<br>
printf(&quot;============ parse =============\n&quot;);<br>
tokenIdx = 0;<br>
PROG();<br>
}</p>
