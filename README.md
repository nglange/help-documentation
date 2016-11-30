# IBM Cloud Object Storage Help
This repo contains help documentation for users of IBM Managed Dedicated Cloud Object Storage.

Here are some **Style Conventions** for this Repository, if you are editing these documents:

 * Blue Box (2 words, Both Capitalized)
 * Box Panel (2 words, Both Capitalized)
 * SoftLayer (one word, CamelCase)
 * OpenStack (one word, CamelCase)
 * Vyatta (Capitalized)
 * Ursula (Capitalized)
 * Neutron, Nova, and so forth, all names of OpenStack projects (Capitalized)
 * GitHub (CamelCase)

Note that these conventions might not apply when these names are used in `code snippets`. Thus, any appearance of these terms that does not follow the conventions would only appear in `courier font`, easily identifiable as `code`.

Please avoid using abbreviations such as BP for Box Panel and SL for SoftLayer at any time.

**Format:**

We need to use "Markdown" format in the documentation. First, just be sure that every file you put into the repository has the extension .MD

See below for information on Markdown:

https://guides.github.com/features/mastering-markdown/

GitHub natively will display Markdown files as WYSIWYG, so you can check some of your formatting.

**Front Matter Required**

To make these articles display correctly, there needs to be a section of YML front matter at the beginning of each .MD file. We will do the conversion to publish on the Web using Jekyll.

NOTE with upgrade to Jekyll 3.0, fields are case-sensitive and must be lowercase or camelcase. The 'date' field has been changed to 'dateAdded' field.

**Fields are:**

layout : always set to Page. This tells Jekyll how to render the documentation HTML.

title : sets the header for the documentation page being written. Displayed in all Nav bars, searches, etc.

featured : If this is set to TRUE, the document is visible in the Nav bar. If FALSE, it is hidden under "view more" in the Nav.

weight : determines order in which items are displayed in the Nav. 1 = first. (NOT REQUIRED)

tags : displayed on documentation pages and the search page. Must be enclosed in brackets and comma-delimited [like, this].

dateAdded : Added to the header data next to the page author. No specific format required.

author : Added to the header data. No specific format required.

Also, there is special treatment required for highlighting code blocks so they will line-wrap correctly.

{% highlight bash %}

YOUR CODE BLOCK HERE

{% endhighlight %}

**Sample Document:**

Here is a template for the required YML headers:

https://github.ibm.com/BlueBoxDocs/IBM-Blue-Box-Docs/blob/master/SampleFile.md


**General Style Formatting Guidelines:**

For now, just use Markdown H1, H2, and so forth.

FIGURE CAPTIONS ARE 12 PT BOLD ALL CAPS

Please make figures no more than 6.5''wide if at all possible.

`Code snippets` should be formatted in `Courier, 12 pt`.

## Running Locally
  1. Clone the repo
  2. Check whether you have Ruby 2.0.0 or higher installed `ruby --version`
  3. Install Bundler `gem install bundler`
  4. Run locally with `bundle exec jekyll serve`

## Github Organization
1. [Basic Github folder Organization](#basic-github-folder-organization)
2. [Folders for Content](#folders-for-content)
3. [Folders for site structure, page layout and global styling](#folders-for-site-structure)


## Article Post
1. [Setting up an article](#setting-up-an-article)
2. [Code highlighting](#code-highlighting)
3. [Tag best practices](#tag-best-practices)


#### <a name="basic-github-folder-organization"></a>![github](/readme-img/github-org.png)

Most of the folders with underscores before the name (e.g. `_gettingstarted`) will appear at the top of the list of folders. These folders will contain the content that will appear on the site.

The folders without underscores (e.g. `css`) will contain code for the layout and style of the site.

#### <a name="folders-for-content"></a>Folders for Content

With the exception of `_sass`, `_layouts`, and `_includes`, all of the folders at the top of the list named `_categoryName` contain articles organized under these specific groupings. The content of these files can be edited. The changes will only affect the article associated with that file.  

![docs](/readme-img/github-org-underscore.png)

#### <a name="folders-for-site-structure"></a>Folders for site structure, page layout and global styling

With the exception of `_sass`, `_layouts`, and `_includes`, all of the folders with the naming convention `folderName` contain markup that affect the layout and styling either at a global level or article level. Approach adding or editing to the content of this folder with caution

![structure](/readme-img/github-org-structure.png)

#### <a name="setting-up-an-article"></a> ![article](/readme-img/article.png)

Articles require the follow content areas filled to maintain a consistent layout:  Layout, Title, Featured, Weight, Tags, DateAdded, Author, and Content.

##### Layout

This will always be set to page. This tells Jekyll how to render the documentation HTML.

##### Title

This will set the header for the documentation page being written. This will also be the title displayed in all nav bars, searches, etc..

##### Featured

If this is set to true, the document will be visible in the nav bar by default. If this is set to false, it will be hidden but can be navigated to by clicking ‘view more’ in the nav.

##### Weight

This determines the order of items displayed in the nav. 1 will be given highest priority, 2 second, and so on. Not required, but allows you to order the nav in a specific way. For instance, the most trafficked page on your site could be given a weight of 1 so that it appears first on the nav list.

##### Tags

These are displayed on both the documentation page as well as the search page. The tags must be enclosed in brackets [ ], and are comma delimited.

##### DateAdded

This data attribute is added to the header-data next to the page author. There is no specific format, as it will just take whatever you type here and add it to the post.

##### Author

This data attribute is also added to the header-data and, like the date, does not have any specific format.

#### <a name="code-highlighting"></a>![highlighting](/readme-img/highlighting.png)

Code Highlighting ( ``` ) via markdown is not rendering line breaks properly. To fix this, Jekyll has a built in code highlighter that wraps the code properly. To use this, encapsulate code snippets in the following format (specifying the language highlighting to use):

```
{% highlight bash %}
YOUR CODE HERE
{% endhighlight %}
```

#### <a name="tag-best-practices"></a>![tags](/readme-img/tags.png)

Tags are a core component of the search and browsing experience. It helps the search tool find articles as they are organized according to categories. It also is beneficial with helping the user understand the context how the articles are organized.

When creating a new article, include tags in this order [ category, subject, subject]. For example, if an article is to be organized under ‘Getting Started,’ then the order will be [ getting started, subject name, subject name ].



Contact llundquist@us.ibm.com with questions or concerns.
