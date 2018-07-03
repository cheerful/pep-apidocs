---
layout: v2
title: Authentication
---

* TOC
{:toc}

The Pep API currently provides Personal Access Tokens as the way to handle authentication in your application. Personal Access Tokens are meant for internal applications and scripts.

<p class="note">
The examples below use <a href="http://radek.io/2015/10/20/httpie/">httpie</a>; which returns a pretty-printed and syntax highlighted response, and works on OS X, Linux, and Windows. You should try it out, we really like it!
</p>

## Which authentication method do I choose?

[Sending HTTP Header or `pep_token` parameter for Personal Access Token](#using-personal-access-tokens)
: My application uses Personal Access Tokens for authentication

[Basic Authentication using Personal Access Tokens](#api-access-via-personal-access-tokens)
: My tools only allow me to use Basic Authentication and I am using Personal Access Tokens for authentication.

## Using Personal Access Tokens

[Personal Access Tokens](http://help.pep.cards/article/103-connecting-to-the-pep-api) allow users to issue individual tokens for apps and revoke them at will—be sure to handle authentication errors in your application. Treat Personal Access Tokens like passwords!

The token has to be sent for each request your application makes to the Pep API.

There are two ways to send the token—examples are given below:

As a *query parameter* named `pep_token`:

<pre class="terminal">
http GET <%= API_V1_URL %>/cards pep_token==<%= API_V1_EXAMPLE_PERSONAL_ACCESS_TOKEN %>
</pre>

As a *HTTP header* named `X-PepToken`:

<pre class="terminal">
http GET <%= API_V1_URL %>/cards X-PepToken:<%= API_V1_EXAMPLE_PERSONAL_ACCESS_TOKEN %>
</pre>

## Basic Authentication

The API supports Basic Authentication as defined in [RFC2617](http://www.ietf.org/rfc/rfc2617.txt).

### API access via Personal Access Tokens

You can authenticate using [Personal Access Tokens](http://help.pep.cards/article/103-connecting-to-the-pep-api). This approach is useful if your tools only support Basic Authentication and you are using Personal Access Tokens for authentication.

To do so, provide the Personal Access Token as the username and provide a blank password or a password of `x-pep-token`. For example:

<pre class='terminal'>
http GET <%= API_V1_URL %>/cards -a <%= API_V1_EXAMPLE_PERSONAL_ACCESS_TOKEN %>:x-pep-token
</pre>