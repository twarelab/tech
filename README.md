# Website

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

### Installation

```
$ yarn
```

### Local Development

```
$ yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

### Build

```
$ yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

### Deployment

Using SSH:

```
$ USE_SSH=true yarn deploy
```

Not using SSH:

```
$ GIT_USER=<Your GitHub username> yarn deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.


# 다국어 처리

먼저,
```
$ yarn run write-translations -- --locale ko-kr
```
사용자 페이지 추가

```
# docs
mkdir -p i18n/ko-kr/docusaurus-plugin-content-docs/current
cp -r docs/** i18n/ko-kr/docusaurus-plugin-content-docs/current

# blog
mkdir -p i18n/ko-kr/docusaurus-plugin-content-blog
cp -r blog/** i18n/ko-kr/docusaurus-plugin-content-blog

# src/pages
mkdir -p i18n/ko-kr/docusaurus-plugin-content-pages
cp -r src/pages/**.md i18n/ko-kr/docusaurus-plugin-content-pages
cp -r src/pages/**.mdx i18n/ko-kr/docusaurus-plugin-content-pages
```
