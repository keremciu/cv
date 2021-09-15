[keremciu.github.io/cv]: https://keremciu.github.io/cv
[latest release]: https://github.com/keremciu/cv/releases/latest

# Source of Kerem Sevencan's CV

| Website                       | PDF Version      |
|----------------------------   |------------------|
| [keremciu.github.io/cv] | [latest release] |

**If you want to have your own, just fork this repo and modify the `index.md`.**

This is a fairly modified version of
[eralpkaraduman's markdown-cv](http://eralpkaraduman.github.io/cv) project.  
Which is using [jekyll](https://jekyllrb.com) to host the cv as static site on github.


## Features
- Maintain your cv using Markdown
- Free website for your CV _(hosted on github-pages)_
- Automaticaly updated PDF version _(hosted on github releases)_
- Always have one link to your latest CV online for free
- Update it easily on the web _(using github's web editor)_


## Automatic PDF version generation

If you configure the GitHub Action, it creates a pdf version then create a release on github. You can always link to the latest release by adding the sufffix `/releases/latest` to repo url.  
For example;  
github.com/your-username-here/cv[/releases/latest](https://github.com/eralpkaraduman/cv/releases/latest)

To enable this;  
- Go to [github.com/settings/tokens](https://github.com/settings/tokens)
- Generate a personal access token, give it `public_repo` permission
- Go to the secrets settings of this github repo (the one that is your clone)
  - https://github.com/your-username-here/cv/settings/secrets/actions
  - Remember to change the username in the url above
- Click "New repository secret" 
- Name it `GH_OAUTH_TOKEN`
- Paste the token you generated in the earlier step here
- Next time you make a change, it should create a new release under `/releases` page of your github repo
- Latest release is conveniently always at `/releases/latest`


## Including downlad link to PDF version in the website

I added a feature which automatically adds the latest PDF version download link to the website.   
This only works when automatic PDF version generation was set up (mentioned above).   
This is done by javascript running on the page, it tries to fetch github's API to get the last release.  
This link won't be generated in the PDF itself for several reasons;  
- Lack of necessity, since you have the pdf there's no need to download it again.
- I didn't want to figure out the issues with executing javascript in pdf generation context
- I disabled javascript on wkhtmltopdf, see reasons above.


## Running jekyll locally

*(You don't need to run it locally to update this, do it on github's web ui)*    

Since after your every change a new cv will be generated, this may cause excessive number of generations. To avoid this you may choose to make several commits on your local environment. Then push them all at once. To be able to preview the CV you should run Jekyll locally.

You should look at [jekyll's own documentation](https://jekyllrb.com/docs) but,
this is how you'd get started;  

`bundle install`  
`bundle exec jekyll serve --host=0.0.0.0`
