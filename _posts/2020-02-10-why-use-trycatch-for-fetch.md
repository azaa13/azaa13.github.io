---
layout: post
title:  "Why we should catch errors thrown by fetch API? "
date:   2020-02-10 16:37:00 +0900
categories: trycatch exception fetchAPI
---

Fetching API is a backbone of every application that communicates with other server/app to gather data and represent in their own. But number of failure including network error or any sudden change may cause some issue where fetch not able to run properly.

To catch the origin of issue or failure we need to use try-catch exception handling for fetch API. In this example, i will explain what will happen if we do not handle exception.

## General Fetch API

Fetch API gives us a chance to access certain data which is transferred using HTTP pipeline known as request and responses. Using global `fetch()` method, we can fetch data in async way across the network.


Basic fetch request

```js
fetch("example")
    .then((response) => {
        return response.json();
    })
    .then((data =>{
        // do something with data
    }))
```

Fetch returns a `Promise` containing the response obj. (response.json()) 

So using this method, we can successfully get data which we wanted to be presented. However, as mentioned earlier if some issues such as network related cases it will return simply HTTP status text. 

So just in case when something bad happens, we can catch the error and maybe notify the user who is using the application. For that matter, we are using try-catch handler.

But before that, we should get familiar with Fetch APi. According to the MDN (Mozilla web docs), fetch will not do following 3 things.

1. The Promise returned from fetch will not reject on HTTP error status. 
   
   Means even if error is 404 or 500, still it will return the response Promise. Only on **network failure** or **anything prevented the request from completing**, it will reject the request.

2. Fetch will not receive cross-site cookies. 

    Means `Set-cookie` headers from other sites are silently ignored.

3. Fetch will not send cookies.
    Means unless until someone set the credentials init options, it will follow default credentials policy to `same-origin`.

## Exception handling of Fetch API

Basic try-catch fetch request

```js
try {
    fetch("example")
        .then((function(response) => {
            if(!response.ok) {
                throw new Error('HTTP error ' + response.status)
            }
            return response.json();
        })
        .then((data =>{
            // do anything with data
        }))
} catch (e) {
    // do something with error
    window.alert('Error is caught', e)
}

```
The above example shows that when fetching, it returns error due to any reason/cause. In this case, user is notified by alert popping out on the window.

Detailed info, please find from <https://github.com/mdn/mdn> or <https://developer.mozilla.org/en-US/>.