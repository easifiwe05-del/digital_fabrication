# UR-ACEIoT student documentation

Visit [UR-ACEIoT Modeling & Fabrication](https://fablabrwanda.github.io/UR-ACEIoT/index.html) for class and other information
or read the [Documentation Tutorial](http://https://fablabrwanda.github.io/UR-ACEIoT/documentation-tutorial/) for more about this site.


* This website is built and published automatically using [GitLab CI](https://about.gitlab.com/gitlab-ci/), every time you edit the files in the docs folder
* The markdown content is generated into a site using the Mkdocs tool, a static site generator written in Python
* You can start by customizing the file `mkdocs.yml` with your information
  * To change the looks of your website, use the theme options found in the `mkdocs.yml` file or see the names of the available themes
* If you want to start a website from scratch, you can delete everything in this repository and push your own static website


## Documentation layout

    mkdocs.yml          # The site configuration file.
    docs/               # All site content/files should be in this folder.
        index.md        # The homepage.
        files/          # Put files you'd like available in your site here (except videos)
        images/         # You can put your images in here
        Daily-Activity  # Document daily activity give for each lecture
        ...             # Other markdown pages and folders

Read more about MkDocs at [mkdocs.org](https://www.mkdocs.org).


## Building locally

To work locally on your computer with this project, you can start with the following the steps:

1. Fork, clone, or download this project (to your computer)
1. Either check out [official docs](https://www.mkdocs.org/user-guide/installation/) to install MkDocs on your computer.
1. Or this quick guide, if you already have python v3 install on your computer (ie. Windows):
    * `pip3 install -r requirements.txt` to intall mkdocs (or just `pip`)
    * `python3 -m mkdocs serve` to run your site (or just `python`)
1. Now you can see the live preview of your project using this `mkdocs serve` command.
    * Watch the terminal output of the command for the URL to your site (e.g. `http://127.0.0.1:8000/`)
1. Edit the markdown pages in the `docs` folder and see your changes in the browser.
1. To add new pages, create the markdown file in the `docs/` folder (i.e. `docs/new-page.md`)
1. Finally use GIT to push your changes to GitLab (or add manually through the "Github Web IDE", check your repo page).

