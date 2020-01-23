---
layout: post
title:  "What's new for latest storybook version, what features have been added in later of `storybook@^5.2.0`"
date:   2020-01-23 18:14:00 +0900
categories: storybook latest-updates useful-info
---

Last post I've shared was about a feature of storybook which generates auto documentation for the components, this have been reflected later version of the storybook@5.2.0. ([last-post](2020-01-17-storybook-addon-docs.md))

So by now, version of the storybook have been updated till `storybook@5.3.8`. Each time the package updates it fixes some bugs or adding some patches etc.

So what is really boom updates or features that introduced so far?
Here I'm providing some important ones to check it out and reflect in your project accordingly.

# Auto generated documentation 

Yes, this is super helpful, as number of components are increased, it should be easy to track and determine how its data flows.

By just installing `storybook/addon-docs` and set its config, we can see newly generated documentation for us!. Thanks for this feature.

# Way easier to write documentation using MDX

Also, MDX `markdown syntax` is supported for writing more detailed kind of documentation which includes some graph/analytics, code snippets. Reason is auto generated docs generate general type of docs (all same types), so it is easy to edit and maintain using mdx.

For this feature, it is required to install additional packages which extracts and loads of the components into easy to compile for markdown syntax.

# No more many config files to maintain, maybe a single file (main.js)

Previously, `config.js`, `addons.js` if required `presets.js` are must to be exist. It is not great to deal with multiple config files because simply we can make mistakes or forget some changes to add. As a result, it keeps throwing errors.

But now, later of `storybook@5.3.0` version, a single file `main.js` can includes all config of above three files.

If required additional config files such as `manager.js`, `preview.js` can be created. But most of the time `main.js` is enough to run.

# New format for writing stories

It gets more easier and easier to write stories. Earlier versions, (but we can still use) `storiesOf` was default format to write stories, but not they've introduced `Component Story Format` simply `CSF`. It's based on ES6 module, so it can written as `export default {}`. Now this `CSF` is a default format to write stories according to their official website.

After version `storybook@5.3.0` both formats can be included in a single `.stories.js` file. It can be mixed only if same components are not called in both stories. (we can not include same component into two different styles!)

Those are [really need to know] kind of updates that I've shared. Definitely you can check more detailed updates by checking storybook github repo and their medium blog.
Down below, I am including some useful links, go ahead and check them out.

Storybook official site: <https://storybook.js.org/>

Storybook official medium blog: <https://medium.com/storybookjs>

Storybook github repo: <https://github.com/storybookjs/storybook>

Storybook `addon-docs`: <https://github.com/storybookjs/storybook/tree/next/addons/docs>
