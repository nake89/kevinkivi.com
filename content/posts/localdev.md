---
title: "Local development is a joke (sometimes)"
date: 2021-10-15T15:50:00+02:00
draft: false
tags:
  [
    "localdev",
    "local development",
    "cicd",
    "development",
    "software development",
  ]
---

Local development has many benefits. When you can edit something computer and see the changes immediately (hot-reload), it makes the feedback loop smaller and makes development that much faster. Different toolkits have different ways of trying to solve local dev. Serverless Offline is a plugin for the Serverless Framework simulates AWS Lambda and other serverless providers to give a working offline version of that serverless app you are trying to create. So instead of calling e.g. `https://12312321.execute-api.eu-north-1.amazonaws.com/dev` you would call `http://localhost:3000/`. There is LocalStack which will emulate the whole AWS ecosystem. And most front-end frameworks have some sort of hot-reload enabled toolkit.

I still use Serverless Offline to this day. But more and more I simply deploy straight to AWS Lambda. It used to take up to 10 minutes to deploy, where now it is probably a minute or two. There are issues with serverless offline. The issue is that it is running locally and simply emulates Lambda. It is not Lambda. It will sometimes behave differently and for me it is no longer worth it. I would rather run it in as similar to production environment as I can to get accurate results.

When I do front-end dev, I no longer run a local instance. I have one script, that build, uploads and does cache invalidation. And it takes less than 10 seconds. No more allowing localhost for CORS (or even worse everything). Everything is running in the cloud as close to production because it is running on the same provider, just on a different stage (dev instead of production).

Now maybe that is not enough reason for you to abandon local development. And I agree this is a matter of opinion. But let's dive deeper. Let's say you are running development software that requires a license that calls back home. We run our main software (which is licensed), several plugins (which are licensed and call home). This means I have to pay for separate localdev and development licenses. One to run in local dev and the other at wherever our servers are hosted (and when this project matures, also QA and prod). It does not end there. I have to open firewall ports for the dev server and my local dev, which is behind DCHP IP, so IP changed lots, which I have to constantly update to our main software provider and the numerous plugins. At this point, I can say trying to emulate a whole ecosystem on one localdev is utter horseshit, a pain and worst of all that localdev environment will not match the actual dev server to satisfy anybody's needs (well maybe your setup is good enough for you).
