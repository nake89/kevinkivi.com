---
title: 'Joker.com automation'
date: Sun, 09 Oct 2016 11:47:48 +0000
draft: false
tags: ['api', 'automation', 'Code', 'github', 'joker', 'joker.com', 'node', 'node.js', 'nodejs', 'npm']
---

I've been working on automation for joker.com, so that I can unlock domains and order the auth-id (epp-key, transfer key) faster. It uses the joker.com API. I wrote it in node.js. It is still in development and I will add more functionality to this application. Here is the npm page: [https://www.npmjs.com/package/joker-auto](https://www.npmjs.com/package/joker-auto) Github: [https://github.com/nake89/joker-nodejs](https://github.com/nake89/joker-nodejs)

### Joker Automation

This is a node.js script for automating Joker.com services. Still in early development. Currently only logs you in and unlocks a domain and gives you the auth-id (transfer key) of a domain.

#### Usage

##### Installation

`npm i joker-auto -g` Add your joker.com login credentials to the joker.js file.

##### Login

`joker-auto login` This command returns the temporary (1h) session id.

##### Order auth-id

`joker-auto getkey domain.com <INSERT THE SESSION ID HERE>` This will queue the auth-id order. You will have to wait a bit. You will get the queue ID here.

##### Show auth-id

`joker-auto showkey <INSERT THE QUEUE ID HERE> <INSERT THE SESSION ID HERE>` If you do this too fast. You will not get the auth-id. Patience is key.