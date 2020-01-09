---
layout: post
title:  "End-to-End testing with NightWatchJs"
date:   2020-01-07 15:30:00 +0900
categories: e2e-test testing nightwatch
---

At any point, we as a FE developers have to test web application's smooth flow by applying either end-to-end test or any type of functional or integrated testing.
Since I am using NightwatchJs to do e2e testing, 'd like to share some insights and example snippet code of simple and straightforward test cases.

First of all, what is End-to-End testing?

- Sometimes it is called as UI testing as well, simply saying of this is kind of testing that mimics user interaction and workflow with the web application. For example, we need to test as if user open intended url (web app) in browser, type or click some button and expected behavior or components should be visible. 
- It ensures the app really has correct flow of user activities.

**About NightWatch framework**

There are various testing tools or frameworks which serve UI testing also unit testing. Each of them has own pros and cons, so to find out right (suitable) tool, that really depends on one's requirements and app flow.

In my case, still I am researching whether this is really suitable for my project outline. Hence I am exploring it and writing sample test cases.

**Some insights of the NightWatch**

(this is only based on my experience while using it)
- It works with WebDriver API, so it allows DOM elements level assertions and expectations.
- Syntax is comparatively simple with other tools.
- CSS and XPath selectors can be used to find the DOM elements.
- Installation part is not time consuming.
- API commands (part of documentation) for elements, interactions are well written.
- Can write test code by my own style (TS or JS).
  
Please find more detailed read from [here](https://nightwatchjs.org/).

**Sample e2e testing**

I am assuming that installation and configuration parts are done. 

{% highlight js %}
describe("sample test using nightwatch", () => {
  it("visit duckduckgo and do search ", browser => {
    browser
      .maximizeWindow()
      .url("https://duckduckgo.com/")
      .waitForElementVisible("#search_form_homepage_top")
      .setValue("input[type=text]", "End-to-End testing with Nightwatch")
      .click("input[type=submit]")
      .pause(2000)
      .assert.visible("body")
      .saveScreenshot("tests/e2e/screenshots/test.png")
      .end();
  });
});

{% endhighlight %}

Here it performs searching text from given url and assert its visibility and take screenshot of the search.
When running test, you can see that how fast it has executed.

![compiled test case](_includes\nightwatch.png "Run pretty fast")

As written above, screenshot can be captured as well.

![screenshot of the search](_includes\nightwatch-e2e.png "Screenshot of the search result")

**Explanation of the test case**
 - First open the browser and maximize it.
 - Wait till search box to be visible
 - After search box visible, search the given keyword. In order to put input value in the search box, we used `setValue` and select DOM by `input type text`. Can see DOM elements in developers tools inspection elements section. (press F12 and Elements section, can see the elem structure here).
 - After inputting text into search box need to press button to get all result. Here we used `click` and select elem by `input type submit`. 
 - Can be paused or not (just for seeing purpose, added pause)
 - Then can see all the result, we used `assert.visible("body")` for asserting it.
 - Additionally, we can save screenshots as well, just need to provide location it can be saved.
 - Note:: do not forget add `end()`. This is finish particular test case.

So far so good, can be added other test cases as well.
