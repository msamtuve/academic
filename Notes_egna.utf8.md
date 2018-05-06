
<!-- rnb-text-begin -->

---
title: "Anteckningar rörande blogdown"
author: "Magnus"
date: '2018-01-08'
output: html_notebook
---

testtext

# problem och lösningar
Har fått problem med build.

8:47:28 PM: Building sites …
8:47:28 PM: ERROR 2018/04/10 18:47:28 Error while rendering "home" in "": template: theme/index.html:1:3: executing "theme/index.html" at <partial "widget_page...>: error calling partial: template: theme/partials/widget_page.html:23:9: executing "theme/partials/widget_page.html" at <partial $widget $par...>: error calling partial: template: theme/partials/widgets/projects.html:66:84: executing "theme/partials/widgets/projects.html" at <delimit .Params.tags...>: error calling delimit: can't iterate over <nil>

**Lösning**: Ta bort en html som skapats i min mapp content/project. Skapades när jag gjorde en preview.


# Uppdatera löpande
Nedan är hur jag fick igång det hela. Men hur gör jag nu för att:

- ändra i RStudio
- uppdatera GitHib
- Se ny version på webben via Netlify


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeSgpXG5gYGAifQ== -->

```r
library()
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


Tror man måste göra så här:

- ändra i innehåll, lägga till delete (tar bort sidor i Finder. Obs - blir error i deployment om borttagen sida refereras till på andra sidor!)
- markera i Git-pane
- commit
- commit notes
- commit
- Push

Inget händer. Loggar in på Netlify. Tittar på inställningar. Den säger att siten uppdaterades för 1 min sedan. 

Och nu ser jag ändringar. Är det en lagg. Kan det ta några minuter innan webb-version ändras??

Kan titta här: https://app.netlify.com/sites/magnus-tuvendal/deploys
Ser om build fungerar.

## Diverse edits

<div class="embed loopy">

<iframe width="500" height="440" frameborder="0" src="http://ncase.me/loopy/v1.1/{{ index .Params 0 }}"></iframe>

</div>

# ett försök till egen shortcode. Lyckas inte få det att fungera.
# Nedan är vad jag lägger in som param.
# {{< loopy "?embed=1&data=[[[1,75,228,0.5,%22sk%25C3%25A4nka%2520pengar%22,4],[2,65,488,0.5,%22b%25C3%25A4ttre%2520liv%22,5],[4,614,592,0.5,%22b%25C3%25A4ttre%2520livssituation%22,4],[5,650,203,0.5,%22sk%25C3%25A4nka%2520pengar%22,3],[6,426,429,0.5,%22antal%2520tiggare%22,4],[7,809,422,0.5,%22brottslighet%22,0],[8,412,121,0.5,%22mitt%2520v%25C3%25A4lbefinnande%22,3]],[[2,1,94,-1,0],[1,2,89,1,0],[5,4,54,1,0],[4,6,20,-1,0],[6,5,62,1,0],[5,6,35,1,0],[5,7,94,1,0],[7,4,-24,-1,0],[5,8,-53,1,0],[6,8,106,-1,0],[1,2,151,1,0]],[],8%5D" >}}

- **Ta bort widget**: gå in i content>home> och öppna en widget. Här sätter man **active = false**.
- 


### lägga in draft utan att det visas
*draft*: You can mark a document as a draft by setting draft: true in its YAML metadata. Draft posts will not be rendered if the site is built via blogdown::build_site() or blogdown::hugo_build(), but will be rendered in the local preview mode (see Section D.3).

> har inte testat detta än.

## Lite tips på texter och stilar

#### Varningsruta
Kan varna genom en ruta i röd färg med vit text genom dessa taggar.
{{% alert warning %}}
bla bla…
{{% /alert %}}

#### Alert-ruta
{{% alert note %}}
bla, bla...
{{% /alert %}}

#### lägga in URL??

[I'm an inline-style link with title](http://ncase.me/loopy/v1.1/?embed=1&data=[[[1,247,282,0.5,%22sk%25C3%25A4nka%2520pengar%22,4],[2,237,542,0.5,%22b%25C3%25A4ttre%2520liv%22,5],[4,786,646,0.5,%22b%25C3%25A4ttre%2520livssituation%22,4],[5,822,257,0.5,%22sk%25C3%25A4nka%2520pengar%22,3],[6,598,483,0.5,%22antal%2520tiggare%22,4],[7,981,476,0.5,%22brottslighet%22,0],[8,584,175,0.5,%22mitt%2520v%25C3%25A4lbefinnande%22,3]],[[2,1,94,-1,0],[1,2,89,1,0],[5,4,54,1,0],[4,6,20,-1,0],[6,5,62,1,0],[5,6,35,1,0],[5,7,94,1,0],[7,4,-24,-1,0],[5,8,-53,1,0],[6,8,106,-1,0],[1,2,151,1,0]],[],8%5D)




# Getting started

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuaW5zdGFsbC5wYWNrYWdlcyhcImJsb2dkb3duXCIpXG5ibG9nZG93bjo6aW5zdGFsbF9odWdvKClcbmJsb2dkb3duOjp1cGRhdGVfaHVnbygpXG5gYGAifQ== -->

```r
install.packages("blogdown")
blogdown::install_hugo()
blogdown::update_hugo()
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


