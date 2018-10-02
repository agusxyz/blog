---
title: 'How to Install and Use Octopress on Windows'
date: 2017-08-18T00:41:00.000-07:00
draft: false
---

A quick and easy 6 steps tutorial to get up and running with octopress and github pages

> **NOTE:** As a pre-requisite you should make sure you have a public github repo with the name : `yourusername.github.io`

### Step 1: Install Chocolatey

1.  Got to [http://chocolatey.org](http://chocolatey.org/)
2.  Open a command prompt
3.  cd to `c:\`
4.  Paste in and execute the following code from chocolatey home page

  

Install Chocolatey

1  
2  
3  

    @powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))"&& SET PATH=%PATH%;%systemdrive%\chocolatey\bin

  

This will install chocolatey in `C:\Chocolatey`

### Step 2: Make sure Git is installed or install it via Chocolatey

  

Install Git with Chocolatey

1  

    choco install git

  

To check that git is installed close and reopen a command prompt and run the following command:

  

Check Git version

1  

    git --version

  

You should get `git version 1.0.0.msysgit.0`

### Step 3 : Install Ruby and Python

1.  Install `Ruby 1.9.3-p545` from `http://rubyinstaller.org`
2.  Ruby should be installed in `C:\Ruby193`
3.  Add the following path to the system variables Path : `c:\Ruby193\bin`
4.  Exit and reopen command prompt and run `ruby --version`, you should get `ruby 1.9.3-p545`
5.  Install ruby developpement kit with chocolatey

  

Install Ruby Devkit with Chocolatey

1  
2  

    c:choco install ruby.devkit

  

This will install the devkit in C:\\Devkit  
6\. Install python

  

Install Python with Chocolatey

1  

    choco install python

  

7\. Exit and reopen command prompt and run `python --version`, you should get `Python 2.7.6`

### Step 4 : Install Octopress

Navigate to your github local repositories folder (for example mine is d:\\github) The installation of Octopress consist in cloning the repository of Octopress

  

Clone Octopress repository

1  

    git clone git://github.com/imathis/octopress.git blog

  

Navigate to the created folder and then run the following command to install the dependencies

  

Install Octopress dependencies

1  
2  

    gem install bundlerbundle install

  

Then install the default Octopress theme

  

Install Octopress default theme

1  

    rake install

  

Next edit `_config.yml` and adjust it with your blog properties (title,name, google tracker, etc…)

And now we can generate the site

  

Generate and preview Octopress blog

1  

    rake generate && rake preview

  

You can open a browser and navigate to `http://localhost:4000`

### Step 5 : Blogging

To create a new post

  

Create a new blog post

1  

    rake new_post["Hello World Post No 1"]

  

The new post file is a simple markdown file generated in `source\_posts`

### Step 6 : Publishing your blog to github pages

Github pages expect to have two branches, the source branch and the master branch. The master branch is the one that github pages will show. The changes in the source branch won’t be published until you push your changes to master. You can configure those branchs manually and add your github pages repository as a remote, but there is also a rake task that does all for you:

  

rake command for setting up github pages

1  

    rake setup_github_pages[repo].

  

In the case of this blog, I ran `rake setup_github_pages[git@github.com:yourusername/yourusername.github.io.git]`and then `rake deploy` to upload the blog. In a snap the blog will be accessible at the url [http://yourusername.github.io.](http://yourusername.github.io./)

Remember that rake deploy just generates the blog a push to the master branch. Your source branch won’t be uploaded to github if you don’t want to. You probably want, to have a secure backup online, among other reason. Commit your changes and do

  

pushing the sources

1  

    git push origin source.

  

Workflow when editing your blog
-------------------------------

1.  Make your modification to your local repo using `rake new_post` and editing your markdown
2.  `rake generate && rake preview` to check your changes
3.  `git add .` and `git commit -m "update blog"`
4.  `rake deploy` to deploy the resulting blog
5.  `git push origin source` to deploy your Octopress sources

Tips
----

If you need to put images in your blog just place them in source\\images and reference them with

  

img

1  

    <img src="{{root-url}}/images/yourimage.png" />

  

If you get an error from github when executing `rake deploy` saying that

  

1  
2  
3  
4  
5  
6  
7  

    ! [rejected]        master -> master (non-fast-forward)error: failed to push some refs to 'https://github.com/user/user.githubit'hint: Updates were rejected because the tip of your current branch is behindhint: its remote counterpart. Integrate the remote changes (e.g.hint: 'git pull ...') before pushing again.hint: See the 'Note about fast-forwards' in 'git push --help' for details.

  

Modify the Rakefile at the root of the project by replacing the following line:

  

1  

    system "git push origin #{deploy_branch}"

  

with

  

1  

    system "git push origin +#{deploy_branch}"

  

Try to deploy again and then revert back Rakefile to its original content

Now you have no excuse not making a blog of your own…

Let me know what you think and happy coding.  
  
source : http://thaiat.github.io/blog/2014/03/13/how-to-install-and-use-octopress-on-windows/