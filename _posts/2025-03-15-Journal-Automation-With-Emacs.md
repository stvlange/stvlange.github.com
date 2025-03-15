---
layout: post
title: "Journal Automation with GNU Emacs"
date: 2025-03-15 13:20:36
categories: journal automation emacs
---

{% newthought "Today I decided to add some more automation" %} to my journal writing with GNU Emacs and the yasnippet package.<!--more-->

This journal uses markdown format for its posts {% sidenote 'sn-id-2' '<a href="https://en.wikipedia.org/wiki/Markdown">Wikipedia Markdown Entry</a>' %}. As such there are certain required elements when preparing the journal entry.

This theme also has specific formatting that must be used for supported styles that can be used in the journal entry (e.g. marginfigures, sidenotes, marginnotes).

Prior to this today I was referring back to documentation and past journal entries to get examples formatting I needed. Not really all that efficient, and prone to error. Automation to the rescue!

### GNU Emacs & Yasnippet
I use the GNU Emacs editor{% sidenote 'sn-id-3' '<a href="https://www.gnu.org/software/emacs/">GNU Emacs</a>' %} when writing this journal. There are a variety of editor options out there, I like Emacs because of the multitude of add-ons that can be used with it to extend the capabilities.

It is an editor that has infuriated and enthralled many and I am by no means an expert, far far from it. The add-on package I am using for my automation is called "yasnippet"{% sidenote 'sn-id-4' '<a href="https://github.com/joaotavora/yasnippet">Yasnippet Github</a>' %} which is available in the emacs elpa package system or directly on the author's github site.

With the yasnippet package it is possible to create custom snippets that to add preformatted text to emacs. Yasnippets allows you to configure prompting that allows you to tab trough and replace the prompt text with content you want to use.

Below are the yasnippets that I setup to make my journaling easier.

### Custom Yasnippets

*<jhead*
{% maincolumn 'assets/img/jhead.png' 'Yasnippet code for journal header' %}

*<mn*
{% maincolumn 'assets/img/mn.png' 'Yasnippet code for marginnote' %}

*<sn*
{% maincolumn 'assets/img/sn.png' 'Yasnippet code for sidenote' %}

*<mf*
{% maincolumn 'assets/img/mf.png' 'Yasnippet code for marginfigure' %}

*<mci*
{% maincolumn 'assets/img/mci.png' 'Yasnippet code for maincolumn image' %}

*<fwi*
{% maincolumn 'assets/img/fwi.png' 'Yasnippet code for fullwidth image' %}

*<epi*
{% maincolumn 'assets/img/epigraph.png' 'Yasnippet code for epigraph' %}

### How does it work

When I start a new journal entry I start with setting up the journal header. With the yasnippet in place, I simply type "<bt" (without the quotes) and press the TAB key on the keyboard.

The "<bt" is replaced by the content of the snippet and anything the is formatted with a "${#:NAME}" is accessed by pressing the TAB key.

I then press TAB to go to the next field and type the text I want to replace the NAME value. Quick, simple and always formatted correctly.

This *really* saves time and makes quickly adding the different elements so easy. I am honestly kicking myself for not doing this sooner.

So there you have it, everything you ever wanted to know about my journal writing automation.