OK. Nu är jag igång.

## Preview site
Jag kan skapa en ny site med *blogdown::new_site()*. Men det vill jag inte nu.
Hur gör jag för att öppna/ladda en existerande site jag redan gjort?

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuYmxvZ2Rvd246OnNlcnZlX3NpdGUoKVxuYGBgIn0= -->

```r
blogdown::serve_site()
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

Nu har min site publiserat lokalt.

Om inte siten uppdaderas automatisk när jag sparar filen i Rstudio så kolla: options(servr.daemon = TRUE).
- men var hittar jag detta?

### Theme - academic
Jag använder academic.
- Ref: https://github.com/gcushen/hugo-academic


## Edit site - config.toml
Grundinställningar görs i *config.toml*.

To edit a website (https://bookdown.org/yihui/blogdown/workflow.html):
1. Click the RStudio addin “Serve Site” to preview the site in RStudio Viewer. This only needs to be done once every time you open the RStudio project or restart your R session. Do not click the Knit button on the RStudio toolbar.
2. Use the “New Post” addin to create a new post or page, then start writing the content.
3. Use the “Update Metadata” addin to modify the YAML metadata if necessary.


## Publish site

To publish a website if you are not familiar with GIT or GitHub:

1. Restart the R session, and run blogdown::hugo_build(). You should get a public/ directory under the root directory of your project.
2. Log into https://www.netlify.com (you can use a GitHub account if you have one). If this is the first time you have published this website, you can create a new site, otherwise you may update the existing site you created last time. You can drag and drop the public/ folder from your file viewer to the indicated area on the Netlify web page, where it says “Drag a folder with a static site here.”
3.Wait for a few seconds for Netlify to deploy the files, and it will assign a random subdomain of the form random-word-12345.netlify.com to you. You can (and should) change this random subdomain to a more meaningful one if it is still available.

It can be much easier to publish a website if you are familiar with GIT and GitHub. We **recommend that you create a new site on Netlify from your GitHub repository** that contains the source files of your website, so that you can enjoy the benefits of continuous deployment instead of manually uploading the public/ folder every time. With this approach, you do not need to run blogdown::hugo_build() locally, because the website can be built on Netlify via Hugo. See Chapter 3 for more information.

### Getting site from RStudio to Github
En bra resurs, tutorial: https://notes.peter-baumgartner.net/tutorial/blogdown-tutorial-part-1/
**RStudio, Git and GitHub**: http://r-pkgs.had.co.nz/git.html#git-init

- Creating a new GitHub repository: detta har jag redan gjort.
- Tell Git your name and email address. These are used to label each commit so that when you start collaborating with others, it’s clear who made each change. In the shell, run:
- **git config --global user.name "Magnus Tuvendal"**
- **git config --global user.email "Magnus.tuvendal@gmail.com"**
- RStudio is Tools > Shell. 
If you’ve never used the shell before, I recommend playing Terminus: http://web.mit.edu/mprat/Public/web/Terminus/Web/main.html.

Kan testa med **git config --global --list**:
>user.name=Magnus Tuvendal
>user.email=magnus.tuvendal@gmail.com
>MacBookPro-47:Academic_blogdown magtuv$ 

From R, you can check if you already have an SSH key-pair by running:

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZmlsZS5leGlzdHMoXCJ+Ly5zc2gvaWRfcnNhLnB1YlwiKVxuYGBgIn0= -->

```r
file.exists("~/.ssh/id_rsa.pub")
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

### Create a local Git repository
Problem - jag kan inte välja i Tools/Project options/Git/versions control
Här finns bara alternativet **none**- Ska här välja **Git**.
Testar att ändra: Preferences/Git/git executaple. Ändrar path till: /usr/local/git/bin/git

Nu fungerar det! Har aktiverat Git i "Project options"!
Har nu en *git pane* i RStudio

### bring these folders and files under version control
- I Git pane så kryssar jag i under *Staged*. Får då status A på paths.
- click in the Commit tab opens up a new window where you must write a message. This first (e.g.initial) commit will bring all the files under version control.

En konsekvens är att nu har alla paths i Git pane försvunnit! kanske för att de nu är sparade och inte ändrade.

