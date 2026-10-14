---
title: Writting Documentation
description: Writting new documentation.
---

# <p style="text-align: center;"> Writting Documentation </p>

As a team, we want our software and hardware decisions well-documented and kept in one place to ensure that new members can easily learn the big and complex system they work with, as well as quickly be plugged into development process. As such, after achieving a significant milestone, it is highly recommended to document it and contribute to this website. It is a lot easier than it sounds.

To start, install the necessary dependencies in WSL or the terminal. **Do not do this in the dev container!**

``` bash
pip install mkdocs
pip install mkdocs-material
```

Then, clone the github repository:

``` bash
git clone git@github.com:advt-vt/advt-vt.github.io.git && cd advt-vt.github.io && code .
```

You may now make changes to the website code. To edit an existing page, simply find its .md file in `docs` and edit the text inside. To add a new page, add the file into whichever folder you want it to be (or create a new folder), type it up, and then include in `mkdocs.yml`. The documentation supports html, markdown, and several extensions. [You can read about the extensions here](https://facelessuser.github.io/pymdown-extensions). You can read the [mkdocs documentation here](https://squidfunk.github.io/mkdocs-material/reference/)

To put your changes on the website, run:

``` bash
mkdocs serve
```

This will open the website to run locally on the <http://127.0.0.1:8000/> (localhost) IP address. To access it, just type that link in the web-browser.

After you feel good about your changes, push them to the repo first. then deploy them to the website with the following command.

``` bash { .yaml .no-copy }
git add --all
git commit -m "Put a descriptive message here"
git push
```

``` bash
mkdocs gh-deploy
```
