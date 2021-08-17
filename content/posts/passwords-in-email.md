---
title: "Passwords in Email"
date: 2021-08-17T18:28:00+02:00
draft: false
tags: ["password", "plaintext", "hash", "information security"]
---

It happened again. I created an account to a service (a domain registrar) and their welcome email contained the password I just gave them. You might think that that is fine, because _maybe_ they didn't store that password plain text in their DB. Maybe they hashed it. If you are confused about what _hashing_ means, then read this [auth0 article](https://auth0.com/blog/hashing-passwords-one-way-road-to-security/).
Hashing in short: Normally passwords are stored in the database in a cryptographically secure manner, called a hash. This hash cannot be reversed to the password. Unless bruteforced, the stronger the password, the longer it will take, potentially up to tens/hundreds of thousands years (hashing algorithm and salting also can affect the difficulty in bruteforcing). This means that if somebody hacks the database, the attacker wont get all the customers' passwords.
Now why do I care that they sent me my password when I registered. Well first off, I don't need the password. I mean, I just gave it to them. It shows me that they think the correct way to send the customer a password is plain text to the email (Email is not a good place to store passwords!). Do they also do this when I ask for password reset? If they do they have the password stored as plain text. I never got that far with this service provider. I just quit using their services immediately.
Another service was a pizzeria. I wanted to order a pizza from them. I remembered that I had created an account with them a long time ago. So I asked for a password reset. I gave them my email address. To my absolute shock, the password I used to use years ago popped right into my inbox.
Since the early 2000s, when I first started developing software we were told to always hash our passwords and never store plaintext passwords. And the fact that this still happens to this day, is quite frankly inexcusable (even if it _just_ a pizzeria). People shouldn't use the same password, but they do sometimes. This means that hackers can now try to login to Facebook, Google, etc with the credentials. This is why it is important to use a password manager.
I use 1password, because it supports multiple devices, browsers and operating systems. I am in no way affiliated with them. I just enjoy their services. But you can use any other one you like. There are free and paid options. KeePass and derivatives are free and open source. Lastpass is a cloudhosted one that has a free option. 1password is the only one that works for Linux+Firefox and Android+Firefox combo. This is great for me because I prefer to use Firefox and linux based operating systems.

Moral of this story: Never, ever, use the same password in many services. Always use a password manager. Even big companies like Yahoo has stored plaintext passwords. **Trust. No. One.**
