# antirez stringmatch

This is the Tcl-style glob matcher from Redis and Jim by Salvatore Sanfilippo
(“antirez”), extracted as a library.

It first appeared in the Jim Tcl interpreter as its implementation of the
`string match` Tcl function. It was then [reused](https://github.com/redis/redis/issues/5632#issuecomment-446186753)
in several other projects by antirez, with each apparently copying the function
from the previous. The function has evolved separately in Redis to fix security
issues and in Jim to add features like UTF-8 support. Forks of Redis have not
changed it besides cosmetic updates.

Projects using this string matcher:
- [Jim](https://github.com/msteveb/jimtcl) (2005, BSD-2-Clause):
  Tcl interpreter originally by antirez
- [Visitors](https://github.com/antirez/visitors) (2006, GPL-2.0,
  then BSD-3-Clause): web log analyzer by antirez
- [Strabo](https://github.com/antirez/strabo) (c. 2008, BSD-3-Clause):
  elevation map 2D and 3D modeler by antirez
- [Redis](https://github.com/redis/redis) (2009, BSD-3-Clause,
  then RSALv2/SSPLv1, then RSALv2/SSPLv1/AGPLv3):
  in-memory key/value database originally by antirez
- [Disque](https://github.com/antirez/disque) (2014, BSD-3-Clause)
  in-memory distributed job queue by antirez, based on Redis
- [KeyDB](https://github.com/Snapchat/KeyDB) (2019, BSD-3-Clause):
  multithreaded fork of Redis owned by Snapchat
- [Valkey](https://github.com/valkey-io/valkey) (2024, BSD-3-Clause):
  open source fork of Redis maintained by the Linux Foundation

The relevant subsets of each project's revision history are tracked in separate
Git branches.

Notably, it was vulnerable to a denial-of-service from pathological
patterns that triggered exponential time complexity, until it was reported in
[CVE-2022-36021](https://nvd.nist.gov/vuln/detail/CVE-2022-36021) (and earlier
on [Hacker News](https://news.ycombinator.com/item?id=32436743)) and fixed in
Redis commit [dcbfcb916](https://github.com/redis/redis/commit/dcbfcb916ca1a269b3feef86ee86835294758f84)
(2023-02-28).

## License

stringmatch is made available under the BSD-3-Clause license, maintaining the
original license of Redis before it [changed](https://redis.io/blog/redis-adopts-dual-source-available-licensing/)
to tri-license RSALv2, SSPLv1, and [AGPLv3](https://redis.io/blog/agplv3/). As
`util.c` retains its original license header, it [remains available](https://github.com/redis/redis/blob/unstable/REDISCONTRIBUTIONS.txt)
under BSD-3-Clause and upstream changes to it have been cherry-picked here.

Other branches have versions of the string matcher with lineage from other
projects and may be under different licenses (listed above).
