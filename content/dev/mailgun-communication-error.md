---
type: docs
title: Mailgun::CommunicationError
description: How to fix "Mailgun::CommunicationError (400 Bad Request)".
categories:
  - dev
tags:
  - mailgun
bookToc: false
---

`Mailgun::CommunicationError (400 Bad Request)`

If you encounter this exception from Mailgun when trying to send emails using the sandbox domain, make sure that the recipients of your emails are active in the `Authorized Recipients` list in your Mailgun settings. Mailgun's exception handling for this case was exceptionally sparse. The error messsage had no details. I figured out that my problem was with the `Authorized Recipients` by printing out the response that the Mailgun gem (library) receives when it sends a REST request to Mailgun's services found at `~/.rvm/gems/ruby-2.3.0/gems/rest-client-1.8.0/lib/restclient/request.rb`:

    "{\n  \"message\": \"Sandbox subdomains are for test purposes only. Please add your own domain or add the address to authorized recipients in domain settings.\"\n}"
