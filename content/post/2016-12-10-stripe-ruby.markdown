---
title: "Accepting payments with Stripe and Ruby on Rails"
date: 2015-08-07T21:56:46Z
draft: false
url: /blog/2016/12/10/stripe-ruby/
categories: []
---

Global digital currencies such as Bitcoin are disrupting online commerce and the landscape of digital payments is going to undergo a lot of change in the next decade. This reflects a popular use of the internet: to pass bits back and forth that represent transactions in exchange for goods and services.

Buying things on the internet and getting billed for subscriptions is ubiquitous in our day to day lives. Yet, building a site that accepts traditional payment methods can be a daunting task. Dealing with redirects, logins, and checkouts with PayPal API can be a huge pain– but fear not! I will walk through the basic structure of an ecommerce site and then implement an application with Stripe subscription billing and an application with the Hello World of payments: Stripe Checkout for Rails.

####Why Ruby on Rails and Stripe?

Stripe's products are easy to use, well documented, have clear cut pricing, integrate easily into Rails applications, and are arguably the most straightforward way to learn how to handle online payments. They currently offer an [API](https://stripe.com/docs/api/) and full-featured [checkout](https://stripe.com/docs) handled by Stripe. [Ruby on Rails](http://rubyonrails.org/) is a database agnostic, robust, opinionated web development framework with a large community behind it and many resources in which to learn and contribute.

####How ecommerce sites work

* Membership sites that restrict access to content (media, Software as a Service (SaaS), etc.)
* Revenue model is the same: subscription based services, usually paid monthly.

####Basic functionality:

* Content/web functionality to deliver
* Landing pages to convert visitors to paying customers
* User management to register/remove users
* Access control to limit site wide access
* Authorization management to restrict access to content or services based on role or other characteristics
* Account management to maintain records/subscription status
* Recurring billing system for periodic payment transactions

####Key challenges/requirements:

* PCI compliance: key requirement for any ecommerce site. This will minimize risk of customer credit card exposure. Your website will meet PCI compliance if you accept payment information through the Stripe JS library and serve your payment page through SSL. It’s wise to host any app that requires login through an SSL connection. 
* Merchant account: a line of credit that allows a business to accept credit card payments from its customers. Stripe provides this service.
Recurring billing and account management must be in sync. Stripe provides webhooks to make sure this happens. Stripe will initiate an HTTP request to the app and that will notify the app to change a subscription status.

####Setting up Subscription Billing with Stripe API

* Use meta tag to set the Stripe Public API Key 
* Access external Javascript libraries to submit data to Stripe and obtain a Stripe token that indirectly references a credit card.

<img src="/img/articles/stripe_api.png" alt="" style="width: 100%;max-height: 100%">

####Additional considerations for subscriptions:

* Tiered pricing for multiple subscription plans
* Optional "free trial" subscription
* Subscribers can upgrade/downgrade plans
* Subscribers can cancel subscription plans
* Configure the subscription renewal period (Stripe defaults to one month)
* Administrator can change subscription plan or delete user
* Basecamp style subdomains (each user gets their own subdomain)
* Multitenancy database segmentation (ex. using [Apartment](https://github.com/influitive/apartment) gem)

#####Landing Page

<img src="/img/articles/api_home_page.png" alt="" style="width: 100%;max-height: 100%">

#####Subscribe

<img src="/img/articles/api_sign_up.png" alt="" style="width: 100%;max-height: 100%">

#####Admin

<img src="/img/articles/api_admin.png" alt="" style="width: 100%;max-height: 100%">

####Setting up Simple Payments with Stripe Checkout

Embedded payment form that works for desktop, mobile, tablet
Entire purchase experience handled by Stripe.

<img src="/img/articles/stripe_checkout.png" alt="" style="width: 100%;max-height: 100%">

#####Landing Page

<img src="/img/articles/checkout_list.png" alt="" style="width: 100%;max-height: 100%">

#####Product Checkout

<img src="/img/articles/checkout_pay.png" alt="" style="width: 100%;max-height: 100%">

####Future of electronic payments

* Mobile: 1.5 billion global smartphone users predicted by 2017
* Underserved merchants want alternative way to pay: SaaS based companies and industries in developing markets
* Decentralized cryptocurrencies gaining traction

####Resources: 

* [Ruby on Rails Tutorial](https://www.railstutorial.org/book) by Michael Hartl
* [Mastering Modern Payments: Using Stripe with Rails](https://www.masteringmodernpayments.com/) by Pete Keen
* Daniel Kehoe’s [RailsApps](http://railsapps.github.io/) Project
* [Software as a Disservice](http://gilesbowkett.blogspot.com/2013/10/new-ebook-software-as-disservice-fixing.html) by Giles Bowkett




