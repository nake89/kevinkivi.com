---
title: "Fix Certificate error with wget"
date: Sat, 22 Apr 2017 21:55:18 +0000
draft: false
tags: ["Guides"]
---

So, you are unable to download from https sources with wget. Instead you get the following error.

```
ERROR: The certificate of \`www.google.com' is not trusted.
ERROR: The certificate of \`www.google.com' hasn't got a known issuer.
```

No problemo. This error is most likely occurring for missing root certificates. Simply install the ca-certificates package:

```
sudo apt-get install ca-certificates
```

This should work on Ubuntu and Debian derivatives.
