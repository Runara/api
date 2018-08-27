---
title: Runara API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://app.runara.com/developer'>Sign Up for a Developer Key</a>

includes:
  - errors
  - accounts
  - appointments
  - classes
  - admin
  - clients
  - locations
  - profiles
  - payments
  - promos
  - checkout
  - bookings
  - checkin

search: true
---

# Introduction

Welcome to the Runara API! Runara provides a REST interface for integrating your application data onto your own website and applications.

# Authentication

Runara uses API keys to allow access to the API. You can register a new Runara API key by logging into your [account](https://app.runara.com/) and navigating to "Account Settings" then to "API".

The Runara API expects your API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer your.jwt.token`

<aside class="notice">
You must replace <code>your.jwt.token</code> with your personal API key.
</aside>
