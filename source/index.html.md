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
  - admin
  - bookings
  - classes
  - clients
  - favorites
  - locations
  - profiles
  - promos
  - checkout
  - bookings
  - checkin

search: true
---

# Introduction

Welcome to the Runara API! You can use our API to access Runara endpoints.

# Authentication

Runara uses API keys to allow access to the API. You can register a new Runara API key by logging into Runara and navigating to Account Settings -> API.

Runara expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer your.jwt.token`

<aside class="notice">
You must replace <code>you.jwt.token</code> with your own API key.
</aside>
