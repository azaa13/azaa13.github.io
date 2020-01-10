---
layout: post
title:  "Analyzing memory consumption of the web application using Firefox developer tool"
date:   2020-01-09 17:29:00 +0900
categories: analyze memory dev-tool firefox
---

We are aware of that when application's page is loaded in the browser, it consumes some memory about ~mbs. However we are not sure how much capacity's are used and exactly what part of the function is loaded (more). In order to analyze and investigate, we can use browser's developer tool.

 Dev tools are available in most of the browsers including Chrome, Chromium, Firefox, Edge, EI and so on. In this example, we are using Firefox browser, dev tool is visible by pressing `F12`.
So, let's get started.

### Launch Firefox browser

Launch any browser and in the address bar write address of the site. In this example, I wanted to show any website which requires user interaction by clicking button or inputting, so that we can see more details in the monitoring. Example I visited `www.bbc.com` as it loads rich imgs and videos. So we can see how memory consumption increased or decreased.

Press F12 and go to Memory section tab.
It looks like below img. !["Example of memory tab"](https://github.com/azaa13/azaa13.github.io/blob/master/_includes/memory-tab.png)

### Take a snapshot

To take snapshot, press `camera` looking button. From above img, please refer step 2.

After taking snapshot, it will show general snaps info in the left side of the panel including timestamp, from there should check memory consumed value size shows in `mb`. In the right side, detailed info of loaded elements with its loaded size (by `bytes` and `counts`) such as objects, strings, domNode. And view can be seen as `Tree Map` or `Aggregate`. To see results differently please select `View` from top select button.

### Analyzing snapshot

Firefox dev tool offers some styles in order to analyze the page object effectively.

During this sample test case, first I have taken snapshot when the web app loaded for the first time. After refreshing page, memory consumed value should be similar to previous snapshot. Again, press any of the tab from the web page and load new page, take its snapshot. Depend on the interaction with web server (sending HTTP requests to fetch data), network response time varies and memory consumption differs.

Select any tab and wander around the web page (for some time), now again visit the same page (which recently snapshot is taken), and take new snapshot. The memory should not increased significantly if the cache is enabled. (even cache is disabled should not increase since it sends same # of req to the server as earlier). As shown in example img's step 3, can see consumed values by bytes.

#### Comparing two snapshots

To observe more details of the snapshots, we can compare two different snapshots of same page's which are taken at the different time. For doing that, press a button which is right to the `camera` looking button (snapshot button). It shows all taken snapshots that can be compared by selecting its baseline and comparison snaps.

From right side of the panel, can check how many total # of counts or bytes are differ. Specifically, which group is loading (arrays, json, obj etcs.,).

If 'd like to read and explore more about Firefox developer tool, please go ahead and check this official site <https://developer.mozilla.org/en-US/docs/Tools/Network_Monitor/Performance_analysis>.