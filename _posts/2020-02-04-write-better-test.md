---
layout: post
title:  "How to write better unit testing using jest and vue-test-utils?"
date:   2020-02-4 17:21:00 +0900
categories: unit-test vue-test-utils jest
---

Writing unit testing is vital process of any software or application development. Without unit testing it is way difficult to assure that given function or method is working as expected or not. Instead, writing a test and its failure  makes us to debug and lead some improvements of the function or method.

## Front-End development
So what if we using Front-End framework and only developing UI components? Indeed, we should test those components by applying UI or E2E testing or integration testing. 

As the title of the post described that I'll cover mainly about writing better and efficient unit test for functions and methods. We're using `jest` Javascript testing framework and `vue-test-utils` VueJs framework's unit testing utility library.

I've already covered how to write unit test in my previous [post.](2020-01-27-write-unit-test-ts.md) Hope it is helpful for one who needs some samples.

## Unit testing of UI components

In any FE application, I am assuming that components are implemented. But in SFC (Single File Components) contains script section where to write client-side scripting, in other words we can write main logic to manage or control the DOM elements of the component. SFC file structure looks like below.

```
# any .vue component file
<template>

/* can include DOM elem */
    <div>
        <p> Testing is Fun! <p>
    </div>

</template>

<script lang=ts>
// language can be js or ts
</script>

<style scoped>
/* CSS DOM elem decoration */
</style>

```

For unit testing we need to test logic written in `<script></script>` section. For DOM element part which is written in `<template></template>` section can be testing using UI testing or E2E testing.

Since for unit testing we'are using `jest` JS testing framework, it provides pretty much API that can we use in our testing.

Here is lists of widely used yet strong functions that we will help you to write much better unit test.

I am assuming that you are familiar with  fundamental testing functions or APIs, so not including in this list.

test Fn or Method name | Description
---|---|
afterEach() | It will run after each test case is completed. Helpful if some cleaning up process is required. For example, reset all mocked methods are functions.
beforeEach() | It will run before each test get started. Helpful if some config is required. For example, mock some methods or functions.
describe.skip() or xdescribe or xit | Skip to run particular test case.
it.todo() or test.todo() | Write todo for writing test, test will be highlighted in summary output.
jest.fn() or jest.mock() | Mock method or function
jest.spyOn()| Mock method or function
jest.setTimers()| Set time interval for test before or after hook
expect or asset | Testing its value, mostly for assertion purpose

If you know these testing methods for your initial unit testing steps,it will help to write better tests and achieve some tasks.

If you are more curious and ready to use other test methods, please visit jest's official [web-page.](https://jestjs.io/docs/)
