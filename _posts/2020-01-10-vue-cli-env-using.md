---
layout: post
title:  "Using environment variables (env) in VueJS project with `vue-cli-3`"
date:   2020-01-10 14:52:00 +0900
categories: vue-cli3 env-var vuejs
---
Environment variable is super useful variable that can be used in project level usage, means in any file this variables can be called and used. Such as API secret key, base url are used global (project) level in most of the project, so it can be used as env var. Additionally, it is advised to use some confidential value including API secret key should be kept as `local env` var.

As security purpose, .env local files are ignored by `.gitignore` by default.

If the project is configured by webpack or vue-cli-3, `.env` file need to be created for using env var and its process is pretty straightforward.

 I'm providing steps to to use env var in your Vuejs project.

## Steps

 **1. In project root folder (means same place `package.json` is stored) create `.env` file.**

If you want to use env for development phase, it'll be useful to create `.env.development` also for production phase `.env.production`. Such distinguishes are helpful if env var are varied depend on production and dev mode.

To create file, run following command.

`touch .env  `

**Note::**

If project has different type of `.env` file, the priority to loading file differs.
Let's say `.env` and `.env.development` both file exist in the project root folder. But only `.env` file is stored env var (explicitly assign values to the env variables). When running `npm run serve` (by default runs as `development` mode) command, env var not loaded correctly. Because, `.env.development` file has higher priority to load when `npm run serve ` run as it specifies development mode. So in this case, please use `env.development`.

Similarly, when `npm run serve --mode production` is specified `.env.development` loads.

 **2. No need to install `dotenv` if using `vue-cli-3` or above.**
It is already included, so directly create file and assign values to the var.

**3. Put env var into `.env` file.**

Environment value is nothing but key and value pair. Again, if you using `vue-cli-3`, there is naming convention need to be followed.

All env var starts with `VUE_APP_your_env_var`. For example, if I want to store API key then var name can be `VUE_APP_API_KEY = 0000`.

In order to assign value, it is normal `key=value` assign. 

If webpack configured, no need to include `VUE_APP_` as env var name. It can be directly `API_KEY= 0000`.

**Note::**
Key, value pair is not JSON styled as such `key:value`. So be aware of it.

**4. Use env var in the project**

As mentioned earlier, env var can be used anywhere in the project. Can be used directly writing as `process.env.VUE_APP_your_env_var`. For example, above I have created api key env var, so I can use it as `process.env.VUE_APP_API_KEY` in any file of the project.

**Note::**
After updating `.env` file, please restart the running server. In the terminal, press `Ctrl-C` and again run `npm run serve`.

If want to read more details, please go to the [official-site](https://cli.vuejs.org/guide/mode-and-env.html#example-staging-mode).