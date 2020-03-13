---
layout: post
title:  "What is visual regression test? and how to do that?"
date:   2020-03-09 16:37:00 +0900
categories: storybook addon-storyshots regression-test visual-regression-test
---
## So what is visual regression test?

To test UI component appearing correctly on browser, we do visual testing. It verifies the UI component visual appearance pixel by pixel, and point out from minor to major difference. Sometimes developers don't realize small UI changes and neglect, however this kind of tests are great for finding such cases and notifies us.

There are plenty of tools or library available in the github with free of charge.
Such as
 - storybook's addon storyshots
 - jest-image-snapshot
 - percy
 - happo
 - testcafe
 - loki and so on.

To find out the right tool for visual regression test, we need to be clear which features we want, and be specific with the requirement.

I will cover those tools pros/cons more detailed in below.

## storybook's `storyshots` addon

Storybook already provides testing addon which works with `jest`. For unit testing we can use `addon-storyshots`.
For visual regression test we use `addon-storyshots-puppeteer`. It works with `puppeteer`, the screenshot capture package to take image snapshot of the UI component.

Pros 
 - easy config 
- easy running test
- auto generated HTML snapshots 
- auto generated image snapshots


