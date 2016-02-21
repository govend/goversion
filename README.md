# goversion
Identify the installed Go version at runtime.

**note: it does not work yet, it might never work, its a crazy idea**

## Why?
I know what your thinking, how hard can it be to parse `$ go version`?
_Well, it depends on what you want to do_.

If you read about the Go [runtime.Version()](https://golang.org/pkg/runtime/#Version) function, it might return a release tag name (like "go1.3") or it might return the commit hash and date at the time of the build (probably for development builds).

Some things can be difficult to do like:
* identify/support the development tip of Go
* identify/support release candidates
* do not shell out to identify the version

## How could you do this?  
Using a combination of dates, tag names, commit sha hashes, and parent sha of tagged commits from github.com/golang/go it should be possible to identify a particular version or at least make an educated guess.

In order to grab this info we use the `go generate` command to reach out to the GitHup API and download all the tag info. The file that does this is `generate.go` and it stores that info into `gotags.go`.

This `gotags.go` file theoretically would eventually also contain dates and parent sha hashes so that if `runtime.Version()` did not report back a tag, we could identify a commit parent, or make a general guess to the Go version based upon the build date.
