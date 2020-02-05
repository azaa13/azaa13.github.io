---
layout: post
title:  "Why HTML's <video> event listening tag matters? "
date:   2020-02-05 18:11:00 +0900
categories: hmtl dom video event
---

As a FE developer, we have often times have to work with native HTML DOM elements, and manipulate or set its values to our desired one.
All the page related component's elements are absolutely using native HTML DOM elems after it is parsed and read as Javascript. However, different types of FE frameworks are available in current development environment and it is already included all the HTML elems into their own UI components with their pretty CSS config. Due to that, sometimes it is not necessary to work on native HTML elements.

Even though we've numerous choice of elements which can be used in our project. So I've selected `<video>` element to write about today, because most of the time video included in many projects and native HTML DOM properties give us a lof of opportunities to set its config as we want to display or play the video. 

## HTML DOM `<video>` element

Major video playing and streaming application uses it, including `Youtube`.

It has number of properties can be set and controlled the way we want.
Detailed information refer Mozilla's [page.](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Technical_summary)


## About event comparison

Events | Description 
--|---
canPlay| will buffer video data till it can be played (during video play, video properties set as default)
loadedData | just load video frame, in this case video properties  can be configured before the video gets played
process | after loading video frame, it is processed to buffer video data (video properties  can be configured before the video gets played)

