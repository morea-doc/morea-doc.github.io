What is Morea?
==============

The name "Morea" is an acronym for Modules, Outcomes, Readings, Experiences, and Assessments. These are
the five building blocks of Morea's approach to creating online course web sites, where:

* A *course* consists of a sequence of modules;
* A *module* consists of one or more outcomes, readings, experiences, and assessments.
* An *outcome* is a "student learning outcome", or educational goal for the module.
* A *reading* is an online resource (web page, PDF file, YouTube video, etc.) providing explanations useful to
achievement of one or more of the outcomes.
* An *experience* is an activity with which the learner engages in order to acquire the information. Sometimes these
are referred to as "homework assignments".  They could also be meetings or events. They typically help the learner
to assimilate information in the readings.
* An *assessment* is a mechanism used to help the learner determine if they have actually achieved the desired outcomes.

Why Morea?
==========

After years of recreating class websites from scratch using WordPress, I started this project to make easier for
me to create, share, and modify educational material. Initially, I just wanted to get away from a traditional CMS
and use git for course content management.  As I started prototyping, I realized that my educational approach typically
contains the same five building blocks, and so I baked them into the framework as well.

The content for a Morea-based course is contained in a [GitHub](http://github.com) repository.  Note that educators (with a .edu account) can get a
free "micro" GitHub account with 5 private repositories. Such a repo can contain both private content (such as tests) and
 public content (the published web site), which is quite convenient.

A Morea course website is generated by running [Jekyll](http://jekyllrb.com), and published using [GitHub Pages](http://pages.github.com/).
In essence, a Morea course is just a Jekyll website that is structured in a particular way and has a couple of custom plugins.
Hopefully, you don't need to learn much about Jeykll to use Morea efficiently.

The [Morea github organization](http://morea-doc.github.io) provides templates you can use to build course websites from scratch.  Even better,
you can fork an existing course repo and modify it to suit your own course needs.

Getting started
===============

Join GitHub
-----------

If you haven't already, [sign up for GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account).
If you are associated with an educational institution (i.e. have a .edu email account), you can [request a free micro account](https://education.github.com/) providing you with 5 private repos.

Install git
-----------

Follow these instructions to [install git](https://help.github.com/articles/set-up-git). (Be sure to click the tab corresponding to your OS.)

Install Jekyll
--------------

Next, [install Jekyll](http://jekyllrb.com/docs/installation/). Jekyll is the system used by Morea to convert the source
files into the actual website. Note that Jekyll is easy to install on Linux and Mac, less so on Windows.
If you have problems, you might want to consider using [Vagrant for Jekyll site generation](http://dwradcliffe.com/2013/04/12/vagrant-to-compile-jekyll.html).

Fork the template-basic repo
----------------------------

Morea provides the [template-basic](https://github.com/morea-doc/template-basic) repo for new Morea users. Go to this page,
then press the "Fork" button in the upper right corner.  This will create a copy of that repo in your own account and
take you to your new repo's home page.

Now click the "Settings" link on the right side of the page, and rename the repo from "template-basic"
to the name of the course you wish to develop (such as "CS300").  If you are just experimenting, you might name
it "MoreaTest".

You now have a Morea repo, but it's in the cloud. To actually develop your site, you need to create a local environment.

Set up your local directory structure
-------------------------------------

Developing a Morea site requires managing (at a minimum) two branches for each repo: the "master" branch containing the source
files for your course, and the "gh-pages" branch containing the website files produced by running Jekyll over your
source files. So, development of your course involves (at a minimum) the following workflow:

  * Improve your content by editing the source files in your master branch.
  * Run Jekyll to produce the improved website in your gh-pages branch.
  * Commit the gh-pages branch to GitHub to make the improved website publicly available.
  * Commit the master branch to GitHub to back up your improvements to the cloud and make your sources available to others.

A simple way to facilitate this workflow is to create a top-level directory containing two subdirectories, one
containing the master branch of your repo, and one containing the gh-pages branch of your repo. For example, if your repo is
named "MoreaTest", then your directory structure would be:

    moreatest/
      master/
      gh-pages/

An additional complexity is that GitHub [requires the gh-pages branch to be an "orphan" branch](https://help.github.com/articles/creating-project-pages-manually).

To get there, do the following:

1. Create the top level directory manually:

    $ mkdir moreatest

2. Clone the master branch of your repo into a subdirectory named master

    $ cd moreatest
    $






First, create your repository and orphaned gh-pages branch as discussed [here](https://help.github.com/articles/creating-project-pages-manually).  Your master branch can start as a clone of this repo's master branch.

Maintain two parallel directories locally.  In my case, these directories are: ase-mockup/ (containing the master branch of the ase-mockup repo) and ase-mockup-gh-pages/ (containing the "orphaned" gh-pages branch of the ase-mockup repo).

Local development
---------------------

The [jekyll github-pages](http://jekyllrb.com/docs/github-pages/) page contains important info on setting the baseurl property in _config.yml.  If you don't configure this correctly, then the links and css may not resolve correctly.

The jekyll source code lives in the src/ directory.  To run the local version, cd to the src/ directory and invoke:

    jekyll serve --baseurl "" --watch

The results are at http://localhost:4000.  The --watch options means rerun jekyll when files change.  Combine this with [LiveReload](http://livereload.com/) and your browser will refresh whenever a change is made. Sweet!

Publishing to github
-------------------------

To "publish" the site, run jekyll to process the files in the src/ directory and generate html into the ase-mockup-gh-pages directory. For this repo, you do the following:

    $ cd ase-mockup/src
    $ jekyll build --destination ../../ase-mockup-gh-pages

Then use git to commit the derived html to the gh-pages branch:

    $ cd ../../ase-mockup-gh-pages
    $ git commit -a -m "Commit latest html sources"
    $ git push origin gh-pages

