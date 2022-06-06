---
title: "How to set up this website using Hugo part2"
date: 2022-06-04T01:122:42+02:00
author: "Emmanuel Amadio"
linktitle: How to set up this website using Hugo
# next: /spring-boot-devtools-on-intellij
prev: /set-hugo-1
weight: 3
authorAvatar: image/logo.svg
image: image/3/selfBlog.png
tags : [
    "hugo",
    "blog",
    "tutorial",
]
categories : [
    "tutorial"
]
draft: false
---

In part 1 we explored how to create a website using Hugo, now we are going to create a github action to automatically deploy the site on github pages when we create a commit.

### **Set up Git repositories**

We will create 2 GitHub repositories for the project

1. First Repository for main project `github-page`
2. Second repository to host our blog as Github User page

We would also link both these repositories using Github sub-modules.

Create a repository like [https://github.com/bhanuchaddha/github-page](https://github.com/bhanuchaddha/github-page). And one more repository like [https://github.com/bhanuchaddha/demoblog-bhanuchaddha.github.io](https://github.com/bhanuchaddha/demoblog-bhanuchaddha.github.io). Second repository must be in `<Your-Github-User-Name>.github.io` format. It is important because Github allows only 1 User/Organization page. We are using Github User page for this blog.  Github initialize the static website for us if you specify `.github.io` at the end of a repository name.

Now go to the root of the project and execute below commands.

```
# set sub-module mapping
git sub-module add -b main https://github.com/eamadio/eamadio.github.io public

# commit any uncommitted changes
git commit -a -m "init"

# set remote origin branch
# git remote add origin https://github.com/<Your-Github-User-Name>/github-page.git
git remote add origin https://github.com/eamadio/eamadio.github.io.hugo.git

# push changes
git push -u origin master
```

We have mapped `public` directory in root as sub-module, which is mapped to `<Your-GitHub-User-Name>>.github.io` repository. If you check the public directory it is empty now. 

But if you run below command in the root directory. You will see `Hugo` generate the static content based upon the configuration and content.

Before generate static content, there is one last thing we need to change in our `config.toml` file. Remember we kept `baseurl` as empty. Because now we know the url of our blog website repository, we can set this value. Set below for baseurl

`"https://<Your-GitHub-User-Name>.github.io"`

Runt the command now

```
hugo -t casper-two
```

### **Push your content**

Now we have set up our repositories and created our static content in `public` directory . The only step remain is pushing our local content to GitHub. Lets do that now. Run below commands in the terminal

```
# go to public directory
cd public

# commit static content
git commit -a -m "init blog content"

# push your content
git push
```

And thats it. Now if you go to [https://<Your-GitHub-User-Name>.github.io](https://<Your-GitHub-User-Name>.github.io
) , you will notice that your website is up and ready now. You should see something like [https://bhanuchaddha.github.io/demoblog-bhanuchaddha.github.io/](https://bhanuchaddha.github.io/demoblog-bhanuchaddha.github.io/). I have observed that it take minute or 2 to reflect the changes.

You can match your content and configuration with below repositories. The only difference is the value of `baseurl` that is because I have set up this demo website as Project Site and not the User Site.

1. [Project Repository](https://github.com/bhanuchaddha/github-page)
2. [Blog Repository](https://bhanuchaddha.github.io/demoblog-bhanuchaddha.github.io)

### **From here**

Now you can update your `first-blog.md` file or write new blog by creating more `*.md` files in `post` directory. Do remember to add front matter on the top of each blog file. After creating new blog files just repeat below steps to publish your new blog

1. Generate static content using `hugo -t casper-two` command.
2. Go to public directory and commit your changes 
3. Go back to main directory and commit your changes. 


If you are still reading this blog. I know it was a long post . But I hope it was worth it. 
Do reach me out if you have any questions. 