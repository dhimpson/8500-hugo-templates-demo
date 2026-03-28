# Hugo Activity

* 1. In hugo.toml you will find code that creates navigation items. Add one for the people page you created on Monday. Add the code you used below.
```baseURL = 'https://example.org/'
languageCode = 'en-us'
title = "The Woman's Journal Digital Archive"

[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
  [[menu.main]]
    name = "Issues"
    url = "/issues/"
    weight = 2
  [[menu.main]]
    name = "Analysis"
    url = "/analysis/"
    weight = 3
  [[menu.main]]
    name = "About"
    url = "/about/"
    weight = 4
  [[menu.main]]
    name = "People"
    url = "/people/"
    weight = 5
 ```

* 2. Reorder Your Navigation Menu (2 points)In hugo.toml, menu items have a weight parameter that controls their order. Lower numbers appear first. Your task: Rearrange the menu so it displays in this order: Home, People, Issues, About, Analysis
```baseURL = 'https://example.org/'
languageCode = 'en-us'
title = "The Woman's Journal Digital Archive"

[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
  [[menu.main]]
    name = "Issues"
    url = "/issues/"
    weight = 3
  [[menu.main]]
    name = "Analysis"
    url = "/analysis/"
    weight = 5
  [[menu.main]]
    name = "About"
    url = "/about/"
    weight = 4
  [[menu.main]]
    name = "People"
    url = "/people/"
    weight = 2
```


* 3. On individual issue pages (single.html) add a "Back to all issues" button at the bottom so users can easily navigate back to the list of issues.
```<div>
  <a href="/issues/" class="btn btn-secondary">Back to All Issues</a>
  </div>
```

4. The homepage (layouts/index.html) stats bar currently uses a variable to count the number of issues and show that content dynamically.
```
<div class="stats-bar">
    {{ $issues := where .Site.RegularPages "Section" "issues" }}
    <div class="stat">
      <span class="stat-number">{{ len $issues }}</span>
      <span class="stat-label">Issues in Collection</span>
    </div>
    <div class="stat">
      <span class="stat-number">1870</span>
      <span class="stat-label">Year of Publication</span>
    </div>
    <div class="stat">
      <span class="stat-number">Vol. 1</span>
      <span class="stat-label">Volume Represented</span>
    </div>
    <div class="stat">
      <span class="stat-number">2</span>
      <span class="stat-label">Founding Editors</span>
    </div>
  </div>
</section>

```
First, look up .Site.RegularPages in the hugo documentation. Based on reading this documentation, what does ```{{ $issues := where .Site.RegularPages "Section" "issues" }}``` do?

Now, Edit this page so that the number of people are also dynamically generated. 


5. Reverse the order of the timeline list on layouts/issues/list.html. Right now it is in ascending order. How would you reverse that? 

6. Create a new piece of metadata on each issue that is called "editornotes:". Then add some content to each one (it can be lorem ipsum or some other fake text if you'd like). On the issue page, (layouts/issues/single.html) display these editor notes on the page. Style and format as you'd like.

7. What happens if one template doesn't have a field calle "editornotes"? Can you write a piece of code that shows that field only _if_ it appears in the metadata?

8. Just like we can call parameters that are stored in the metadata for a piece of content, we can also display pieces of info that are stored in the hugo.toml configuration file. Open hugo.toml and add this line anywhere after the title line:
```
tagline = "Voices of the American Women's Suffrage Movement"
```
Your hugo.toml should now include:
```
baseURL = 'https://example.org/'
languageCode = 'en-us'
title = "The Woman's Journal Digital Archive"
tagline = "Voices of the American Women's Suffrage Movement"
```
On the homepage template (layouts/index.html) find the hero section. Within the hero section add the tagline using this:
```{{ .Site.Params.tagline }}```. You will need to wrap it in html. 
