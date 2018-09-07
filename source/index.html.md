---
title: Runara API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://app.runara.com/developer'>Sign Up for a Developer Key</a>

includes:
  - errors
  - accounts
  - admin
  - appointments
  - bookings
  - classes
  - clients
  - favorites
  - locations
  - passes
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

> jQuery Auth Example:

```javascript
$.ajax({
  url: "https://api.runara.com/classes",
  type: 'GET',
  headers: {"Authorization": 'Bearer eyJ0eXAiOiJKV.eyJpc3MiOiJodHRwczovL2FwaS5ydDBhZGIzOWU3MDFjNDAwODcyZGI3YTU5NzZmNyIsInVzZXIiOnsiaWQiOjEwMDMxOX19.ma52y-xNn2AYuKCv2zznWMSQ'}
});
```

Runara uses API keys to allow access to the API. You can register a new Runara API key by logging into Runara and navigating to Account Settings -> API.

Runara expects for the API key to be included in all API requests to the server as the value for the header `Authorization`.

`Authorization: Bearer your.jwt.token`

<aside class="notice">
You must replace <code>your.jwt.token</code> with your own API key.
</aside>
