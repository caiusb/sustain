---
layout: post
title: AWS Access Keys considered harmful
date: 2014-03-06 17:13:32 -0800
categories: 
---

...or _"How I learned that today, the hard way"_.

As I was comming back from getting some groceries, I got an call for Amazon Web Services.
Somebody has started  about 20 large instances on my account.
Oh dear!
By the time I got to kill them all, they racked about $150 worth of charges.
Luckily, the nice lady who called me said they will not charge me for that.
I hope that's the case.
I'm stil waiting for a confirmation.

<!-- more -->

All of this happened probably because of a really old Access Key.
It was created in December 2012, and I haven't bothered to rotate it (the fancy term for replace).
And, I used for everything, from backups to accessing S3 via Cyberduck.
This was clearely an incident waiting to happen.
And it did.

To my defence, I did set up Two-Factor Authentication about a month ago.
But that was clearly not enough, and I forgot about the power of the root access keys.

The solution I used was to create a unique access key for each application/use using the IAM service.
This allows you to create users with well defined set of permisions.
So, if there would be a leak of one of the credentials, at least the attackers could not launch 20 large VMs on an account linked to my credit card.

Oh, and do enable billing alerts.
That should tell you straight away when the costs start to skyrocket.
It serves a good wake-up call, well before you reach the 3 or 4 digit mark.

Root access keys are bad, since you risk too much in case they are compromised.
So, if you use them, please consider retiring them.
Don't rotate.
Just delete.
They are more trouble than they are worth!

I know this may sound quite lame for a seasoned AWS user.
And it is.
But for the vast majority of us out there, who don't really want to bother too much with all this security maze, these simple tips might prove useful.