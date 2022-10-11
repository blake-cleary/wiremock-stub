wiremock-stub
==================================

WireMock: The flexible tool for building mock APIs. (https://wiremock.org/)

With WireMock we are able to stub requests and responses via JSON files.

Local Development Environment
-----------------------------

#### Change the window.entry_url to point to the WireMock service rather than Entry Service in AWS

public/index.html
```
window.entry_url = "http://localhost:8080/entry/";
```

#### Start Local Environment

This will bring up WireMock on port 8080.

```
docker-compose -f docker-compose.yml up
```

#### Stop Local Environment

```
docker-compose down --rmi local -v
```

#### Restart Local Environment

This command is very helpful if you are actively manipulating the json data. Run this command
rather than stopping the container and starting it again for new json data changes to take effect.

```
docker-compose -f docker-compose.yml restart wiremock
```

#### Verify Mocked Data

This will show you a detailed list of all mocked mappings
```
curl http://localhost:8080/__admin
```

You could also simply visit this url in your browser to see the same data http://localhost:8080/__admin

To see the result of visiting an endpoint visit the url http://localhost:8080 + the
request url defined in a mapping file.

For instance, the file mappings/entry.json defines the request > url as "/entry/". Therefore, you would visit
http://localhost:8080/entry/ to get the mocked response (__files/entry.json).

#### Inspiring Links (Helpful Documentation and General Overview of Purpose)

Helpful Documentation:
* https://wiremock.org/docs/stubbing/
* https://wiremock.org/docs/request-matching/
* https://wiremock.org/docs/response-templating/

General Overview of Purpose:
* https://blog.muya.co.ke/wiremock-response-templating/
* https://medium.com/@jw_ng/mocking-with-wiremock-and-docker-1f1601bd10e4
