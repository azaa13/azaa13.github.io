---
layout: post
title:  "End-to-End testing framework NightWatchJs: installation and config step by step"
date:   2020-01-08 11:41:00 +0900
categories: e2e-test testing nightwatch
---

Let's dive more into NightWatchJs end-to-end testing tool by installing it first and set config. 

Before following the steps, encouraging you to first visit their official site and have base knowledge or getting familiar with the tool. Please redirect [here](https://nightwatchjs.org/).

If already installed and ready to write your first test, please visit [here](2020-01-07-e2e-testing-nightwatch.md) to read simple example of how writing test cases.

## Installation

Adding this package and run on the project is not hard part. It is just a matter of timing. Let's get started.

Assuming that you've already have `nodejs` installed in your system, as NightwatchJs is written in NodeJs, hence it required to be installed beforehand.

In order to run nightwatch, it's required to install 2 different packages.
 1.  Nightwatch (through `npm` command line tool)
 2.  WebDriver (Chrome, Firefox, Edge, IE etc., )

### Installing Nightwatch

As mentioned earlier, we can run following command and install nightwatch in our project dependencies.

`npm install nightwatch --save-dev`

### Installing WebDriver

Depend on the project testing requirement, free to select any browser that automatic tests can run. 

Providing a table to refer which driver to install based on browser.

Browser | Web Driver 
--- | --- | ---
Chrome | `Chrome-driver` 
Firefox Mozilla | `Gecko-driver`
Windows Edge | `microsoft-webdriver`
Safari | `safari-driver`

We'll install chrome driver as following.

`npm install chromedriver --save-dev`

Last time, even chrome driver installed, it shows warning says geckodriver should be installed with. Just for the sake of warning resolving, installed geckodriver as well.

`npm install geckodriver --save-dev`

So far so good, all required packages are installed.
## Configuration

After installing `nightwatch`, config json file named `nightwatch.conf.js` is generated automatically by default. And can be found in the root dir. (`/src`)

We can create another file named `nightwatch.json` and by default nightwatch will load conf.js file. 

Config part is not complicated, we just need to select which browser will be used during automatic test and set its path or server path to run the execution command. Also, specify port number and test folder.

Following is how my `nightwatch.json` file looks like:
{% highlight json %}
{
    "src_folders" : ["tests/e2e/"],
  
    "webdriver" : {
      "start_process": true,
      "port": 9515
    },
  
    "test_settings" : {
      "default" : {
        "desiredCapabilities": {
          "browserName": "chrome"
        }
      }
    }
  }
  {% endhighlight %}

#### Explanation of `nightwatch.json` file

As mentioned before, we can set default browser that automatic test can run. In this case, `default.desiredCapabilities.browserName:"chrome"`. We can set any other browser. After we will set port, but as default it is set as `port:9515`, we can set any but note that it should available port. Sometimes we set same port as our localhost and keep receiving failed errors (be careful).  In `src_folders`, can give folder of the testing file. In above test it is `tests/e2e`.

 I created separate `nightwatch.conf.js` file which only include web driver path via importing.

  Here is how my `nightwatch.conf.js` file looks file:
  {% highlight js %}
const chromedriver = require("chromedriver");
module.exports = (function(settings) {
  settings.test_workers = false;
  settings.webdriver.server_path = chromedriver.path;
  return settings;
})(require("./nightwatch.json"));
  {% endhighlight %}


  In conf.js file, driver path is imported and we need to simply fill correct path in `webdriver.server_path` object.

### Running test
Additionally, for running tests we can write executable script in `package.json` 's `script` section. 

Or, can run test as follows in project specific manner. 

`./node_modules/.bin/nightwatch testfile `

It is convenient to include `nightwatch` in package.json.
In this case, we can run test as follows.

`npm run nightwatch testfile`

Single or multiple test files can be run together. For example, 
`npm run nightwatch testfile1 testfile2`

And if you thinking to read more about it, encouraging to visit official site and look around `Developer Guide` and `API Reference` section.

Below, I am providing hyperlinks.

Dev guide - <https://nightwatchjs.org/guide>

API ref - <https://nightwatchjs.org/api>