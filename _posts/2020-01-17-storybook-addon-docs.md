---
layout: post
title:  "Let's add some documentation to stories using @storybook-addon-docs"
date:   2020-01-17 17:00:00 +0900
categories: storybook addon-docs addon vuejs
---

# What is storybook?

Well, if you work as FE developer, then storybook or simply generating stories is part of your job and its super useful, since it loads independent components into the browser so we can visually interact with components not writing any extra codes.

If you first time reading about storybook, for sure you should visit their official site to gain more understanding also installation and get comfortable using of it. Visit here [storybook-official-site](https://storybook.js.org/) and read documentation :).

Plus, it supports most of the popular front-end development framework such as React, Vue, Angular etc.

# Why use storybook-addon-docs?

Surely, we've spent most of our dev time staring at numerous components trying to remember what it does, what's is transmitted values mainly props etc.

To reduce that time and to organize, to make documentations of various components will be achieved using this `docs`. It is relatively simple, any of the team member can be part of it, since it supports `MDX` markdown syntax.

If you using storybook below `@storybook5.2` version, this feature is not added, so please upgrade `@storybook^5.2`.

This package provides auto created documentation for your component without requiring additional effort. The docs are generated automatically, hence their styling is default. If you want to prepare your documentation more detail, additionally `markdown` syntax generator or `MDX` will help.

# How to start using docs?

I am assuming that you've already read about `storybook` and install it in the project you've working on.

Just for information matter, as mentioned before it is not included in `@storybook^4.0` or below `@storybook5.2`. So please update its latest version.

# Let's use `storybook-addon-docs`

1. Install storybook addon docs through `npm` or `yaml`.
   
   `npm install @storybook-addon-docs --save-dev`
   It adds package into dev dependenciens in `package.json` of the project.
2. Include addon into storybook config file (`.storybook/main.js` or `.storybook/config.js`)


    In `main.js`, add the docs in addons section.
    This is how my main file look like.

    {% highlight js %}
    /* main.js */
    module.exports = {
    stories: ['../src/**/*.stories.(js|mdx)'],
    addons:[
        '@storybook/addon-actions/',
        '@storybook/addon-links/',
        '@storybook/addon-docs/' /* this is newly added docs addon*/
    ]
    };
    {% endhighlight js %}


3.Include docs into stories

If you've already updated your storybook, you've noticed that syntax or the way of writing story has been updated from `storiesOf({})` to `Component Story Format(CSF)`. 
    Following example of story is written in `CSF` format, which is simply same as vue component style.
    
    {% highlight js %}
    import Vue from "vue";
    import Hello from "../components/helper/Hello.vue";
    /* default export style*/
    export default { title: "Footer component", component: Hello };

    /* export style as function*/
    export const withText = () => "<hello>yupp, normal test</hello>";
    
    /* export style as function include template of component*/
    export const asAComponent = () => ({
        components: { Hello },
        template: `<hello></hello>`
    });
    {% endhighlight js %}

If using `storiesOf({})` format, 
    adding `addParameters({component:Componentname})` will do the same.
    Providing sample story below.

    {% highlight js %}
    import {storiesOf} from "storybook/vue";
    import Hello from "../components/helper/Hello.vue";
    storiesOf("Sample story", module)
        /* this section will add docs to the component */
        .addParameters({
            component:ComponentName
        })
        .add("story", () => {
            components: {
                ComponentName
            }
        })
    })
    {% endhighlight js %}

After running storybook, you sure will see `Docs` tab in the storybook and can see auto generated docs. Hope this will help your work effectively.

Alright, this is section is showing only `DocsPage` of using `storybook-addon-docs` package. There is `MDX` which is more personalized documentation preparation helper. Can include source code of the code as well text of document explaining about the component.

I will provide `MDX` used documentation of components in different post.
Feel free to visit storybook website and research more about their recent updates.
