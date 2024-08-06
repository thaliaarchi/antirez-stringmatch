# antirez stringmatch

This is the Tcl-style glob matcher from Redis and Jim by Salvatore Sanfilippo,
aka antirez, extracted as a library.

It first appeared in [Jim](https://github.com/msteveb/jimtcl), a Tcl
interpreter, as an implementation of the `string match` Tcl function. It was
then [reused](https://github.com/redis/redis/issues/5632#issuecomment-446186753)
in other projects by antirez, in a succession from [Visitors](https://github.com/antirez/visitors)
to [Strabo](https://github.com/antirez/strabo), [Redis](https://github.com/redis/redis),
then [Disque](https://github.com/antirez/disque). The function has evolved
separately in Redis to fix security issues and in Jim to add features like UTF-8
support. Forks of Redis, [Valkey](https://github.com/valkey-io/valkey) and
[KeyDB](https://github.com/Snapchat/KeyDB), have not changed it. The relevant
subsets of each project's revision history are tracked in separate Git branches.

Of particular note, it was vulnerable to a denial-of-service from pathological
patterns that caused exponential time complexity, until it was reported in
[CVE-2022-36021](https://nvd.nist.gov/vuln/detail/CVE-2022-36021) (and earlier
on [Hacker News](https://news.ycombinator.com/item?id=32436743)) and fixed in
Redis in [dcbfcb916](https://github.com/redis/redis/commit/dcbfcb916ca1a269b3feef86ee86835294758f84)
(String pattern matching had exponential time complexity on pathological
patterns (CVE-2022-36021) (#11858), 2023-02-28).

## License

stringmatch is made available under the BSD-3-Clause license, just as Redis was
before [changing](https://redis.io/blog/redis-adopts-dual-source-available-licensing/)
to dual (non-free) RSALv2 and SSPLv1 licenses. Versions with lineage from other
projects may be under different licenses.
