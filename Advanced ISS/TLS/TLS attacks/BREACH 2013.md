BREACH (2013) deduces a secret within HTTP responses provided by a server that:
– uses HTTP compression (remember that compression can be used also at the application layer and not only with TLS);
– inserts user input into HTTP responses;
– contains a secret (e.g., a CSRF token) in the HTTP responses;