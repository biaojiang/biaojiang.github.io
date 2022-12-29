---
layout: post
title:  "New Google domain started!"
date:   2021-03-23 22:06:00 +0100
categories: thoughts
#comments: false
math: false
---

## Root Domain

[Root domain](https://plotsignal.com) keep the same as the old blog and CV pages.

## Subdomains
* [Portfolio](https://cv.plotsignal.com) is the CV including some project info (beta version).
* [Sensor data analytics](https://msensor.plotsignal.com) is the multi-sensor data analytics project (beta version). 
* [Family journey](https://yiru.plotsignal.com) is the family life journeys (under construction).

## Host static websits with GitHub pages
[Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-a-records-with-your-dns-provider) is the full instruction on how to point the custom domain to GitHub Pages.

It only needs to set the apex domain, just create a __A__ record to point the apex domain to the IP addresses for GitHub Pages by using any one of the following 4 IP's:

1. 185.199.108.153
1. 185.199.109.153
1. 185.199.110.153
1. 185.199.111.153

There is no need to point the *www* subdomain, nowdays less people want to input *www.yourwebsite.com*. If setting the _www_ subdomain, Google Domains will add 3 records under "_DNS/Custom resource records_", making it a little mess.

:sparkles:, Now it is really easy and ready to enjoy the Google ecosystems.
