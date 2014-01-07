---
layout: post
title: "Introducing Jackpot: Billing made easy for rails applications"
date: 2012-03-27 10:56
comments: true
published: true 
categories: opensource
---

I would like to introduce you to my new open source project: [Jackpot](https://github.com/pellegrino/jackpot). It started out @ [Mendicant University](http://mendicantuniversity.org) as my core skills project and now its going through a major overhaul to get ready to hit its primetime. 

Jackpot has pretty high ambitions, though. It aims to become the easiest way to get paid using rails. It abstracts all the nasty details about recurring payment processing and let you focus on writing your appliaction, not billing code. Billing code is a boring thing to write, so i expect you not having to do it all by yourself. 

## YUNO USE X OR Y..!?!11

There [are](http://chargify.com) [a](https://cheddargetter.com/) [lot](http://stripe.com) of great solutions available, the problem is that many of them are restricted to certain countries. Being outside US and the UK, i know how painful it is to roll your own Billing solution everytime you start a new SaaS project. Also there are people that prefer having more control about their own billing solution or might not need all the advanced functionalities these solutions provide.


There are also a few open source projects, but most are quite outdated and do not take full advantage of more current solutions. Jackpot was designed to be easily distributed via Rails Engines, so it can be mounted in any Rails 3.1 or 3.2 application. 


### Active Merchant

Jackpot also relies on the great time tested project brought up by the fantastic guys at Shopify [ActiveMerchant](https://github.com/Shopify/active_merchant). Jackpot uses it to interact with Gateways, so providing it with any Active Merchant gateway with card storage support will work. This card storage support is really important, since you will not want to do it by yourself, which would make getting PCI Compliance much harder. Jackpot does not and will not record any sort of credit card information.

Unlike Active Merchant, Jackpot was designed to provide a full yet simple  billing solution for SaaS apps, which means it takes care of subscriptions, customers and charging your customers monthly. In practice, Jackpot takes care of those details you would have to do within your application.


## Current Status

Please, be aware that this project its in a super alpha state and that there are some rough edges yet to be polished. Right now it only supports Braintree and lacks features such as Invoicing and Mailing. Currently, you can use it to create your subscriptions, track your customers and processing monthly payment using a Cron process ready to roll. 

You can see the source code at [http://github.com/pellegrino/jackpot](http://github.com/pellegrino/jackpot) and also see a little rails 3.2 [demo application](http://github.com/pellegrino/jackpot-demo).

I hope you like the project and that it may be useful to you as well. Your feedback is highly appreciated, leave your comments below or feel free to reach me at IRC. My username is _pellegrino_ @freenode and i'm happy to help. 

Stay tuned for more!
