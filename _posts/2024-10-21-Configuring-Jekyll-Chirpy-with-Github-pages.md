---
title: Setting up Jekyll / Chirpy with Github Pages!
date: 2024-10-21 12:00:00 -0500
categories: [TUTORIAL]
tags: [tutorial, hosting, github]     # TAG names should always be lowercase
description: Tutorial on how to setup and configure Jekyll and Chirpy on Github pages.
toc: true
comments: false
---

# Tutorial: Hosting a Jekyll Site with the Chirpy Theme on GitHub Pages
This guide will walk you through forking the Chirpy Jekyll theme and deploying it on GitHub Pages. By the end of this tutorial, you will have a working Jekyll website hosted on GitHub.

Prerequisites:
A development workstation running Linux.
An internet connection.

## Step 1: Install Required Dependencies
First, ensure your system is up to date and install the necessary dependencies (Node.js, Git, Ruby, and build tools):

```
sudo apt update
sudo apt install nodejs git ruby-full build-essential zlib1g-dev
```

## Step 2: Configure RubyGems Installation Directory
It's recommended to avoid installing RubyGems as the root user. Instead, set up a directory for RubyGems specific to your user account by adding the following environment variables to your `~/.bashrc` file:

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Step 3: Install Jekyll and Bundler
Once the environment variables are set, install Jekyll and Bundler:

```
gem install jekyll bundler
```

## Step 4: Fork the Chirpy Theme Repository
Sign in to GitHub.
Fork the [Chirpy Theme Repository](https://github.com/cotes2020/jekyll-theme-chirpy/fork).
Name your new repository in the format `<username>.github.io`, where `username` is your GitHub username in lowercase.

## Step 5: Clone the Repository to Your Local Machine
Clone the forked repository to your local development machine:

```
git clone https://github.com/<username>/<username>.github.io.git
cd <username>.github.io
```

## Step 6: Initialize the Repository
Run the following command to initialize your repository:

```
bash tools/init.sh
```

This will set up the necessary directories and configurations.

## Step 7: Install Dependencies
Use Bundler to install the project dependencies:

```
bundle
```

## Step 8: Run the Jekyll Server Locally
Start the Jekyll server to preview your site locally:

```
bundle exec jekyll s
```

After a few moments, the server will be available at `http://127.0.0.1:4000`. You can now preview and make changes to your site.

## Step 9: Customize Your Site
Edit the configuration in `_config.yml` to set up your site’s basic settings such as URL, avatar, timezone, and language.
Update your social media/contact information in `_data/contact.yml`.
## Step 10: Configure for Deployment
Before deploying, make sure the `url` in `_config.yml` is correct and that the `baseurl` starts with a `/`.

If you’re using GitHub Pages and you're on the Free plan, keep your repository public.

If you've committed the `Gemfile.lock` to your repository and your local machine isn't running Linux, update the platform list in the lock file with the following command:

```
bundle lock --add-platform x86_64-linux
```

## Step 11: Deploy Using GitHub Actions
Navigate to your repository on GitHub and click the Settings tab.
From the left navigation bar, select Pages.
In the Source section, under Build and deployment, choose GitHub Actions from the dropdown menu.
Push any changes to GitHub to trigger the Actions workflow.
You can monitor the workflow in the Actions tab of your repository. Once the build and deploy process is complete, your site will be live.

## Step 12: Access Your Site
After deployment, visit the URL provided by GitHub to view your live website at `<username>.github.io`.

And that's it! You now have a Jekyll site hosted using GitHub Pages with the Chirpy theme. Great job!