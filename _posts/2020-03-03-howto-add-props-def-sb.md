---
layout: post
title:  "How to add specific definition for the prop table using storybook addon-docs? "
date:   2020-03-03 16:37:00 +0900
categories: storybook addon-docs props
---

We're using storybook for checking out the independent components behavior, representation, also to use auto generating documentation.

Storybook's handy addon `addon-docs` auto generates documentation including prop table, event and slot definition. This is really helpful for everyone of the team member.

Since the prop/emit(event)/slot table are generated auto, so does its definition.
But what if we want to include more detailed or specific definition of the properties. 

Yes, we can add our desired prop/emit/slot definition by adding comments describing the definition of the data exchange, in there those prop/emit/slot are initialized or created.

## Sample prop definition

I am assuming the project is already using storybook, and required addons. Which means it simply configured correctly and installed dependent packages.

Let's say we have a `sampleComponent.vue` file where we initialize a `prop` named `isSample`. 

```js
// sampleComponent.vue

// using vue-class-decorator
...

@Prop({ default: false })
isSample!: boolean;
...

```

As mentioned earler, where prop is initialized we need to write `multi-line comments` in order to describe prop definition.

```js
// sampleComponent.vue

// using vue-class-decorator
...

// this is shown as prop definition in storybook docs section
/*
* indicates whether current value is sample or not.
*/
@Prop({ default: false })
isSample!: boolean;
...

```

This comment parsing uses `vue-docgen-api` to parse and generate the prop definition.

More details, go ahead and check those repos.
 - https://github.com/storybookjs/storybook/tree/next/addons/docs
 - https://github.com/vue-styleguidist/vue-styleguidist/tree/dev/packages/vue-docgen-api
 - https://github.com/pocka/vue-docgen-loader
