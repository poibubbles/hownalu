RFC 7636

So far my understanding is that it's the *callback URL* that receives the authorization code that is subject to compromise when a legitimate app uses a platform that shares the ability to listen to the callback URL with a malicious app. From the RFC: "The operating systems must allow a custom URI scheme to be registered by multiple applications."

..or: OAuth responds to a callback URL rather than to a client that made a request. Callback URLs may be compromised on a shared platform. A normal client-server request-response is used by the intended client *after* receiving information on the callback URL to make sure the intended client gets the token.

code challenge = b64urlencode(sha256(code verifier))

Good YouTube series: "OAuth 2.0 tutorial | OAuth flows" Jan Goebel