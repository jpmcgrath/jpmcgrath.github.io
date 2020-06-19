---
layout: page
title: Shortener
permalink: /projects/shortener/
---

Shortener is a [Rails Engine](https://guides.rubyonrails.org/engines.html) Gem that makes it easy to create and interpret shortened URLs on your own domain from within your Rails application. Once installed Shortener will generate, store URLS and “unshorten” shortened URLs for your applications visitors, all whilst collecting basic usage metrics.

## Overview

The majority of the shortener consists of two parts:

*   a model for storing the details of the shortened link (including the user
    the shortened link belongs to and counter that increments as the link is
    clicked);
*   a controller to accept incoming requests, grab the shortened link data out
    of the database and redirecting the visitors request to the target URL;

### Some niceties of shortener:

*   The controller does a 301 redirect, which is the recommended type of
    redirect for maintaining maximum google juice to the original URL;
*   A unique code of is generated for each shortened link, instead of using the
    id of the shortened link record. This means that we can get more unique
    combinations than if we just used numbers;
*   The link records a count of how many times it has been “un-shortened”;
*   The link can be associated with a user, this allows for stats of the link usage
    for a particular user and other interesting things;

## Installation

You can use the latest Rails gem with the latest Shortener gem. In your
Gemfile:

<pre class="code">  <span class="id gem">gem</span> <span class="tstring"><span class="tstring_beg">'</span><span class="tstring_content">shortener</span><span class="tstring_end">'</span></span></pre>

After you install Shortener run the generator:

<pre class="code">  <span class="id rails">rails</span> <span class="id generate">generate</span> <span class="id shortener">shortener</span></pre>

This generator will create a migration to create the shortened_urls table
where your shortened URLs will be stored.

## Usage

To generate a Shortened URL object for the URL “[www.jargonaut.net](http://www.jargonaut.net)“ within your controller /
models do the following:

<pre class="code">  <span class="const">Shortener</span><span class="op">::</span><span class="const">ShortenedURL</span><span class="period">.</span><span class="id generate">generate</span><span class="lparen">(</span><span class="tstring"><span class="tstring_beg">"</span><span class="tstring_content">http://www.jargonaut.net</span><span class="tstring_end">"</span></span><span class="rparen">)</span></pre>

or

<pre class="code">  <span class="const">Shortener</span><span class="op">::</span><span class="const">ShortenedURL</span><span class="period">.</span><span class="id generate">generate</span><span class="lparen">(</span><span class="tstring"><span class="tstring_beg">"</span><span class="tstring_content">dealush.com</span><span class="tstring_end">"</span></span><span class="rparen">)</span></pre>

To generate and display a shortened URL in your application use the helper
method:

<pre class="code">  <span class="id shortened_url">shortened_url</span><span class="lparen">(</span><span class="tstring"><span class="tstring_beg">"</span><span class="tstring_content">dealush.com</span><span class="tstring_end">"</span></span><span class="rparen">)</span></pre>

This will generate a shortened URL. store it to the db and return a string
representing the shortened URL.

You can find the shortener gem on [rubygems](http://rubygems.org/gems/shortener) and complete source code of the shortener gem on [github.](http://github.com/jpmcgrath/shortener)

Any questions? Need help? Don’t be shy, you can post to the projects [issues](http://github.com/jpmcgrath/shortener/issues) tracker.