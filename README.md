[Hux Blog](https://huangxuan.me)
================================

> I never expected this to become popular.

![](http://huangxuan.me/img/blog-desktop.jpg)


[User Manual 👉](_doc/Manual.md)
--------------------------------------------------

### Getting Started

1. You will need [Ruby](https://www.ruby-lang.org/en/) and [Bundler](https://bundler.io/) to use [Jekyll](https://jekyllrb.com/). Following [Using Jekyll with Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/) to fullfill the enviromental requirement.

2. Installed dependencies in the `Gemfile`:

```sh
$ bundle install 
```

3. Serve the website (`localhost:4000` by default):

```sh
$ bundle exec jekyll serve  # alternatively, npm start
```

### Development (Build From Source)

To modify the theme, you will need [Grunt](https://gruntjs.com/). There are numbers of tasks you can find in the `Gruntfile.js`, includes minifing JavaScript, compiling `.less` to `.css`, adding banners to keep the Apache 2.0 license intact, watching for changes, etc. 

Yes, they were inherited and are extremely old-fashioned. There is no modularization and transpilation, etc.

Critical Jekyll-related code are located in `_include/` and `_layouts/`. Most of them are [Liquid](https://github.com/Shopify/liquid/wiki) templates.

This theme uses the default code syntax highlighter of jekyll, [Rouge](http://rouge.jneen.net/), which is compatible with Pygments theme so just pick any pygments theme css (e.g. from [here](http://jwarby.github.io/jekyll-pygments-themes/languages/javascript.html) and replace the content of `highlight.less`.


### Interesting to know more? Checkout the [full user manual](_doc/Manual.md)!


Other Resources
---------------

Ports
- [**Hexo**](https://github.com/Kaijun/hexo-theme-huxblog) by @kaijun
- [**React-SSR**](https://github.com/LucasIcarus/huxpro.github.io/tree/ssr) by @LucasIcarus

[Starter/Boilerplate](https://github.com/huxpro/huxblog-boilerplate)
- Out of date. Helps wanted for updating it on par with the main repo

Translation
- [🇨🇳  中文文档（有点过时）](https://github.com/Huxpro/huxpro.github.io/blob/master/_doc/README.zh.md)


License
-------

Apache License 2.0.
Copyright (c) 2015-present Huxpro

Hux Blog is derived from [Clean Blog Jekyll Theme (MIT License)](https://github.com/BlackrockDigital/startbootstrap-clean-blog-jekyll/)
Copyright (c) 2013-2016 Blackrock Digital LLC.

New modify (1/27/2025)
-------
1. 问题：GitHub Actions不成功，返回错误信息：
```
build
The current runner (ubuntu-24.04-x64) was detected as self-hosted because the platform does not match a GitHub-hosted runner image (or that image is deprecated and no longer supported).
In such a case, you should install Ruby in the $RUNNER_TOOL_CACHE yourself, for example using https://github.com/rbenv/ruby-build
You can take inspiration from this workflow for more details: https://github.com/ruby/ruby-builder/blob/master/.github/workflows/build.yml
$ ruby-build 3.1.4 /opt/hostedtoolcache/Ruby/3.1.4/x64
Once that completes successfully, mark it as complete with:
$ touch /opt/hostedtoolcache/Ruby/3.1.4/x64.complete
It is your responsibility to ensure installing Ruby like that is not done in parallel.
```

2. 解决方法：
https://github.com/Huxpro/huxpro.github.io/issues/502
**应该是ubuntu默认使用最新版，不兼容了。**

方法 1：替换 Setup Ruby 的步骤
你可以修改 Setup Ruby 步骤，确保其兼容性并使用正确的 Ruby 版本。更新后的代码如下：

yaml
```
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.3 # 使用 Ruby 3.3
          bundler-cache: true # 缓存 Bundler 安装的 Gems
```
这个修改会直接应用到现有的 Ubuntu 环境中，无需额外更改。

方法 2：将 Ubuntu 版本改为 22.04
如果你更倾向于使用稳定的 Ubuntu 版本（如 22.04），可以直接修改 runs-on 参数，将 ubuntu-latest 替换为 ubuntu-22.04。更新后的代码如下：

修改 build 作业：
yaml
```
  build:
    runs-on: ubuntu-22.04 # 改为使用 Ubuntu 22.04
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.3
          bundler-cache: true
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      - name: Build with Jekyll
        run: bundle exec jekyll build --baseurl "${{ steps.pages.outputs.base_path }}"
        env:
          JEKYLL_ENV: production
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
```
修改 deploy 作业：
yaml
```
  deploy:
    runs-on: ubuntu-22.04 # 改为使用 Ubuntu 22.04
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

**推荐**
优先选择方法 2（改为 Ubuntu 22.04），因为这可以避免未来潜在的不兼容问题，同时仍能使用官方稳定的 Ruby 安装方法。

完成后，将修改后的 jekyll.yml 推送到仓库，并重新触发 GitHub Actions 流程以验证修复效果！
