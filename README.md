# Webseite Uni & Kind e.V.
This Project maintains the codebase for [Uni und Kind e.V. Website](http://www.uni-und-kind.rwth-aachen.de).
The content is written in [Markdown](https://de.wikipedia.org/wiki/Markdown), an easy text formatting syntax.
A good overview and cheet sheet is [this](https://www.markdownguide.org/cheat-sheet) one from Markdown Guide.

## Setup
To edit markdown easily we can use IntelliJ Idea or Visual Studio Code.

### Install IntelliJ
IntelliJ can be install [manually](https://www.jetbrains.com/de-de/idea/) or via [Chocolatey](https://community.chocolatey.org/packages?q=intellij):

### Install Jekyll manually
To install jekyll I suggest following the [jekyll installation instructions](https://jekyllrb.com/docs/installation/).
**Remark:** Ruby+Devkit means you need with devkit version in the newest version

### Install Jekyll via Docker
To build a Docker image via the provided Dockerfile use
```bash
podman build --tag jekyll:latest docker
```

Using the build image you can serve the website via
```bash
podman run -p 4000:4000 -v .:/var/srv -it jekyll:latest
```
and build the website via
```bash
podman run  -v .:/var/srv -it jekyll:latest /build.sh.
```

## Small Remarks

### Linebreaks
It is considered as best practice to use one line per sentence, this makes the files more readable.
Single linebreaks are ignored at site generation because the layout is defined by the website, not the content.
One can force a linebreak by introducing an emoty line.

### Image locations
It is recommended to place images used within a side or post within the same directory, this simplifies referencing.
If commonly available assets are needed (f.ex. Uni-und-Kind-Logo) they are located in the assets folder.
Keep in mind that using assets require the `{{ 'path-to-file' | relative_url }}` operation instead of direct linking.

## Technical Background
Markdown files can be edited with any texteditor, but one with support is recommended.
Common examples are [Visual Studio Code](https://code.visualstudio.com), [IntelliJ IDEA](https://www.jetbrains.com/idea/) or other code editors.

The Markdown sources are transformed into a static HTML website using [Jekyll static site generator](https://jekyllrb.com).
This can be done local with `bundle exec jekyll build` or `budle exec jekyll serve` right after the [jekyll environment setup](https://jekyllrb.com/docs/installation/).
An automated build action is configured within the [GitHub repository](https://github.com/MBoegers/uni-und-kind-v2).

For versioning we use [git](https://git-scm.com) with GitHub.
Git is already integrated within the most code editors. 
