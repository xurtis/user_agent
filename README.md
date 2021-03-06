[![Build Status](https://travis-ci.org/pfernie/user_agent.svg?branch=master)](https://travis-ci.org/pfernie/user_agent)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/user_agent)

# Future direction
This project has stagnated, but perhaps can provide a foundation for future work. In particular, I beyond any of the TODO/FIXMEs listed, some thoughts. See https://github.com/seanmonstar/reqwest/issues/14 for some background/history. The work that @SergioBenitez did in https://github.com/alexcrichton/cookie-rs and related answered/solved some of the questions in the above issue, esp. w.r.t. efficiency of cookie handling. At the same time, it raised some questions for me in terms of a good direction to take this code in:

* The Cookie work largely involved decreasing/eliminating allocations with some more efficient string indexing, but I believe much of the logic in `user_agent` necessarily involves some canonicalization/normalization that would obviate this benefit. So it would make sense for this project to evolve in a way that e.g. a project like `reqwest` supporting `user_agent` doesn't have a negative impact when not needed.
* cookie-rs has a CookieJar implementation, which handles storing cookies as well as some security details, but does not aim to implement path/domain matching, etc. Does it fit into this picture anywhere? Should `CookieJar` be updated to e.g. separate out concerns like security, session management, etc.?
* Does it make more sense for `user_agent` to be something that wraps a thing like a `reqwest`/`hyper`/`curl`/etc. client, or should things like `reqwest` to "own" a session?

## License
This project is licensed and distributed under the terms of both the MIT license and Apache License (Version 2.0).

See [LICENSE-APACHE](LICENSE-APACHE) and [LICENSE-MIT](LICENSE-MIT)
