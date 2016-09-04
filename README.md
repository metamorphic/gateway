# gateway

A reverse proxy server that will redirect requests to the appropriate background based on URL pattern or HTTP header.

The server plays a key role in a microservices architecture by enabling sets of services within a [bounded context]() to be separately packaged and run in its own process. The gateway presents a single entry point to clients, which avoids having to encode the system topology in each client. The client can pretend its communicating with a single backend. 

    zuul:
      routes:
        forms:
          path: /api/form-schemas/**
          url: http://localhost:7005
          stripPrefix: false
        services:
          path: /api/**
          url: http://localhost:7007
          stripPrefix: false
    server.port: 7001
    logging:
      level:
        ROOT: INFO
