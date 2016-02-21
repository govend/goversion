# goversion
Identify the installed Go version at runtime.

I know what your thinking, how hard can it be to parse `$ go version`?
_Well, it depends on what you want to do_.

Some things can be difficult to do like:
* identify/support the development tip of Go
* identify/support release candidates
* do not shell out to identify the version

The `goversion` package makes it easy to identify the currently installed Go
version at runtime.
