# Presentation: Slides Template

> I stopped using `reveal-md` because it [lacks support for markdown syntax using reveal plugins such as code focus](https://github.com/webpro/reveal-md/issues/187).

To generate web deployment using github pages:
- use the [`vscode-reveal`](https://marketplace.visualstudio.com/items?itemName=evilz.vscode-reveal) add-on
- configured it to save to `./docs` when generating static HTML
- configure the GitHub pages on the repo to use './docs'

Travis-CI would be a cool way to do it, but so far there is no command-line feature for the `vscode-reveal` plug-in, and I have not found a better support for markdown with reveal and its popular plugins.
