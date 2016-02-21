# goversion
Identify the installed Go version at runtime.

**note: it does not work yet, it might never work, its a crazy idea**

## Why?
I know what your thinking, how hard can it be to parse `$ go version`?
_Well, it depends on what you want to do_.

If you read about the Go [runtime.Version](https://golang.org/pkg/runtime/#Version) function, it might return a release tag name (like "go1.3") or it might return the commit hash and date at the time of the build (probably for development builds).

Some things can be difficult to do like:
* identify/support the development tip of Go
* identify/support release candidates
* do not shell out to identify the version

## How could you do this?  
Using a combination of dates, tag names, commit sha hashes, and parent sha of tagged commits from github.com/golang/go it should be possible to identify a particular version or at least make an educated guess.

The `goversion` package makes it easy to identify the currently installed Go
version at runtime.
