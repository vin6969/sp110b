# code
```
#include <assert.h>
#include "compiler.h"

int E();
void STMT();
void IF();
void BLOCK();

int tempIdx = 0, labelIdx = 0;

#define nextTemp() (tempIdx++)
#define nextLabel() (labelIdx++)
#define emit printf

int isNext(char *set) {
  char eset[SMAX], etoken[SMAX];
  sprintf(eset, " %s ", set);
  sprintf(etoken, " %s ", tokens[tokenIdx]);
  return (tokenIdx < tokenTop && strstr(eset, etoken) != NULL);
}

int isEnd() {
  return tokenIdx >= tokenTop;
}

char *next() {
  // printf("token[%d]=%s\n", tokenIdx, tokens[tokenIdx]);
  return tokens[tokenIdx++];
}

char *skip(char *set) {
  if (isNext(set)) {
    return next();
  } else {
    printf("skip(%s) got %s fail!\n", set, next());
    assert(0);
    
  }
}

// F = (E) | Number | Id
int F() {
  int f;
  if (isNext("(")) { // '(' E ')'
    next(); // (
    f = E();
    next(); // )
  } else { // Number | Id
    f = nextTemp();
    char *item = next();
    emit("t%d = %s\n", f, item);
  }
  return f;
}

// E = F (op E)*
int E() {
  int i1 = F();
  while (isNext("+ - * / & | ! < > =")) {
    char *op = next();
    int i2 = E();
    int i = nextTemp();
    emit("t%d = t%d %s t%d\n", i, i1, op, i2);
    i1 = i;
  }
  return i1;
}

// ASSIGN = id '=' E;
void ASSIGN() {
  char *id = next();
  skip("=");
  int e = E();
  skip(";");
  emit("%s = t%d\n", id, e);
}

// WHILE = while (E) STMT
void WHILE() {
  int whileBegin = nextLabel();
  int whileEnd = nextLabel();
  emit("(L%d)\n", whileBegin);
  skip("while");
  skip("(");
  int e = E();
  emit("if not t%d goto L%d\n", e, whileEnd);
  skip(")");
  STMT();
  emit("goto L%d\n", whileBegin);
  emit("(L%d)\n", whileEnd);
}

void dow() {
  int dowBegin = nextLabel();
  int dowEnd = nextLabel();
  emit("(L%d)\n", dowBegin);
  skip("do");
  STMT();
  skip("while");
  skip("(");
  int e = E();
  emit("if not t%d goto L%d\n", e, dowEnd);
  skip(")");
  skip(";");
  emit("goto L%d\n", dowBegin);
  emit("(L%d)\n", dowEnd);
}

// STMT = WHILE | BLOCK | ASSIGN
void STMT() {
  if (isNext("while"))
    WHILE();
  else if (isNext("do"))
    dow();
  else if (isNext("{"))
    BLOCK();
  else
    ASSIGN();
}

// STMTS = STMT*
void STMTS() {
  while (!isEnd() && !isNext("}")) {
    STMT();
  }
}

// BLOCK = { STMTS }
void BLOCK() {
  skip("{");
  STMTS();
  skip("}");
}

// PROG = STMTS
void PROG() {
  STMTS();
}

void parse() {
  printf("============ parse =============\n");
  tokenIdx = 0;
  PROG();
}
```
# output
```
s=0;
i=1;
do {
  s = s + i;
  i = i + 1;
} while (i < 10);
========== lex ==============
token=s
token==
token=0
token=;
token=i
token==
token=1
token=;
token=do
token={
token=s
token==
token=s
token=+
token=i
token=;
token=i
token==
token=i
token=+
token=1
token=;
token=}
token=while
token=(
token=i
token=<
token=10
token=)
token=;
========== dump ==============
0:s
1:=
2:0
3:;
4:i
5:=
6:1
7:;
8:do
9:{
10:s
11:=
12:s
13:+
14:i
15:;
16:i
17:=
18:i
19:+
20:1
21:;
22:}
23:while
24:(
25:i
26:<
27:10
28:)
29:;
============ parse =============
t0 = 0
s = t0
t1 = 1
i = t1
(L0)
t2 = s
t3 = i
t4 = t2 + t3
s = t4
t5 = i
t6 = 1
t7 = t5 + t6
i = t7
t8 = i
t9 = 10
t10 = t8 < t9
if not t10 goto L1
goto L0
(L1)
```
