---
layout: post
title: "Content Workflow"
date: 2022-02-02 10:00:00 -0600
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: /p_Content_workflow/intro.png # Add image post (optional)
tags: [Conference, Workflow, GitLab] # add tag
---

# Content Workflo
This post contains the common used workflow for the update of posts contents and how it is commit to the remote repository.

******************************************************
## Table of Contents
1. [Welcome](#welcome)
2. [Info & Docs](#information-and-documentation)
3. [GitLabCI](#gitlab-ci )
4. [GitLab User or Group Pages](#gitlab-user-or-group-pages)
5. [Customization](#customization)
6. [Remove Fork Relationship](#remove-fork-relationship)
7. [Troubleshooting](#troubleshooting)


## Welcome 
- This is the readme file with common instructions on how to delpoy a blog site with [jekyll] in Gitlab pages.
- This site was constructed using [jekyll] by the user: :8ball:Z37:8ball:
- All content is written in english :us: and some in spanish :es:.

## Information and Documentation 
### :notebook_with_decorative_cover:

 1. :gem: Example [jekyll] website using GitLab Pages.
 2. :book: For more advanced and specific topics visit the GitLab Pages documentation at https://pages.gitlab.io. 

<!---
New section division
New section division
New section division
-->

## GitLab CI 
### :wrench: :hammer:
This project's static blog is built by [GitLab CI][ci], following the steps

defined in [`.gitlab-ci.yml`](.gitlab-ci.yml):

```
# requiring the environment of Ruby 2.3.x
image: ruby:2.6

# add cache to 'vendor' for speeding up builds
cache:
  paths: 
    - vendor/

before_script:
  - bundle install --path vendor

# add a job called 'test'
test:
  stage: test
  script:
    - bundle exec jekyll build -d test/
  artifacts:
    paths:
      - test # generating site folder to be browsed or download
  except:
    - master # the 'test' job will affect all branches expect 'master'

# the 'pages' job will deploy and build your site to the 'public' path
pages:
  stage: deploy
  script:
    - bundle exec jekyll build -d public/
  artifacts:
    paths:
      - public
  only:
    - master # this job will affect only the 'master' branch
```

<!---
New section division
New section division
New section division
-->

## GitLab User or Group Pages
To use this project as your user/group website, you will need one additional

step: just rename your project to `namespace.gitlab.io`, where `namespace` is

your `username` or `groupname`. This can be done by navigating to your

project's **Settings**.  

Read more about [user/group Pages][userpages] and [project Pages][projpages].

<!---
New section division
New section division
New section division
-->

## Customization
### :pencil2: :triangular_ruler: :straight_ruler:
To work and add content with this project inside Gitlab, you'll have to follow the steps below. Adding content depends on what is the addition made, like a new page, post or graphical content. Below is the general structure of the workspace of the files and folders that englobe the whole blog site.
```
├── name_of_PARENT_FOLDER
|   ├── _includes -------------------------------------- Blog site folder with files of footer,head,header *.html.
|   ├── _layouts --------------------------------------- Folder which with the layout for the pages/post of the site.
|   ├── _posts/---------------------------------- This folder is where your posts are.
|   |	|   ├── yyyy-mm-dd-name-of-post.md ------ Sample post name syntax form.
|   ├── _sass ----------------------------------- sass files, containing sass syntax, to format the layout of the site.
|   |	├── _base, _layout, _syntax...*.scss ---d scss files.
|   ├── _css ------------------------------------ Main css file.
|   |	├── main.css----------------------------- This is the css file for the blog site style.
|   ├── layout
|   |	├── default.html-------------------------------- This is the default layout for the pages of the blog site.
|   ├── _config.yml ------------------------------------ The configuration settings for the site.
|   ├── .gitignore ------------------------------------- git .gitignore file.
|   ├── .gitlab-ci.yml --------------------------------- Gitlab configuration file for Gitlab CI/CD pipeline.
|   ├── about.md --------------------------------------- The about blog site page.
|   ├── feed.xml --------------------------------------- Feed xml file.
|   ├── Gemfile ---------------------------------------- A list of gem dependencies.
|   ├── index.html ------------------------------------- Index main page.
|   ├── README.md -------------------------------------- Read file documentation for the blog site construction.
|   ├── Resume.md -------------------------------------- The resume blog site page.
```
The branch used in this case is always the master branch.
1. First add some content. 
2. Commit the changes to the master branch; add comments to necessary updates.
3. To preview the project waith for the pipelince to finish on the CI/CD Pilelines of the gitlab project.
4. Once the pipeline has passed, visit youe new blog site at the pulished gitlab pages site, which might be ```https://user_name.gitlab.io``

### The basic workflow is shown below: 

### The basic workflow is shown below: 
<script async src="https://unpkg.com/mermaid@8.2.3/dist/mermaid.min.js"></script>
<div class="mermaid">
graph LR; 
Content_update-->Pipeline_test; Pipeline_test-->Passed;
Pipeline_test-->Not_Passed;
Passed-->Deployment;
Not_Passed-->Review_code;
Not_Passed-->Review_pipeline;
Deployment-->visit_blog_site_page;
</div>



### Gantt Diagram

<!-- this is a gantt diagramm-->

<div class="mermaid">
gantt
       dateFormat  YYYY-MM-DD
       title Adding GANTT diagram functionality to mermaid

       section A section
       Completed task            :done,    des1, 2022-01-01,2022-01-08
       Active task               :active,  des2, 2022-01-09, 3d
       Future task               :         des3, after des2, 5d
       Future task2              :         des4, after des3, 5d

       section Critical tasks
       Completed task in the critical line :crit, done, 2022-01-06,24h
       Implement parser and jison          :crit, done, after des1, 2d
       Create tests for parser             :crit, active, 3d
       Future task in critical line        :crit, 5d
       Create tests for renderer           :2d
       Add to mermaid                      :1d

       section Documentation
       Describe gantt syntax               :active, a1, after des1, 3d
       Add gantt diagram to demo page      :after a1  , 20h
       Add another diagram to demo page    :doc1, after a1  , 48h

       section Last section
       Describe gantt syntax               :after doc1, 3d
       Add gantt diagram to demo page      :20h
       Add another diagram to demo page    :48h
</div>
 

## Remove Fork Relationship
If you forked this project for your own use, please go to your project's

**Settings** and remove the forking relationship, which won't be necessary

unless you want to contribute back to the upstream project.


## Troubleshooting

1. CSS is missing! That means two things:

* Either that you have wrongly set up the CSS URL in your templates, or your static generator has a configuration option that needs to be explicitly set in order to serve static assets under a relative URL.
  

[ci]: https://about.gitlab.com/gitlab-ci/

[jekyll]: https://jekyllrb.com/

[install]: http://nanoc.ws/doc/installation/

[documentation]: https://jekyllrb.com/docs/

[userpages]: https://docs.gitlab.com/ce/user/project/pages/introduction.html#user-or-group-pages

[projpages]: https://docs.gitlab.com/ce/user/project/pages/introduction.html#project-pages
