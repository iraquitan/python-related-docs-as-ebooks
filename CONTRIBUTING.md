# Contributing to Python related docs as ebooks

## Search project docs
Some organizations provide a link to download EPUB documentations, like [Python](https://docs.python.org/3/download.html) or [Django](https://docs.djangoproject.com/en/1.10/). Just download the EPUB file and head to [Preprocessing](#preprocessing).

## Or build if needed
If you can't find the download link for a EPUB file, you can check if the project source have a easy way to build the docs using Sphinx. One example is the [Requests](https://github.com/kennethreitz/requests) library that provide a docs folder with a Sphinx generated Makefile. If so, you can proceed like follow:

```shell
$ git clone https://github.com/kennethreitz/requests.git
$ cd requests/docs
$ make epub
```
And you will have a EPUB file in the build directory, generally `_build`.

## Preprocessing
For the preprocessing I use [Calibre](https://calibre-ebook.com/) software. You can download and install, or if you have Homebrew | Cask:

```shell
$ brew cask install calibre
```
### Edit metadata and add cover
In Calibre, import the EPUB file and edit the metadata if needed. To generate the cover file, in the `Edit metadata` panel, click on the `Generate cover` in the `Change cover` section.

![Calibre generate cover](http://3.bp.blogspot.com/-VkHLio2p57U/VChH_yMmafI/AAAAAAAAAcQ/aTsTxOz17x4/s1600/how_to_customize_1.png)

### Convert to Kindle format
Next convert the EPUB ebook to the Kindle new format `.azw3`. Make sure to check the Table of Contents (TOC).

## Submitting ebooks docs
### Fork and clone
```shell
$ git clone https://github.com/<your_user_name>/python-related-docs-as-ebooks
$ cd python-related-docs-as-ebooks
$ git checkout -b <descriptive_branch_name>
```

### Folder and filename conventions
If the project doc belongs to a organization, name the folder lowercase using dashes if it is a compose name `organization-name`. Next add another folder inside with the name of the project `foobar`, followed by another folder with the version `1.3` and finally the files named like follows:

```shell
$ls -1 ebooks/organization-name/foobar/1.3/
cover.jpg
foobar_1_3.azw3
foobar_1_3.epub
```
Or if the project does not belongs to an organization, do as follows:
```shell
$ls -1 ebooks/foobar/1.3/
cover.jpg
foobar_1_3.azw3
foobar_1_3.epub
```

### Update README
Update the README with the new ebook info, by adding a new section with a table or a new line if it is a new version.

```markdown
## Foobar Documentation
| Version | Epub     | Kindle     | Cover     |
| :------ | :------- | :--------- | :-------- |
| 1.3  | [.epub](ebooks/foobar/1.3./foobar_1_3.epub) | [.azw3](ebooks/foobar/1.3/foobar_1_3.azw3) | <img src="ebooks/foobar/1.3/cover.jpg" width="96"> |
```

### Commit message
```shell
$ git add <new_and_modified_files>
$ git commit
```

The established standard for Git commit messages is:

* When adding a new ebook doc `foobar 1.3 (new ebook)`
* When adding a new version `foobar 1.4`
* When fixing a ebook `foobar 1.4: fix ebook path`

### Push
Now just push your commit to GitHub.

If you haven’t forked this project yet, [go to the python-related-docs-as-ebooks repository and hit the fork button](https://github.com/iraquitan/python-related-docs-as-ebooks/).

If you have already forked, then you can manually push:

```shell
$ git push origin <descriptive_branch_name>
```

Now [open a pull request](https://help.github.com/articles/creating-a-pull-request-from-a-fork/) for your changes.
