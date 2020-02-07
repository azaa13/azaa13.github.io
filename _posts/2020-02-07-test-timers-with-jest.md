---
layout: post
title:  "Write a unit test for native `timer` function using jest"
date:   2020-02-07 16:37:00 +0900
categories: unit-test jest test-timers
---
# Introduction

Native timers are widely used and its use cases are wide. Such as for updating particular page every x seconds, or every x interval refresh the page etcs.

`setTimeout`, `setInterval`, `clearTimeout`, `clearInterval` are timer function, it uses real time to perform given task. However, in testing environment it is bit different as it relies on real time to elapse. Luckily, `jest` provides `fakeTimers` which can be used during testing phase.

Below I will provide sample code which uses jest fake timers to run the function and passes test case.

# Sample code 

```js
// draw.js
updateDraw(){
    setInterval(this.draw, 100) // call draw() 10 times per a sec
}

draw(){
    // draw something
}
```

## Sample test code

```js
// draw.spec.js
import Draw from "./draw.js"
describe("updateDraw()", ()=>{
it("call draw() 10 times per a sec",()=>{
    // here is mock timer function has been used
    jest.fakeTimers()
    d = updateDraw()
    expect(setInterval).toHaveBeenCalledTimes(1)
    expect(setInterval).toHaveBeenLastCalledWith(expect.any(Function), 100);
})
})
```

### Explanation of sample test code

We've used `fakeTimers()` function to behave as native timer function from `jest`. Using this it is quite straightforward, after all we just need to assert whether `setInterval` function have been called only once.

For more info, encouraging you to visit <https://jestjs.io/docs/en/timer-mocks> and try more tests using it.