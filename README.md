# Jim/Redis Tcl-style glob matcher

This is the glob-style string matcher `stringmatch` from [Redis](https://github.com/redis/redis)
and [Jim](https://github.com/msteveb/jimtcl), extracted as a library.

The relevant subsets of the Git revision histories for Redis, forks [Valkey](https://github.com/valkey-io/valkey)
and [KeyDB](https://github.com/Snapchat/KeyDB), Jim, and old projects by
antirez, [Visitors](https://github.com/antirez/visitors), [Strabo](https://github.com/antirez/strabo),
and [Disque](https://github.com/antirez/disque) are maintained in separate Git
branches.

Of particular note, it was vulnerable to a denial-of-service from pathological
patterns that caused exponential time complexity, until it was reported in
[CVE-2022-36021](https://nvd.nist.gov/vuln/detail/CVE-2022-36021) (and earlier
on [Hacker News](https://news.ycombinator.com/item?id=32436743)) and fixed in
[dcbfcb916](https://github.com/redis/redis/commit/dcbfcb916ca1a269b3feef86ee86835294758f84)
(String pattern matching had exponential time complexity on pathological
patterns (CVE-2022-36021) (#11858), 2023-02-28).

## License

stringmatch is made available under the BSD-3-Clause license, just as Redis was
before [changing](https://redis.io/blog/redis-adopts-dual-source-available-licensing/)
to dual (non-free) RSALv2 and SSPLv1 licenses.
