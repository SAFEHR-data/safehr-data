---
layout: archive
---

# Submitting a project

You can submit your own research project for sharing here.

This is a brief over guide, but a more complete version for those less familiar with GitHub and pull requests is also [available](./project_submission_lowcode)

The simplest approach is to clone this repository locally.

## Preparing your submission

```sh
git clone https://github.com/SAFEHR-data/uclh-research-discovery.git
cd uclh-research-discovery
```

Now create a *new* directory under `./projects`, and add a file called `index.md`.

```sh
cd ./projects
mkdir my_new_project
cd my_new_project
touch index.md
```

An example is available for you in `./projects/_project_template`. You could simple duplicate and rename this directory.

```sh
cd ./projects
cp -R ./projects/* ./my_new_project
```

### The `index.md` file

Now edit the `index.md` file. It will need a YAML header as below. The additional data and results tabs are optional. If you choose to use them then each is a simple markdown file.

```yaml
---
layout: project
title: My New Project
status: ongoing
authors:
  - Jeremy Bentham
  - Charles Darwin
  - John Snow
tabs:
- {
  name: my_data_tab,
  source: data.md,
  label: Data
  }
- {
  name: my_results_tab,
  source: results.md,
  label: Results
  }
---

Here is the text introducing my study. The YAML frontmatter above will not be displayed to the user.

We recommend including your lay summary here.
```

#### YAML frontmatter

title
: By default the title for your project will be derived from the folder name by replacing any dash or hyphen characters with spaces, and converting the result to title case. Add a title here to override this

status
: Each project page displays the current status of the project on a label displayed next to the title. This can be one of two options: ongoing or completed. If not included here, the default will be ongoing.

authors
: This file must contain a list of authors added in the format shown in the example above

The tab section is optional.

### Sharing data

If you wish to share data, then we encourage the use of the UCL [Research Data Discovery](https://rdr.ucl.ac.uk/) service. You can embed a link to your data directly.

For example, the `data.md` file might be look like this.

```md
## My data

Here are the data that I used for my study

<iframe src="https://widgets.figshare.com/articles/18692549/embed?show_title=1" width="568" height="351" allowfullscreen frameborder="0"></iframe>

```

### Sharing results

Similarly, you can embed results and images in the `results.md` file. We would recommend considering the Quarto publishing system. In which case, replace `results.md` with `results.html` and include the Quarto assets folder in the project folderinclude the Quarto assets folder in the project folder. Relative links should be preserved.

### Ready to submit

Your folder structure might look like

```txt
|-my_new_project
  |-index.md
  |-data.md
  |-results.html
  |-assets/
    |-figure-html
    |-libs
```


### Tips

If you'd like to split content across several pages, or include an embed link for your data, you can add extra content by including additional markdown or html files in your project folder. This content will appear in separate tabs across the top of the page.

The name of the file is used to generate the tab label for the extra content as follows:

- The filename suffix (.md/.html is removed)
- Any underscore(_) or hyphen (-) characters are replaced with spaces
- Digits at the start of the filename are removed
- Any whitespace remaining at the start or end of the name is removed
- The name is converted to title case

As an example, the tab label for `03_code-and_data.md` would be "Code And Data".

Tab order is alphabetical (except index.md which always appears first). To determine the order in which tabs appear, use numbers at the start of your filenames (e.g. `01_methods.md`, `02_privacy.md`, `03_data.html`).

#### Assets

The site builder only picks up files with .html or .md suffixes as extra content to be included as tabs on the project page, anything else is ignored. However, you can use relative links to include other types of assets in your pages such as images, javascript, css etc. For example, you could create a folder inside your project folder called images, where you can upload all of the images you'd like to include in your pages. To upload a file, select "Upload files" from the "Add files" dropdown menu.

#### Quarto

If you use Quarto to generate an html page, you will find it generates a whole folder of assets that need to be included. No problem, just include the Quarto assets folder in your project folder alongside the html file, and the relative links to those assets should still work.

## Make a pull request

To publish your project, you will need to merge your new files back into the original GitHub repository. To do this you will need to submit a [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests). The pull request process allows us to review submissions before they are added to ensure they comply with our standards.


Your pull request will then need to be approved by two reviewers who are chosen automatically from a pool of volunteer editors. Reviewers might sometimes make comments or request changes before approving your submission so please make sure you are able to receive notifications from GitHub in order to respond to their requests.

Once approved, your project will be merged into the main branch and it will automatically appear on the live website.