Japp - så är det. Sparade nu min Notes_egna_rmd och då dyker den upp i Git pane.

### Set up github repository. 
Väljer:
- …or push an existing repository from the command line:
> git remote add origin git@github.com:msamtuve/academic.git
> git push -u origin master

Och NU är kopplingen mellan mitt project i RStudio och Github etablerad.

### Setting global options in your R startup profile file

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZmlsZS5lZGl0KFwiLlJwcm9maWxlXCIpXG5gYGAifQ== -->

```r
file.edit(".Rprofile")
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

Nu har jag gjort det.
Detta initieras varje gång jag startar detta projekt: 
>options(servr.daemon = TRUE, 
        blogdown.author = "Magnus Tuvendal", 
        blogdown.ext=".md", 
        blogdown.subdir="post", 
        blogdown.yaml.empty=TRUE)
        

Har nu kommit fram till: https://notes.peter-baumgartner.net/tutorial/blogdown-tutorial-part-3/


### Titta på min site lokalt
Hmm - nu fungerar inte detta.
Jo - men var tvungen att göra en refresh.

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuYmxvZ2Rvd246OnNlcnZlX3NpdGUoKVxuXG5gYGAifQ== -->

```r
blogdown::serve_site()

```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiXHUwMDFiWz8yNWxCdWlsZGluZyBzaXRlcyDigKYgRVJST1IgMjAxOC8wMy8yMCAxMzozMTowNSBlcnJvciBwcm9jZXNzaW5nIHNob3J0Y29kZSBcIl9pbnRlcm5hbC9zaG9ydGNvZGVzL3JlZi5odG1sXCIgZm9yIHBhZ2UgXCJwb3N0L2dldHRpbmctc3RhcnRlZC5tZFwiOiB0ZW1wbGF0ZTogX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWw6MTo3MzogZXhlY3V0aW5nIFwiX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWxcIiBhdCA8cmVmIC5QYWdlICguR2V0IDApPjogZXJyb3IgY2FsbGluZyByZWY6IE5vIHBhZ2UgZm91bmQgd2l0aCBwYXRoIG9yIGxvZ2ljYWwgbmFtZSBcInBvc3Qvd2lkZ2V0cy5tZFwiLlxuRVJST1IgMjAxOC8wMy8yMCAxMzozMTowNSBlcnJvciBwcm9jZXNzaW5nIHNob3J0Y29kZSBcIl9pbnRlcm5hbC9zaG9ydGNvZGVzL3JlZi5odG1sXCIgZm9yIHBhZ2UgXCJwb3N0L2dldHRpbmctc3RhcnRlZC5tZFwiOiB0ZW1wbGF0ZTogX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWw6MTo3MzogZXhlY3V0aW5nIFwiX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWxcIiBhdCA8cmVmIC5QYWdlICguR2V0IDApPjogZXJyb3IgY2FsbGluZyByZWY6IE5vIHBhZ2UgZm91bmQgd2l0aCBwYXRoIG9yIGxvZ2ljYWwgbmFtZSBcInBvc3QvbWFuYWdpbmctY29udGVudC5tZFwiLlxuRVJST1IgMjAxOC8wMy8yMCAxMzozMTowNSBlcnJvciBwcm9jZXNzaW5nIHNob3J0Y29kZSBcIl9pbnRlcm5hbC9zaG9ydGNvZGVzL3JlZi5odG1sXCIgZm9yIHBhZ2UgXCJwb3N0L2dldHRpbmctc3RhcnRlZC5tZFwiOiB0ZW1wbGF0ZTogX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWw6MTo3MzogZXhlY3V0aW5nIFwiX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWxcIiBhdCA8cmVmIC5QYWdlICguR2V0IDApPjogZXJyb3IgY2FsbGluZyByZWY6IE5vIHBhZ2UgZm91bmQgd2l0aCBwYXRoIG9yIGxvZ2ljYWwgbmFtZSBcInBvc3QvbWFuYWdpbmctY29udGVudC5tZFwiLlxuRVJST1IgMjAxOC8wMy8yMCAxMzozMTowNSBlcnJvciBwcm9jZXNzaW5nIHNob3J0Y29kZSBcIl9pbnRlcm5hbC9zaG9ydGNvZGVzL3JlZi5odG1sXCIgZm9yIHBhZ2UgXCJwb3N0L2dldHRpbmctc3RhcnRlZC5tZFwiOiB0ZW1wbGF0ZTogX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWw6MTo3MzogZXhlY3V0aW5nIFwiX2ludGVybmFsL3Nob3J0Y29kZXMvcmVmLmh0bWxcIiBhdCA8cmVmIC5QYWdlICguR2V0IDApPjogZXJyb3IgY2FsbGluZyByZWY6IE5vIHBhZ2UgZm91bmQgd2l0aCBwYXRoIG9yIGxvZ2ljYWwgbmFtZSBcInBvc3Qvd3JpdGluZy1tYXJrZG93bi1sYXRleC5tZFwiLlxuXHUwMDFiWz8yNWhcblx1MDAxYltLXG4gICAgICAgICAgICAgICAgICAgfCBFTiAgXG4rLS0tLS0tLS0tLS0tLS0tLS0tKy0tLS0rXG4gIFBhZ2VzICAgICAgICAgICAgfCAyNSAgXG4gIFBhZ2luYXRvciBwYWdlcyAgfCAgMCAgXG4gIE5vbi1wYWdlIGZpbGVzICAgfCAgMCAgXG4gIFN0YXRpYyBmaWxlcyAgICAgfCAyMCAgXG4gIFByb2Nlc3NlZCBpbWFnZXMgfCAgMCAgXG4gIEFsaWFzZXMgICAgICAgICAgfCAgOCAgXG4gIFNpdGVtYXBzICAgICAgICAgfCAgMSAgXG4gIENsZWFuZWQgICAgICAgICAgfCAgMCAgXG5cblRvdGFsIGluIDkyIG1zXG4ifQ== -->

```
[?25lBuilding sites … ERROR 2018/03/20 13:31:05 error processing shortcode "_internal/shortcodes/ref.html" for page "post/getting-started.md": template: _internal/shortcodes/ref.html:1:73: executing "_internal/shortcodes/ref.html" at <ref .Page (.Get 0)>: error calling ref: No page found with path or logical name "post/widgets.md".
ERROR 2018/03/20 13:31:05 error processing shortcode "_internal/shortcodes/ref.html" for page "post/getting-started.md": template: _internal/shortcodes/ref.html:1:73: executing "_internal/shortcodes/ref.html" at <ref .Page (.Get 0)>: error calling ref: No page found with path or logical name "post/managing-content.md".
ERROR 2018/03/20 13:31:05 error processing shortcode "_internal/shortcodes/ref.html" for page "post/getting-started.md": template: _internal/shortcodes/ref.html:1:73: executing "_internal/shortcodes/ref.html" at <ref .Page (.Get 0)>: error calling ref: No page found with path or logical name "post/managing-content.md".
ERROR 2018/03/20 13:31:05 error processing shortcode "_internal/shortcodes/ref.html" for page "post/getting-started.md": template: _internal/shortcodes/ref.html:1:73: executing "_internal/shortcodes/ref.html" at <ref .Page (.Get 0)>: error calling ref: No page found with path or logical name "post/writing-markdown-latex.md".
[?25h
[K
                   | EN  
+------------------+----+
  Pages            | 25  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 20  
  Processed images |  0  
  Aliases          |  8  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 92 ms
```



<!-- rnb-output-end -->

<!-- rnb-output-begin eyJkYXRhIjoiU2VydmluZyB0aGUgZGlyZWN0b3J5IC9Vc2Vycy9tYWd0dXYvQ2xvdWRTdGF0aW9uL0NhbGx1bmFfY2xvdWRzdGF0aW9uL1IvQWNhZGVtaWNfYmxvZ2Rvd24gYXQgaHR0cDovLzEyNy4wLjAuMTo1Mzk0XG5UbyBzdG9wIHRoZSBzZXJ2ZXIsIHJ1biBzZXJ2cjo6ZGFlbW9uX3N0b3AoXCI0NTM5OTUxOTM2XCIpIG9yIHJlc3RhcnQgeW91ciBSIHNlc3Npb25cbiJ9 -->

```
Serving the directory /Users/magtuv/CloudStation/Calluna_cloudstation/R/Academic_blogdown at http://127.0.0.1:5394
To stop the server, run servr::daemon_stop("4539951936") or restart your R session
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## .gitignore
Öppnar .gitignore. Ligger bland mina filer. 
Ändrar denna och lägger till:
-  # ignore all files in the public/ directory
-  public/

Så nu borde allt i public inte läggas över på Github. Detta behövs inte eftersom Netlify skapar min site utifrån mina andra filer. Kan då ändra inkrementellt via github. Alternativet är att lokalt skapa en /public och dra den till en repository som visar en statisk site.

## Push to Github
- välj upp-pilen i git pane.
- Upptäcket att inget händer - blir inte uppdaterat på Github - OM jag inte också skriver in text i rutan Commit/Commit-message!

 
### Getting site from Github to Netlify

Viktigt att lägga in en version av Hugo. Görs som en variabel i Netlify.

OK - Netlify jobbar men siten blir inte publiserad.

Ändrar till HUGO 0.37.

# Site is live!

<!-- rnb-text-end -->

