## Building the Server

Just like with the HTTP client, we can build this example by doing the following on the shell:
```
$ cd ~/cpp-netlib
$ g++ -o hello_world_server \
>     libs/network/example/http/hello_world_server.cpp \
>     -I$BOOST_ROOT                                    \
>     -I.                                              \
>     -L$BOOST_ROOT/stage/lib                          \
>     -lboost_system                                   \
>     -pthread
```
#### shell
```
shell$ ./hello_world_server 0.0.0.0 8000
```


### creating a simple HTTP Server in C++ using cpp-netlib.

```
#include <boost/network/protocol/http/server.hpp>
#include <string>
#include <iostream>

namespace http = boost::network::http;

struct hello_world;
typedef http::server<hello_world> server;

struct hello_world {
    void operator() (server::request const &request,
                     server::response &response) {
        std::string ip = source(request);
        response = server::response::stock_reply(
            server::response::ok, std::string("Hello, ") + ip + "!");
    }
};

int
main(int argc, char * argv[]) {

    if (argc != 3) {
        std::cerr << "Usage: " << argv[0] << " address port" << std::endl;
        return 1;
    }

    try {
        hello_world handler;
        server server_(argv[1], argv[2], handler);
        server_.run();
    }
    catch (std::exception &e) {
        std::cerr << e.what() << std::endl;
        return 1;
    }

    return 0;
}
```

#### source
https://cpp-netlib.org/0.9.2/hello_world_server.html




