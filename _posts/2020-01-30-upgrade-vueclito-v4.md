---
layout: post
title:  "How to upgrade vue-cli v3 to vue-cli v4"
date:   2020-01-230 17:16:00 +0900
categories: vue-cli4 cli vuejs
---

We agree that vue-cli standard tooling package for VueJs project is super useful, as it reduces complicated configuration of vue project setting.
Lately, in Dec, 2019 their version 4.1.2 is released that has some really good updates which can be used in our project effectively.

First of all, I will briefly go through latest updates of `vue-cli@4.1.2`, then will share some good practice to upgrade or migrate from version 3 to version 4 without producing error.

# Latest updates of `vue-cli@^4`

- Vue config 
- Babel config
- Jest config
- Babel, babel-preset config

As an user of the tool, main updates are reflected in our daily config file such as vue,babel,and jest config.
By upgrading the latest version, the config of above files seem way faster and easy to understand, also setup its config.

# Way to migrate to `vue-cli@^4`

Before upgrading vue-cli, it is advised to check its version installed in your system. For that, run the following command.

    vue --version or vue -V

After that you'll see similar to `@vue/cli@3.x.x`.
If it is shows as a version 3, we can upgrade to version 4.

## Upgrade all plugins

You can upgrade all plugins or dependencies which is in your project by running 

    vue upgrade

But this is sometimes really powerful and update all the packages related to `@vue/cli`. So before running the command, make sure which all dependencies are about to update. Is there any complicated config or external setup you've been set lately. Make sure to check those and run this command.

## Upgrade by plugins

This approach better if you know the exact plugins or package that should be upgraded. In this case, we can upgrade `@vue-cli` by running following command.

    vue upgrade @vue/cli-service

This will only upgrade cli-service, so other plugins won'be affected.

Another useful plugin is `babel`, we can upgrade babel using this command.

    vue upgrade @vue/cli-babel

In latest cli-babel version, instead of `core-js@2`, `core-js@3` is used. If your project's other package is dependent on core-js, make sure which version they are using.
As it mentioned that core-js version 2 will not be maintained further, so most of the coje-js dependent packages are migrated to its version 3.

After making sure their package version, it is advised to migrate for avoiding error.

To read version 4 of vue-cli, please read their [release-notes.](https://github.com/vuejs/vue-cli/releases/tag/v4.1.2)

To read more about migrating from v3, please read it from [official-page.](https://cli.vuejs.org/migrating-from-v3/#vue-cli-plugin-typescript)