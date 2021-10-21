https://hapi-websocket-test.herokuapp.com/
ws://hapi-websocket-test.herokuapp.com/

OK - wscat --connect ws://hapi-websocket-test.herokuapp.com/baz
OK - wscat --connect ws://localhost:12345/baz

FAIL - wscat --subprotocol "quux/1.0" --auth foo:bar --connect ws://hapi-websocket-test.herokuapp.com/quux
(invalid protocol)

OK - wscat --connect ws://hapi-websocket-test.herokuapp.com/framed



# ------------------------------------------

https://rtc-api-server.herokuapp.com/
ws://rtc-api-server.herokuapp.com/

ws://localhost:8000/socket/AAAAAAAA

503 - wscat --connect ws://rtc-api-server.herokuapp.com/missing_socket_route
503 - wscat --connect ws://rtc-api-server.herokuapp.com/socket/AAAAAAAA

OK - wscat --connect ws://localhost:8000/socket/AAAAAAAA
OK - wscat --connect ws://localhost:8000/baz1

Notes: 
Missing routes give the same error if they are missing(invisible)



# ---------------------------
# Jsut requests:
curl -X POST --header 'Content-type: application/json' --data '{ "foo": 42 }' http://localhost:8000/baz1
curl -X POST --header 'Content-type: application/json' --data '{ "foo": 42 }' https://rtc-api-server.herokuapp.com/baz1