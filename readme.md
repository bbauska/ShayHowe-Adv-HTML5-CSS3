---
title: "Shay & Howe's Advanced HTML and CSS"
author: "Brian Bauska (bbauska)"
date last editted: "3/25/2024 5 +pm"
output: 
  markdown:
    with some style
---

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->

<h1 id="title"; style="align:center";>Advanced HTML &amp; CSS</h1>
<h6 id="author"; style="align:center";>by Shay-Howe</h6>

<h2>[Lesson 1] Performance & Organization</h2>

<h3>In this Lesson 1</h3>

<h5>HTML</h5>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#minify-compress-files">
    Minify & Compress Files</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#cache-common-files">
    Cache Common Files</a></li>
</ul>

<h5>CSS</h5>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#strategy-structure">
    Strategy &amp; Structure</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#performance-driven-selectors">
    Performance Driven Selectors</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#reusable-code">
    Reusable Code</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#reduce-http-requests">
    Reduce HTTP Requests</a></li>
</ul>

Having the ability to <a href="https://learn.shayhowe.com/html-css/writing-your-best-code/">
write HTML and CSS with a solid understanding is a great expertise to have. As a 
website's code base and traffic grows, a new skill set comes into play, one that is
extremely important to both development time and user experience. Knowing the fundamentals of
website <a href="http://developer.yahoo.com/performance/rules.html">performance</a> and
organization can go a long way.

The organization and architecture of a code base can greatly affect not
only the speed of development, but also the speed at which pages render.
Both of which can be sizeable concerns not only for developers but also
users. Taking the time to design the right structure for a code base,
and identify how all of the different components will work together, can
speed up production and make for a better experience all around.

Additionally, taking a few small steps to improve the performance of a
website can pay off in dividends. <a href="https://www.stevesouders.com/blog/2012/02/10/the-performance-golden-rule/">
Website performance</a> greatly resembles the 80/20 rule, where 20% of the optimizations will speed up
roughly 80% of the website.

<h4>Strategy & Structure</h4>

The first part to improving a website's performance and organization
revolves around identifying a good strategy and structure for developing
the code base. Specifically, building a strong directory architecture,
outlining design patterns, and finding ways to reuse common code.

<h4>Style Architecture</h4>

Exactly how to organize styles boils down to personal preference and
what is best for a given website but generally speaking there are best
practices to follow. One practice includes separating styles based on
intent, which includes creating directories for common base styles, user
interface components, and business logic modules.

```
 1   # Base
 2     -- normalize.css
 3     -- layout.css
 4     -- typography.css
 5  
 6   # Components
 7     -- alerts.css
 8     -- buttons.css
 9     -- forms.css
 10    -- list.css
 11    -- nav.css
 12    -- tables.css
 13  
 14  # Modules
 15    -- aside.css
 16    -- footer.css
 17    -- header.css
 18 
```

The architecture outlined above includes three directories, all with
individual groups of styles. The goal here is to <b>start thinking of
websites as systems</b> rather than individual pages, and the code
architecture should reflect this mindset. Notice how there aren't any
page specific styles here.

The base directory includes common styles and variables to be used
across the entire website, layout and typography styles for example.
The components directory includes styles for specific user interface
elements which are broken down into different component files such as
alerts and buttons. Lastly, the modules directory includes styles for
different sections of a page, which are determined by business needs.

The component styles are purely interface driven and have nothing to do
with the core business logic of the website. Modules then include styles
specific to the business logic. When marking up a module in HTML it is
common to use different user interface components within it. For
example, the sidebar of a page may have list and button styles that are
defined within component styles while other styles needed for the
sidebar are inherited from the module style. The separation of style
encourages well thought out presets and the ability for styles to be
widely shared and reused.

The strategy of organizing styles this way isn't exactly new, and has
been previously mentioned in different CSS methodologies including
Object Oriented CSS, OOCSS, and the Scalable and Modular Architecture
for CSS, SMACSS. These methodologies have their own opinions on
structure, as well as on how to use styles.

### Object Oriented CSS

The [[Object Oriented CSS]{.underline}](http://oocss.org/) methodology
was pioneered by Nicole Sullivan in her work with writing styles for
larger websites. Object Oriented CSS identifies two principles that will
help build scalable websites with a strong architecture and a reasonable
amount of code. These two principles include:

-   Separate structure from skin

-   Separate content from container

Overall <b>separating structure from skin</b> includes abstracting the
layout of an element away from the theme of a website. The structure of
a module should be transparent, allowing other styles to be inherited
and displayed without conflict. Most commonly this requires a solid grid
and layout structure, along with well crafted modules.

<b>Separating content from the container</b> involves removing the
dependency of a parent element nesting children elements. A heading
should look the same regardless of its parent container. To accomplish
this, elements need to inherit default styles, then be extended with
multiple classes as necessary.

<h5>HTML</h5>

```
 1  <div class="alert alert-error">
 2    <p class="msg">...</p>
 3  </div>
 4 
```

<h5>CSS</h5>

```
 1  .alert {...}
 2  .alert-error {...}
 3  .msg {...}
 4 
```

Object Oriented CSS advocates building a component library, staying
flexible, and utilizing a grid. These are good ground rules, and they
can help you avoid the need to add additional styles every time you add
a new page or feature to a website.

### Scalable & Modular Architecture for CSS

Along the same line of Object Oriented CSS is the [[Scalable and Modular
Architecture for CSS]{.underline}](http://smacss.com/) methodology
developed by Jonathan Snook. The Scalable and Modular Architecture for
CSS promotes breaking up styles into <b>five</b> core categories,
including:

-   Base

-   Layout

-   Module

-   State

-   Theme

The <b>base</b> category includes core element styles, covering the general
defaults. The <b>layout</b> category then identifies the sizing and grid
styles of different elements, determining their
layout. <b>Module</b> styles are more specific styles targeting individual
parts of the page, such as navigation or feature styles.
The <b>state</b> styles are then used to augment or override other styles
in the event that a module includes an alternate state, an active tab
for example. Lastly, the <b>theme</b> category may be added which could
include styles based around the skin, or look and feel, of different
modules.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;alert is-error&quot;&gt;                                     |
|   |                                                                      |
| 2 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 3 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .alert {&#8230;}                                                        |
|   |                                                                      |
| 2 | .alert.is-error {&#8230;}                                               |
|   |                                                                      |
| 3 | .alert p {&#8230;}                                                      |
|   |                                                                      |
| 4 | .alert.is-error p {&#8230;}                                             |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

In the example above the alert class falls into the module category
while the is-error class falls into the state category. Styles from each
of these categories are then inherited as necessary.

### Choosing a Methodology

Choosing which methodology to use, if any, is completely [[up to
you]{.underline}](http://viget.com/inspire/css-squareoff) and what you
feel is best for a given website. Generally speaking, a solid mix of
both OOCSS and SMACSS works well, borrowing principles from each
methodology as you prefer.

### Performance Driven Selectors

One functionality of CSS often abused without awareness
are [[selectors]{.underline}](http://csswizardry.com/2011/09/writing-efficient-css-selectors/).
Much of the attention within CSS is given to properties and values. So
long as these styles are applied to the correct element, everything
looks to be fine. This is a very poor assumption. How elements are
selected within CSS affects performance, including how fast a page
renders as well as how practical and modular the styles are in the
overall site architecture.

### Keep Selectors Short

There are a handful of benefits to keeping CSS selectors as short as
possible. These include minimizing specificity, allowing for better
inheritance and portability, and improving efficiency. Long, over
qualified selectors reduce performance because they force the browser to
render each individual selector type from right to left. They also put a
burden on all other selectors to be more specific.

+---+----------------------------------------------------------------------+
| 1 | /&ast; Bad &ast;/                                                          |
|   |                                                                      |
| 2 | header nav ul li a {&#8230;}                                            |
|   |                                                                      |
| 3 | /&ast; Good &ast;/                                                         |
|   |                                                                      |
| 4 | .primary-link {&#8230;}                                                 |
|   |                                                                      |
| 5 | /&ast; Bad &ast;/                                                          |
|   |                                                                      |
| 6 | button strong span {&#8230;}                                            |
|   |                                                                      |
| 7 | button strong span .callout {&#8230;}                                   |
|   |                                                                      |
| 8 | /&ast; Good &ast;/                                                         |
|   |                                                                      |
| 9 | button span {&#8230;}                                                   |
|   |                                                                      |
| 1 | button .callout {&#8230;}                                               |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

In the code above, the first selector is extremely specific and could be
identified, and rendered, much quicker with the use of a class.
Additionally, using a class in this case greatly reduces the need to
identify an element's parent, allowing that elements location to change
over time without breaking any styles.

The second example includes selectors shorter than the first example but
it can be improved by providing the same level of specificity to each
selector. Avoid using overly specific selectors, in return they are less
likely to break should the order of elements change. Cutting out some of
the individual selector units, and giving all of the selectors the same
strength, allows them to better cooperate.

The overall goal with short selectors is to decrease specificity,
creating cleaner, more charitable code.

### Favor Classes

Classes are great, they render quickly, allow for styles to be reused,
and are already commonly used in building a website. When using classes
though, there are common practices to observe in order to see that they
are leveraged properly.

Since selectors are rendered from right to left it is important to keep
an eye on the <b>key selector</b>. The key selector is the selector unit at
the end, furthest to the right. The key selector is crucial as it
identifies the first element a browser is going to find. Having a poor
key selector can send the browser on a wild goose hunt. Don't be afraid
to use a class to be more unique simply for the benefit of performance.

Additionally, do not prefix class selectors with an element. Doing so
prohibits those styles from easily being applied to a different element
and increases the overall specificity of the selector.

+---+----------------------------------------------------------------------+
| 1 | /&ast; Bad &ast;/                                                          |
|   |                                                                      |
| 2 | #container header nav {&#8230;}                                         |
|   |                                                                      |
| 3 | /&ast; Good &ast;/                                                         |
|   |                                                                      |
| 4 | .primary-nav {&#8230;}                                                  |
|   |                                                                      |
| 5 | /&ast; Bad &ast;/                                                          |
|   |                                                                      |
| 6 | article.feat-post {&#8230;}                                             |
|   |                                                                      |
| 7 | /&ast; Good &ast;/                                                         |
|   |                                                                      |
| 8 | .feat-post {&#8230;}                                                    |
|   |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

It is also worth noting, stay away from ID selectors where possible as
they are overly specific and do not allow for any repetition. At the end
of the day using an ID isn't a whole lot different than
using !important.

### Reusable Code

One of the largest performance drawbacks comes with bloated file sizes
and unnecessary browser rendering. One quick way to help largely cut
down on CSS file sizes is to reuse styles as much as possible. Any
repeating styles or interface patterns should be combined, allowing code
to be shared. If two modules share a background, rounded corners, and a
box shadow there is no reason to explicitly state those same styles
twice. Instead they can be combined, within a single class, allowing the
styles to be written once and then shared.

Reusing code doesn't have to come at the cost of semantics either. One
technique would be to pair selectors together, separating them with a
comma, allowing the same styles to be inherited across two selectors.
Another approach, often seen within the OOCSS and SMACSS methodologies
previously mentioned, includes binding styles to one class, then using
multiple classes on the same element.

+---+----------------------------------------------------------------------+
| 1 | /&ast; Bad &ast;/                                                          |
|   |                                                                      |
| 2 | .news {                                                              |
|   |                                                                      |
| 3 | background: #eee;                                                    |
|   |                                                                      |
| 4 | border-radius: 5px;                                                  |
|   |                                                                      |
| 5 | box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .social {                                                            |
|   |                                                                      |
| 8 | background: #eee;                                                    |
|   |                                                                      |
| 9 | border-radius: 5px;                                                  |
|   |                                                                      |
| 1 | box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);                      |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 | /&ast; Good &ast;/                                                         |
|   |                                                                      |
| 1 | .news,                                                               |
| 2 |                                                                      |
|   | .social {                                                            |
| 1 |                                                                      |
| 3 | background: #eee;                                                    |
|   |                                                                      |
| 1 | border-radius: 5px;                                                  |
| 4 |                                                                      |
|   | box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);                      |
| 1 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 1 | /&ast; Even Better &ast;/                                                  |
| 6 |                                                                      |
|   | .modal {                                                             |
| 1 |                                                                      |
| 7 | background: #eee;                                                    |
|   |                                                                      |
| 1 | border-radius: 5px;                                                  |
| 8 |                                                                      |
|   | box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);                      |
| 1 |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 2 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Which approach you take doesn't make a huge difference, so long as code
is being shared and reused, and the overall file size is reduced.

### Minify & Compress Files

Simply removing duplicate and unnecessary code is the best way to cut
down on file size, however there are additional ways. One way
includes [[minifying]{.underline}](http://www.hanselman.com/blog/TheImportanceAndEaseOfMinifyingYourCSSAndJavaScriptAndOptimizingPNGsForYourBlogOrWebsite.aspx) and
compressing files, such as HTML, CSS, and JavaScript files.
Additionally, images may be compressed, removing any unnecessary
comments and color profiles.

### gzip Compression

One of the more popular types of file compression is called gzip. gzip
compression takes common files, including HTML, CSS, JavaScript, and so
forth, and identifies similar strings to compress down. The more
matching strings identified, the smaller the file can be compressed,
thus sending a smaller file from the server to the browser.

Setting up gzip is fairly painless, and the [[HTML5
Boilerplate]{.underline}](http://html5boilerplate.com/) team has done a
great job of getting this going. To gzip files an .htaccess file needs
to be added to the root directory of the web server, labeling the
specific files to be gzipped. The dot at the beginning of the file name
is correct, as the .htaccess file is a hidden file.

Within the HTML5 Boilerplate Apache Server Configs, they instruct which
files gzip compression should be applied to. Keep in mind, the code for
this compression should live within a .htaccess file in the root
directory of the web server. Additionally, it is worth noting
that .htaccess files only work on Apache web servers, which need to have
the following modules enabled.

-   mod_setenvif.c

-   mod_headers.c

-   mod_deflate.c

-   mod_filter.c

-   mod_expires.c

-   mod_rewrite.c

Generally speaking this isn't an issue, and some web servers may even
set up compression for you. After all, it is in the web server's best
interest to compress files too.

### Measuring Compression

Within the Google Chrome web browser the web inspector gives a plethora
of data around performance, particularly within the Network tab.
Additionally, there are a few websites that help identify if gzip
compression is enabled.

![gzip Overview Screenshot](./images/image001.png)

Fig. 1

The Network tab identifies each file loaded within the browser and
displays the file size and load time. Notice how gzipping has reduced
the file sizes by around 60%.

![gzip Detail Screenshot](./images/image002.png)

Fig. 1

Looking at a file specifically identifies what type of compression
encoding the browser supports. In this case gzip, deflate, and sdch are
all supported as noted within the request headers.

Looking at the response headers identifies that the file was sent using
the gzip compression encoding.

### Image Compression

Cutting down the size of a text file helps, but you get even better
results by compressing the file size of images. The total file size of
all the images across a website can quickly add up, and compressing
images will greatly help keep the file size under control.

Many people steer away from compressing images in fear that compression
involves reducing the quality of the image itself. For the most part
this is incorrect, and images can be compressed in a lossless fashion,
allowing unnecessary color profiles and comments to be removed from the
image without changing the quality of the image at all.

There are a handful of tools to help compress images, two of the best
are [[ImageOptim]{.underline}](http://imageoptim.com/) for Mac
and [[PNGGauntlet]{.underline}](http://pnggauntlet.com/) for Windows.
Both of these services compress the most commonly used image formats,
specifically JPG and PNG files.

### Image Compression Demo

### Uncompressed, 455kb

![Uncompressed Ocean Picture](./3-25-24/media/image003.jpeg){width="5.0in"
height="3.3360039370078742in"}

Compressed, 401kb

![Compressed Ocean Picture](./3-25-24/media/image004.jpeg){width="5.0in"
height="3.3360039370078742in"}

![ImageOptim Screenshot](./3-25-24/media/image005.png){width="3.0in"
height="0.9733398950131233in"}

Fig. 1

Using ImageOptim the above image was reduced over 14% without any
reduction or loss in quality.

It should also be noted, setting an image's dimensions in HTML by way of
the height and width attributes <b>does help</b> render the page quicker,
setting aside the appropriate space for the image. Understand, these
attributes are to only be used to identify the exact image dimensions
and not to shrink an image. Using a larger image, then scaling it down
with the height and width attributes is bad practice as it loads more
data than necessary.

+---+----------------------------------------------------------------------+
| 1 | &lt;img src=&quot;ocean.jpg&quot; height=&quot;440&quot; width=&quot;660&quot;                 |
|   | alt=&quot;Oceanview&quot;&gt;                                                  |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Reduce HTTP Requests

Next to file size, the number of HTTP requests a website makes is one of
the largest performance pitfalls. Each time a request is made to the
server the page load time increases. Some request have to finish before
others can start, and too many request can bloat the server.

### Combine Like Files

One way, and perhaps the easiest way, to reduce the number of HTTP
requests is to combine like files. Specifically, combine all of the CSS
files into one and all of the JavaScript files into one. Combining these
files then compressing them creates one, hopefully small, HTTP request.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Bad &#45;&#45;&gt;                                                     |
|   |                                                                      |
| 2 | &lt;link href=&quot;css/reset.css&quot; rel=&quot;stylesheet&quot;&gt;                   |
|   |                                                                      |
| 3 | &lt;link href=&quot;css/base.css&quot; rel=&quot;stylesheet&quot;&gt;                    |
|   |                                                                      |
| 4 | &lt;link href=&quot;css/site.css&quot; rel=&quot;stylesheet&quot;&gt;                    |
|   |                                                                      |
| 5 | &lt;!&#45;&#45; Good &#45;&#45;&gt;                                                    |
|   |                                                                      |
| 6 | &lt;link href=&quot;css/styles.css&quot; rel=&quot;stylesheet&quot;&gt;                  |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

In general, the CSS for a web page should be loaded at
the <b>beginning</b> of the document within the head, while the JavaScript
for a web page should be loaded at the <b>end</b>, just before the
closing body tag. The reason for these unique placements is because CSS
can be loaded while the rest of the website is being loaded as well.
JavaScript, on the other hand, can only render one file at a time, thus
prohibiting anything else from loading. One caveat here is when
JavaScript files are asynchronously loaded after the page itself is done
rendering. Another caveat is when JavaScript is needed in helping render
the page, as such the case with the HTML5 shiv.

### Image Sprites

The practice of *spriting* images within CSS includes using one
background image across multiple elements. The goal here is to cut down
the number of HTTP requests made by using multiple background images.

To create a sprite take a handful of background images, ones that are
commonly used, and arrange them into one single image. Then using CSS
add the sprite as a background image to an element, and use
the background-position property to display the correct background
image.

Think of the background image sliding around behind elements, only to
expose the proper background image on a given element. For example, if
an element is 16 pixels wide by 16 pixels tall it can only expose a
background image of 16 pixels by 16 pixels, with the rest of the
background image being hidden.

![Menu Sprite](./3-25-24/media/image006.png){width="3.0in"
height="0.310087489063867in"}

Fig. 1

Here is a sprite for a text editor menu, outlined with guides for
reference of how the images background position will change.

Using the image sprite above, a menu can be created by using the image
sprite as a background on the span element. Then, using classes to
change the background position of the image sprite, different icons can
be shown accordingly.

<h5>HTML</h5>

```
+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;bold&quot;&gt;Bold                    |
|   | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 3 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;italic&quot;&gt;Italicize             |
| 4 | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
|   |                                                                      |
| 5 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;underline&quot;&gt;Underline          |
|   | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 6 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;size&quot;&gt;Size                    |
| 7 | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
|   |                                                                      |
| 8 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;bullet&quot;&gt;Bullet                |
|   | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 9 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;number&quot;&gt;Number                |
| 1 | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 0 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;quote&quot;&gt;Quote                  |
| 1 | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 1 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;left&quot;&gt;Left Align              |
| 1 | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 2 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;center&quot;&gt;Center Align          |
| 1 | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
| 3 |                                                                      |
|   | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;&lt;span class=&quot;right&quot;&gt;Right Align            |
|   | Text&lt;/span&gt;&lt;/a&gt;&lt;/li&gt;                                           |
|   |                                                                      |
|   | &lt;/ul&gt;                                                              |
``

<b>CSS</b>

```
| 1 | ul {                                                                 |
|   |                                                                      |
| 2 | margin: 0;                                                           |
|   |                                                                      |
| 3 | padding: 0;                                                          |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | li {                                                                 |
|   |                                                                      |
| 6 | float: left;                                                         |
|   |                                                                      |
| 7 | list-style: none;                                                    |
|   |                                                                      |
| 8 | margin: 2px;                                                         |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | li a {                                                               |
| 0 |                                                                      |
|   | background: linear-gradient(#fff, #eee);                             |
| 1 |                                                                      |
| 1 | border: 1px solid #ccc;                                              |
|   |                                                                      |
| 1 | border-radius: 3px;                                                  |
| 2 |                                                                      |
|   | display: block;                                                      |
| 1 |                                                                      |
| 3 | padding: 3px;                                                        |
|   |                                                                      |
| 1 | }                                                                    |
| 4 |                                                                      |
|   | li a:hover {                                                         |
| 1 |                                                                      |
| 5 | border-color: #999;                                                  |
|   |                                                                      |
| 1 | }                                                                    |
| 6 |                                                                      |
|   | li span {                                                            |
| 1 |                                                                      |
| 7 | background: url(&quot;sprite.png&quot;) 0 0 no-repeat;                       |
|   |                                                                      |
| 1 | color: transparent;                                                  |
| 8 |                                                                      |
|   | display: block;                                                      |
| 1 |                                                                      |
| 9 | font: 0/0 a;                                                         |
|   |                                                                      |
| 2 | height: 16px;                                                        |
| 0 |                                                                      |
|   | width: 16px;                                                         |
| 2 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 2 | .italic {                                                            |
| 2 |                                                                      |
|   | background-position: -16px 0;                                        |
| 2 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 2 | .underline {                                                         |
| 4 |                                                                      |
|   | background-position: -32px 0;                                        |
| 2 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 2 | .size {                                                              |
| 6 |                                                                      |
|   | background-position: -48px 0;                                        |
| 2 |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 2 | .bullet {                                                            |
| 8 |                                                                      |
|   | background-position: -64px 0;                                        |
| 2 |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 3 | .number {                                                            |
| 0 |                                                                      |
|   | background-position: -80px 0;                                        |
| 3 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 3 | .quote {                                                             |
| 2 |                                                                      |
|   | background-position: -96px 0;                                        |
| 3 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 3 | .left {                                                              |
| 4 |                                                                      |
|   | background-position: -112px 0;                                       |
| 3 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 3 | .center {                                                            |
| 6 |                                                                      |
|   | background-position: -128px 0;                                       |
| 3 |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 3 | .right {                                                             |
| 8 |                                                                      |
|   | background-position: -144px 0;                                       |
| 3 |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 4 |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
| 5 |                                                                      |
```

### Image Sprites Demo

### Image Data URI

Additionally, instead of spriting images, the encoded data for an image
can be included within HTML and CSS directly by way of the [[data
URI]{.underline}](https://css-tricks.com/data-uris/), removing the need
for a HTTP request all together. Using the image data URI works great
for small images, likely to never change, and where the HTML and CSS can
be heavily cached. There are, however, a couple of problems with data
URIs. They can be difficult to change and maintain, leading to having to
generate another encoding. And, they don't work in older browsers,
specifically Internet Explorer 7 and below.

If using data URIs helps cut down a few HTTP requests, and the HTML or
CSS can be heavily cached, the benefits tend to outweigh the risk. A few
tools to help generate data URIs
include [[converters]{.underline}](http://websemantics.co.uk/online_tools/image_to_data_uri_convertor/) and [[pattern
generators]{.underline}](http://www.patternify.com/). Be careful though,
and always double check to see that the actual data URI is less weight
than the actual image.

<h5>HTML</h5>

```
| 1 | &lt;img height=&quot;100&quot; width=&quot;660&quot; alt=&quot;Rigged Pattern&quot;            |
|   | src=&quot;data:image/png;base64,                                         |
| |                                                                      |
| 2 | iVBORw0KGg                                                           |
|    | oAAAANSUhEUgAAAAoAAAAICAYAAADA+m62AAAAPUlEQVQYV2NkQAO6m73+X/bdxoguji |
|   |                                                                      |
|   | IAU4RNMVwhuiQ6H6wQl3XI4oy4FMHcCJPHcDS6J2A2EqUQpJ                     |
|   |                                                                      |
|   | hohQAyIyYy0nBAGgAAAABJRU5ErkJggg==&quot;&gt;                               |
```

<h5>CSS</h5>

```
+---+----------------------------------------------------------------------+
| 1 | div {                                                                |
|   |                                                                      |
| 2 | background:                                                          |
|   | url(&quot;data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAI         |
| 3 |                                                                      |
|   | CAYAA                                                                |
| 4 | ADA+m62AAAAPUlEQVQYV2NkQAO6m73+X/bdxogujiIAU4RNMVwhuiQ6H6wQl3XI4oy4F |
|   |                                                                      |
|   | MHcCJPHcDS6J2A2EqUQpJhohQAyIyYy0nBAGgAAAABJRU5ErkJggg==&quot;) repeat;   |
|   |                                                                      |
|   | }                                                                    |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Image Data URI Demo

### Cache Common Files

Another way to help cut down HTTP requests, and to serve up pages
faster, is to cache common files. When a page loads for the first time
specific files may then be cached. Now the browser doesn't have to
request the same files again on repeating visits for quite some time.
How long a period of time is up to you, all depending on how long you
would like users to hold on to specific file types.

As with gzipping files, setting the expires headers for caching files
can be set within the .htaccess file. And again, the HTML5 Boilerplate
team is one step ahead of us. In their Apache Server Configs there is a
file specifically for setting up expires headers.

Images, videos, web fonts, and common media types are often cached for a
month, while CSS and JavaScript files are often cached for a year.
Should the CSS, or any other file, change more often than once each year
the file name will need to be changed, preferably versioned, in order to
be loaded. Alternatively, the expires headers can be changed to a
smaller period of time.

+---+----------------------------------------------------------------------+
| 1 | ExpiresByType text/css &quot;access plus 1 year&quot;                        |
|   |                                                                      |
| 2 | ExpiresByType application/javascript &quot;access plus 1 year&quot;          |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Changing the &quot;access plus 1 year&quot; value to &quot;access plus 1 week&quot; is
better suited for CSS and JavaScript files that are changing weekly but
are not version controlled with separate file names. For accepted
expires header values reference
the mod_expires [[syntax]{.underline}](http://httpd.apache.org/docs/current/mod/mod_expires.html).

### Resources & Links

-   [[Best Practices for Speeding Up Your Web
    Site]{.underline}](http://developer.yahoo.com/performance/rules.html) via
    Yahoo! Developer Network

-   [[Rules for Faster-Loading Web
    Sites]{.underline}](https://www.stevesouders.com/blog/2012/02/10/the-performance-golden-rule/) via
    Steve Sounders

-   [[CSS Strategy
    Square-off]{.underline}](http://viget.com/inspire/css-squareoff) via
    Viget Labs

-   [[Writing Efficient CSS
    Selectors]{.underline}](http://csswizardry.com/2011/09/writing-efficient-css-selectors/) via
    Harry Roberts

-   [[Minifying and Optimizing
    Files]{.underline}](http://www.hanselman.com/blog/TheImportanceAndEaseOfMinifyingYourCSSAndJavaScriptAndOptimizingPNGsForYourBlogOrWebsite.aspx) via
    Scott Hanselman

-   [[HTML5 Boilerplate]{.underline}](http://html5boilerplate.com/)

-   [[Data URIs]{.underline}](https://css-tricks.com/data-uris/) via
    CSS-Tricks

[<b>Lesson 1</b> [Performance &
Organization]{.underline}](https://learn.shayhowe.com/advanced-html-css/performance-organization/)
[<b>Lesson 3</b> [Complex
Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/)


[Lesson 2]{.mark} Detailed Positioning

In this Lesson 2

<b>CSS</b>

-   [[Containing
    Floats]{.underline}](https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/#containing-floats)

-   [[Position
    Property]{.underline}](https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/#position-property)

-   [[Z-Index
    Property]{.underline}](https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/#z-index-property)

<b>SHARE</b>

When it comes to building layouts and positioning content on a page
there are a handful of different techniques to use. Which technique to
use largely depends on the content and the goals of the page, as some
techniques may be better than others.

For example, the ability to float elements side by side provides a nice,
clean layout that is receptive to the different elements on a page.
However, when more strict control is needed, elements may be positioned
using other techniques, including relative or absolute positioning.

In this lesson, we'll start by taking a look at how to contain floats.
Following that, we'll cover more detailed positioning techniques,
including how to precisely position elements on both the x and y axis as
well as the z axis.

### Containing Floats

Floating elements is a natural process when building a website's layout,
and is the instinctive method for positioning elements on a page. Floats
allow elements to appear next to, or apart from, one another. They
provide the ability to build a natural flow within a layout and allow
elements to interact with one another based on their size and the size
of their containing parent.

When floated, an element's position is dependent on the other elements
positioned around it. Will that element run into the one next to it?
Will it appear on a new line? This all depends on the DOM (Document
Object Model) and what surrounds an element.

### What is the DOM?

The DOM, or Document Object Model, is an API for HTML and XML documents
which provides their structural representation. In our case, we are
speaking specifically to HTML documents, thus the DOM represents all of
the different elements and their relationship to each other.

The representation can be considered a tree of sorts, with each element
having a different relationship with those around it. Elements nested
inside others have a parent and child relationship while elements that
share the same parent have a sibling relationship.

While [[floats]{.underline}](https://css-tricks.com/all-about-floats/) do
provide quite a bit of fire power, they do come with a few of their own
problems. The most popular problem involves a parent element that
contains numerous floated elements. Content on the page will respect the
size and placement of the floated children element, but these floated
elements no longer impact the outer edges of the parent container. In
this event the parent element loses context of exactly what it contains
and collapses, thus giving the parent element a height of 0 and ignoring
various other properties. A lot of times this may go unnoticed,
specifically when the parent element doesn't have any styles tied to it
and the nested elements look to have aligned correctly.

Should the nested elements not line up correctly, styling errors may
appear. Taking a look at the demo below, the .box-set division should
have a light gray background, however the background is not seen as all
of the elements nested within it are floated. Upon inspecting
the .box-set division you will see it has a height of 0.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;box-set&quot;&gt;                                            |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box&quot;&gt;Box 1&lt;/figure&gt;                             |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box&quot;&gt;Box 2&lt;/figure&gt;                             |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box&quot;&gt;Box 3&lt;/figure&gt;                             |
|   |                                                                      |
| 5 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .box-set {                                                           |
|   |                                                                      |
| 2 | background: #eaeaed;                                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box {                                                               |
|   |                                                                      |
| 5 | background: #2db34a;                                                 |
|   |                                                                      |
| 6 | float: left;                                                         |
|   |                                                                      |
| 7 | margin: 1.858736059%;                                                |
|   |                                                                      |
| 8 | width: 29.615861214%;                                                |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Containing Floats Demo

One way to force containing these floats would be to place an empty
element just before the parent elements closing tag, of which would need
to include the style declaration clear: both;. Clearing the floats this
way works and is valid in most cases, but it isn't exactly semantic.
Depending on how many different floats need to be cleared on a page the
number of empty elements can begin to stack up quickly, while not
providing any real contextual value to the page.

Fortunately there are a couple of different techniques we can use to
contain these floats, the most popular of which include the overflow
technique and the clearfix technique.

### The Overflow Technique

One technique for containing floats within a parent element is to use
the CSS overflow property. Setting the overflow property value
to auto within the parent element will contain the floats, resulting in
an actual height for the parent element, thus including a gray
background in our example.

For this to work within Internet Explorer 6 a height or width is
required on the parent element. Since the height may likely be variable
a width of 100% will do the trick. Using overflow: auto; in Internet
Explorer on an Apple computer will also add scrollbars to the parent
element, in which it is better to use the overflow: hidden; declaration.

+---+----------------------------------------------------------------------+
| 1 | .box-set {                                                           |
|   |                                                                      |
| 2 | overflow: auto;                                                      |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Overflow Technique Demo

Using the overflow technique does come with a few drawbacks. For
example, when adding styles or moving nested elements that span outside
of the parent, like when trying to implement box shadows and dropdown
menus. In the demonstration below, you can see how the box shadow is
being cut off wherever it lies outside the parent element. Additionally,
the second box is cropped outside of the parent element.

Different browsers treat the overflow property differently, and thus
could also implement scrollbars in different fashions here too. Look at
the example below in different browsers, noticing how the columns
display differently in each browser.

### Overflow Pitfall Demo

### The Clearfix Technique

Depending on the context of the floated elements a better technique to
contain floats may be
the [[clearfix]{.underline}](http://nicolasgallagher.com/micro-clearfix-hack/) technique.
The clearfix technique is a bit more complex but does have better
support as compared to the overflow technique.

The clearfix technique is based off using
the :before and :after pseudo-elements on the parent element. Using
these pseudo-elements we can create hidden elements above and below the
parent containing the floats. The :before pseudo-element is used to
prevent the top margin of child elements from collapsing by creating an
anonymous table-cell element using the display: table; declaration. This
also helps ensure consistency within Internet Explorer 6 and 7.
The :after pseudo-element is used to prevent the bottom margin of child
elements from collapsing, as well as to clear the nested floats.

Adding the &ast;zoom property to the parent element triggers
the hasLayout mechanism specifically within Internet Explorer 6 and 7,
which determines how elements should draw and bound their content, as
well as how elements should interact with and relate to other elements.

Taking the same example from above you can see how the floats are
contained and the elements are able to live outside of the parent
element.

+---+----------------------------------------------------------------------+
| 1 | .box-set:before,                                                     |
|   |                                                                      |
| 2 | .box-set:after {                                                     |
|   |                                                                      |
| 3 | content: &quot;&quot;;                                                       |
|   |                                                                      |
| 4 | display: table;                                                      |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | .box-set:after {                                                     |
|   |                                                                      |
| 7 | clear: both;                                                         |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | .box-set {                                                           |
|   |                                                                      |
| 1 | &ast;zoom: 1;                                                           |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Clearfix Technique Demo

### Effectively Containing Floats

Which techniques to use boils down to the content at hand and your
personal preference. Some people prefer to stick strictly with the
clearfix technique as it is consistent across the board. Others feel the
clearfix technique is a bit too much code in some cases and prefer a mix
of techniques based on the content. What you decide to use is up to you,
just make sure it is well documented and easily identifiable either way.

One common practice is to assign a class to the parent element which
includes the floats needing to be contained. Using the clearfix
technique for example, Dan Cederholm helped coin the class name group.
The group class name can then be applied to any parent element needing
to contain floats.

+---+----------------------------------------------------------------------+
| 1 | .group:before,                                                       |
|   |                                                                      |
| 2 | .group:after {                                                       |
|   |                                                                      |
| 3 | content: &quot;&quot;;                                                       |
|   |                                                                      |
| 4 | display: table;                                                      |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | .group:after {                                                       |
|   |                                                                      |
| 7 | clear: both;                                                         |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | .group {                                                             |
|   |                                                                      |
| 1 | &ast;zoom: 1;                                                           |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Single Pseudo-Elements

It is worth noting only one :before and one :after pseudo-element are
allowed per element, for the time being. When trying to use the clearfix
technique with other :before and :after pseudo-element content you may
not achieve the desired outcome.

In the examples above, the clearfix styles would not live under
the box-set class. Instead, the class of group would need to be added to
the parent element containing the floats.

### Position Property

Occasionally you need more control over the position of an element, more
than a float can provide, in which case the position property comes into
play. The position property accepts five different values, each of which
provide different ways to [[uniquely
position]{.underline}](http://www.alistapart.com/articles/css-positioning-101/) an
element.

### Position Static

Elements by default have the position value of static, meaning they
don't have, nor will they accept, any specific [[box offset
properties]{.underline}](https://learn.shayhowe.com/html-css/opening-the-box-model/).
Furthermore, elements will be positioned as intended, with their default
behaviors.

In the demonstration below, all the boxes are stacked one on top of the
other as they are block level elements and are not floated in any
specific direction.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;box-set&quot;&gt;                                            |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box box-1&quot;&gt;Box 1&lt;/figure&gt;                       |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box box-2&quot;&gt;Box 2&lt;/figure&gt;                       |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box box-3&quot;&gt;Box 3&lt;/figure&gt;                       |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box box-4&quot;&gt;Box 4&lt;/figure&gt;                       |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .box-set {                                                           |
|   |                                                                      |
| 2 | background: #eaeaed;                                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box {                                                               |
|   |                                                                      |
| 5 | background: #2db34a;                                                 |
|   |                                                                      |
| 6 | height: 80px;                                                        |
|   |                                                                      |
| 7 | width: 80px;                                                         |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Position Static Demo

### Position Relative

The relative value for the position property is very similar to that of
the static value. The primary difference is that the relative value
accepts the box offset properties top, right, bottom, and left. These
box offset properties allow the element to be precisely positioned,
shifting the element from its default position in any direction.

### How Box Offset Properties Work

The box offset properties, top, right, bottom, and left, specify how
elements may be positioned, and in which direction. These offset
properties only work on elements with a relative, absolute,
or fixed positioning value.

For relatively positioned elements, these properties specify how an
element should be moved from its default position. For example, using
a top value of 20px on a relatively positioned element will push the
element 20 pixels down from where it was originally placed. Switching
the top value to -20px will instead pull the element 20 pixels up from
where it was originally placed.

For elements using absolute or fixed positioning these properties
specify the distance between the element and the edges of its parent
element. For example, using a top value of 20px on an absolutely
positioned element will push the element 20 pixels down from the top of
its relatively positioned parent. Switching the top value to -20px will
then pull the element 20 pixels up from the top of its relatively
positioned parent.

While the relative position does accept box offset properties the
element still remains in the normal, or static, flow of the page. In
this case other elements will not impede on where the relatively
positioned element was originally placed. Additionally, the relatively
positioned element may overlap, or underlap, other elements without
moving them from their default position.

In the demonstration below you will notice that the elements are still
stacked on top of one another, however they are shifted from their
default positions according to their individual box offset property
values. These values cause the boxes to overlap one another, yet do not
push each other in different directions. When an element is positioned
relatively the surrounding elements will observe the relatively
positioned elements default position.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;box-set&quot;&gt;                                            |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box box-1&quot;&gt;Box 1&lt;/figure&gt;                       |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box box-2&quot;&gt;Box 2&lt;/figure&gt;                       |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box box-3&quot;&gt;Box 3&lt;/figure&gt;                       |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box box-4&quot;&gt;Box 4&lt;/figure&gt;                       |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .box-set {                                                           |
|   |                                                                      |
| 2 | background: #eaeaed;                                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box {                                                               |
|   |                                                                      |
| 5 | background: #2db34a;                                                 |
|   |                                                                      |
| 6 | height: 80px;                                                        |
|   |                                                                      |
| 7 | position: relative;                                                  |
|   |                                                                      |
| 8 | width: 80px;                                                         |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | .box-1 {                                                             |
| 0 |                                                                      |
|   | top: 20px;                                                           |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 | .box-2 {                                                             |
| 2 |                                                                      |
|   | left: 40px;                                                          |
| 1 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 1 | .box-3 {                                                             |
| 4 |                                                                      |
|   | bottom: -10px;                                                       |
| 1 |                                                                      |
| 5 | right: 20px;                                                         |
|   |                                                                      |
| 1 | }                                                                    |
| 6 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Position Relative Demo

In the event that the top and bottom box offset properties are both
declared on a relatively positioned element, the top properties will
take priority. Additionally, if both the left and right box offset
properties are declared on a relatively positioned element, priority is
given in the direction in which the language of the page is written. For
example, in English pages the left offset property is given priority,
and for Arabic pages the right offset property is given priority.

### Position Absolute

Absolutely positioned elements accept box offset properties, however
they are removed from the normal flow of the document. Upon removing the
element from the normal flow, elements are positioned directly in
relation to their containing parent whom is relatively or absolutely
positioned. Should a relatively or absolutely positioned parent not be
present, the absolutely positioned element will be positioned in
relation to the body of the page.

Using absolutely positioned elements and specifying both vertical and
horizontal offset properties will move the element with those property
values in relation to its relatively positioned parent. For example, an
element with a top value of 50px and a right value of 100px will
position the element 50 pixels down from the top of its relatively
positioned parent and 100 pixels in from the right of its relatively
positioned parent.

Furthermore, using an absolutely positioned element and not specifying
any box offset property will position the element in the top left of its
closest relatively positioned parent. Setting one box offset property,
such as top, will absolutely position the element vertically but will
leave the horizontal positioning to the default value of flush left.

In the demonstration below you can see how each box is absolutely
positioned in relation to the parent division, of which is relatively
positioned. Each individual box is moved in from a specific side with a
positive value, or pulled out from a specific side with a negative
value.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;box-set&quot;&gt;                                            |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box box-1&quot;&gt;Box 1&lt;/figure&gt;                       |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box box-2&quot;&gt;Box 2&lt;/figure&gt;                       |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box box-3&quot;&gt;Box 3&lt;/figure&gt;                       |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box box-4&quot;&gt;Box 4&lt;/figure&gt;                       |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .box-set {                                                           |
|   |                                                                      |
| 2 | background: #eaeaed;                                                 |
|   |                                                                      |
| 3 | height: 200px;                                                       |
|   |                                                                      |
| 4 | position: relative;                                                  |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | .box {                                                               |
|   |                                                                      |
| 7 | background: #2db34a;                                                 |
|   |                                                                      |
| 8 | height: 80px;                                                        |
|   |                                                                      |
| 9 | position: absolute;                                                  |
|   |                                                                      |
| 1 | width: 80px;                                                         |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 1 | top: 6%;                                                             |
| 2 |                                                                      |
|   | left: 2%;                                                            |
| 1 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 1 | .box-2 {                                                             |
| 4 |                                                                      |
|   | top: 0;                                                              |
| 1 |                                                                      |
| 5 | right: -40px;                                                        |
|   |                                                                      |
| 1 | }                                                                    |
| 6 |                                                                      |
|   | .box-3 {                                                             |
| 1 |                                                                      |
| 7 | bottom: -10px;                                                       |
|   |                                                                      |
| 1 | right: 20px;                                                         |
| 8 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 9 | .box-4 {                                                             |
|   |                                                                      |
| 2 | bottom: 0;                                                           |
| 0 |                                                                      |
|   | }                                                                    |
| 2 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Position Absolute Demo

When an element has a fixed height and width and is absolutely
positioned, the top property takes priority should both
the top and bottom offset properties be declared. As with the relatively
positioned elements, should an element with a fixed width have both
the left and right box offset properties, priority is given to the
direction of which the language of the page is written.

If an element doesn't have a specific height or width and is absolutely
positioned, using a combination of the top and bottom box offset
properties displays an element with a height spanning the entire
specified size. Same goes for using both the left and right box offset
properties, resulting in an element with a full width based on both of
the left and right box offset properties. Using all four box offset
properties will display an element with a full specified height and
width.

### Position Fixed

Using the positioning value of fixed works just like that of absolute,
however the positioning is relative to the browser viewport, and it does
not scroll with the page. That said, elements will always be present no
matter where a user stands on a page. The only caveat
with fixed positioning is that it doesn't work with Internet Explorer 6.
Should you want to force fixed positioning within Internet Explorer 6
there are suitable hacks.

Using multiple box offset properties with fixed positioning will produce
the same behaviors as an absolutely positioned element.

Keeping the same box offset properties from the previous demonstration,
watch how the boxes are positioned in relation to the browser's viewport
and not the containing, relatively positioned parent.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;box-set&quot;&gt;                                            |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box box-1&quot;&gt;Box 1&lt;/figure&gt;                       |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box box-2&quot;&gt;Box 2&lt;/figure&gt;                       |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box box-3&quot;&gt;Box 3&lt;/figure&gt;                       |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box box-4&quot;&gt;Box 4&lt;/figure&gt;                       |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | height: 80px;                                                        |
|   |                                                                      |
| 4 | position: fixed;                                                     |
|   |                                                                      |
| 5 | width: 80px;                                                         |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box-1 {                                                             |
|   |                                                                      |
| 8 | top: 6%;                                                             |
|   |                                                                      |
| 9 | left: 2%;                                                            |
|   |                                                                      |
| 1 | }                                                                    |
| 0 |                                                                      |
|   | .box-2 {                                                             |
| 1 |                                                                      |
| 1 | top: 0;                                                              |
|   |                                                                      |
| 1 | right: -40px;                                                        |
| 2 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 3 | .box-3 {                                                             |
|   |                                                                      |
| 1 | bottom: -10px;                                                       |
| 4 |                                                                      |
|   | right: 20px;                                                         |
| 1 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 1 | .box-4 {                                                             |
| 6 |                                                                      |
|   | bottom: 0;                                                           |
| 1 |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Position Fixed Demo

### Fixed Header or Footer

One of the most common uses of fixed positioning is to build a fixed
header, or footer, anchored to one side of a page. As a user scrolls the
element stays prevalent, always within the viewport for users to
interact with.

The code and demonstration below outline how this may be achieved.
Notice how both left and right box offset properties are declared. This
allows the footer to span the entire width of the bottom of the page,
and it does so without disrupting the box model, allowing margins,
borders, and padding to be applied freely.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;footer&gt;Fixed Footer&lt;/footer&gt;                                    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | body {                                                               |
|   |                                                                      |
| 2 | background: #eaeaed;                                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | footer {                                                             |
|   |                                                                      |
| 5 | background: #2db34a;                                                 |
|   |                                                                      |
| 6 | bottom: 0;                                                           |
|   |                                                                      |
| 7 | left: 0;                                                             |
|   |                                                                      |
| 8 | position: fixed;                                                     |
|   |                                                                      |
| 9 | right: 0;                                                            |
|   |                                                                      |
| 1 | }                                                                    |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Fixed Footer Demo

### Z-Index Property

By nature web pages are often considered to be two dimensional,
displaying elements upon a x and y axis. However when you begin to
position elements they are occasionally placed on top of one another. To
change the order of [[how these elements are
stacked]{.underline}](http://www.impressivewebs.com/a-detailed-look-at-the-z-index-css-property/),
also known as the z-axis, the z-index property is to be used.

Generally, elements are positioned upon the z-axis as they appear within
the DOM. Elements coming at the top of the DOM are positioned behind
elements coming after them. Changing this stacking using
the z-index property is pretty straight forward. The element with the
highest z-index value will appear on the top regardless of its placement
in the DOM.

In order to apply the z-index property to an element, you must first
apply a position value of relative, absolute, or fixed. The same as if
you were to apply any box offset properties.

In the example below, without the z-index property each box will be
positioned precisely, starting with box two sitting on top of box one,
then box three sitting on top of box two, and so forth. Reordering the
stacking with the z-index property now positions box two on top of every
other box, followed by box three underneath it, and box four underneath
box three.

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;box-set&quot;&gt;                                            |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box box-1&quot;&gt;Box 1&lt;/figure&gt;                       |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box box-2&quot;&gt;Box 2&lt;/figure&gt;                       |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box box-3&quot;&gt;Box 3&lt;/figure&gt;                       |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box box-4&quot;&gt;Box 4&lt;/figure&gt;                       |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | .box-set {                                                           |
|   |                                                                      |
| 2 | background: #eaeaed;                                                 |
|   |                                                                      |
| 3 | height: 160px;                                                       |
|   |                                                                      |
| 4 | position: relative;                                                  |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | .box {                                                               |
|   |                                                                      |
| 7 | background: #2db34a;                                                 |
|   |                                                                      |
| 8 | border: 2px solid #ff7b29;                                           |
|   |                                                                      |
| 9 | position: absolute;                                                  |
|   |                                                                      |
| 1 | }                                                                    |
| 0 |                                                                      |
|   | .box-1 {                                                             |
| 1 |                                                                      |
| 1 | left: 10px;                                                          |
|   |                                                                      |
| 1 | top: 10px;                                                           |
| 2 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 3 | .box-2 {                                                             |
|   |                                                                      |
| 1 | bottom: 10px;                                                        |
| 4 |                                                                      |
|   | left: 70px;                                                          |
| 1 |                                                                      |
| 5 | z-index: 3;                                                          |
|   |                                                                      |
| 1 | }                                                                    |
| 6 |                                                                      |
|   | .box-3 {                                                             |
| 1 |                                                                      |
| 7 | left: 130px;                                                         |
|   |                                                                      |
| 1 | top: 10px;                                                           |
| 8 |                                                                      |
|   | z-index: 2;                                                          |
| 1 |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 2 | .box-4 {                                                             |
| 0 |                                                                      |
|   | bottom: 10px;                                                        |
| 2 |                                                                      |
| 1 | left: 190px;                                                         |
|   |                                                                      |
| 2 | z-index: 1;                                                          |
| 2 |                                                                      |
|   | }                                                                    |
| 2 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Z-Index Demo

### Resources & Links

<ul>
  <li><a href="https://css-tricks.com/all-about-floats/">All About Floats</a> via CSS-Tricks</li>
  <li><a href="http://nicolasgallagher.com/micro-clearfix-hack/">A New Micro Clearfix Hack</a> via Nicolas Gallagher</li>
  <li><a href="http://www.alistapart.com/articles/css-positioning-101/">CSS Positioning 101</a> via A List Apart</li>
  <li><a href="http://www.impressivewebs.com/a-detailed-look-at-the-z-index-css-property/">A Detailed Look at the z-index CSS Property</a> via
    Impressive Webs</li>
</ul>

<b>Lesson 1</b> [Performance & Organization](https://learn.shayhowe.com/advanced-html-css/performance-organization/)
<b>Lesson 3</b> [Complex Selectors](https://learn.shayhowe.com/advanced-html-css/complex-selectors/)

[Lesson 3] Complex Selectors

In this Lesson 3

<b>CSS</b>

-   [[Common
    Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/#common-selectors)

-   [[Child
    Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/#child-selectors)

-   [[Sibling
    Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/#sibling-selectors)

-   [[Attribute
    Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/#attribute-selectors)

-   [[Pseudo-classes]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/#pseudo-classes)

-   [[Pseudo-elements]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/#pseudo-elements)

<b>SHARE</b>

Selectors are one of, if not, the most important parts of CSS. They
shape the cascade and determine how styles are to be applied to elements
on a page.

Up until recently the focus of CSS never really touched on selectors.
Occasionally there would be incremental updates within the selectors
specification, but never any real ground breaking improvements.
Fortunately, more attention has been given to selectors as of late,
taking a look at how to select different types of elements and elements
in different states of use.

CSS3 brought new selectors, opening a whole new world of opportunities
and improvements to existing practices. Here we'll
discuss [[selectors]{.underline}](http://net.tutsplus.com/tutorials/html-css-techniques/the-30-css-selectors-you-must-memorize/),
old and new, and how to best put them to use.

### Common Selectors

Before diving too deep into some of the more complex selectors, and
those offered within CSS3, let's take a quick look at some of the more
common selectors seen today. These selectors include the type, class,
and ID selectors.

The <b>type</b> selector identifies an element based on its type,
specifically how that element is declared within HTML.
The <b>class</b> selector identifies an element based on its class
attribute value, which may be reused on multiple elements as necessary
to help share popular styles. Lastly, the <b>ID</b> selector identifies an
element based on its ID attribute value, which is unique and should only
be used once per page.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | h1 {&#8230;}                                                            |
|   |                                                                      |
| 2 | .tagline {&#8230;}                                                      |
|   |                                                                      |
| 3 | #intro {&#8230;}                                                        |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;section id=&quot;intro&quot;&gt;                                             |
|   |                                                                      |
| 2 | &lt;h1&gt;&#8230;&lt;/h1&gt;                                                    |
|   |                                                                      |
| 3 | &lt;h2 class=&quot;tagline&quot;&gt;&#8230;&lt;/h2&gt;                                  |
|   |                                                                      |
| 4 | &lt;/section&gt;                                                         |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Common Selectors Overview

  ----------------------------------------------------------------------------------------------------------
  <b>[Example]{.mark}</b>   <b>[Classification]{.mark}</b>   <b>[Explanation]{.mark}</b>
  ---------------------- ----------------------------- -----------------------------------------------------
  h1                     Type Selector                 Selects an element by its type

  .tagline               Class Selector                Selects an element by the class attribute value,
                                                       which may be reused multiple times per page

  #intro                 ID Selector                   Selects an element by the ID attribute value, which
                                                       is unique and to only be used once per page
  ----------------------------------------------------------------------------------------------------------

### Child Selectors

Child selectors provide a way to select elements that fall within one
another, thus making them children of their parent element. These
selections can be made two different ways, using either descendant or
direct child selectors.

### Descendant Selector

The most common child selector is the descendant selector, which matches
every element that follows an identified ancestor. The descendant
element does not have to come directly after the ancestor element inside
the document tree, such as a parent-child relationship, but may fall
anywhere within the ancestor element. Descendant selectors are created
by spacing apart elements within a selector, creating a new level of
hierarchy for each element list.

The article h2 selector is a descendant selector, only
selecting h2 elements that fall inside of an article element. Notice, no
matter where a h2 element lives, so long as it is within
the article element, it will always be selected. Additionally,
any h2 element outside of the article element is not selected.

Below, the headings on lines 3 and 5 are selected.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | article h2 {&#8230;}                                                    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;h2&gt;&#8230;&lt;/h2&gt;                                                    |
|   |                                                                      |
| 2 | &lt;article&gt;                                                          |
|   |                                                                      |
| 3 | &lt;h2&gt;This heading will be selected&lt;/h2&gt;                           |
|   |                                                                      |
| 4 | &lt;div&gt;                                                              |
|   |                                                                      |
| 5 | &lt;h2&gt;This heading will be selected&lt;/h2&gt;                           |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 | &lt;/article&gt;                                                         |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Direct Child Selector

Sometimes descendant selectors go a bit overboard, selecting more than
hoped. At times only the direct children of a parent element need to be
selected, not every instance of the element nested deeply inside of an
ancestor. In this event the direct child selector may be used by placing
a greater than sign, &gt;, between the parent element and child element
within the selector.

For example, article &gt; p is a direct child selector only
identifying p elements that fall directly within an article element.
Any p element placed outside of an article element, or nested inside of
another element other than the article element, will not be selected.

Below, the paragraph on line 3 is the only direct child of its parent
article, thus selected.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | article &gt; p {&#8230;}                                                  |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 2 | &lt;article&gt;                                                          |
|   |                                                                      |
| 3 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 4 | &lt;div&gt;                                                              |
|   |                                                                      |
| 5 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 | &lt;/article&gt;                                                         |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Child Selectors Overview

  -----------------------------------------------------------------------------------------------
  <b>[Example]{.mark}</b>   <b>[Classification]{.mark}</b>   <b>[Explanation]{.mark}</b>
  ---------------------- ----------------------------- ------------------------------------------
  article h2             Descendant Selector           Selects an element that resides anywhere
                                                       within an identified ancestor element

  article &gt; p           Direct Child Selector         Selects an element that resides
                                                       immediately inside an identified parent
                                                       element
  -----------------------------------------------------------------------------------------------

### Sibling Selectors

Knowing how to [[select
children]{.underline}](https://css-tricks.com/child-and-sibling-selectors/) of
an element is largely beneficial, and quite commonly seen. However
sibling elements, those elements that share a common parent, may also
need to be selected. These sibling selections can be made by way of the
general sibling and adjacent sibling selectors.

### General Sibling Selector

The general sibling selector allow elements to be selected based on
their sibling elements, those which share the same common parent. They
are created by using the tilde character, &tilde;, between two elements
within a selector. The first element identifies what the second element
shall be a sibling with, and both of which must share the same parent.

The h2 &tilde; p selector is a general sibling selector that looks
for p elements that follow, and share the same parent, of
any h2 elements. In order for a p element to be selected it must come
after any h2 element.

The paragraphs on lines 5 and 9 are selected as they come after the
heading within the document tree and share the same parent as their
sibling heading.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | h2 &tilde; p {&#8230;}                                                       |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 2 | &lt;section&gt;                                                          |
|   |                                                                      |
| 3 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 4 | &lt;h2&gt;&#8230;&lt;/h2&gt;                                                    |
|   |                                                                      |
| 5 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 6 | &lt;div&gt;                                                              |
|   |                                                                      |
| 7 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 8 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 9 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 1 | &lt;/section&gt;                                                         |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Adjacent Sibling Selector

Occasionally a little more control may be desired, including the ability
to select a sibling element that directly follows after another sibling
element, which is where the adjacent sibling element comes in. The
adjacent sibling selector will only select sibling elements directly
following after another sibling element. Instead of using the tilde
character, as with general sibling selectors, the adjacent sibling
selector uses a plus character, +, between the two elements within a
selector. Again, the first element identifies what the second element
shall directly follow after and be a sibling with, and both of which
must share the same parent.

Looking at the adjacent sibling selector h2 + p only p elements directly
following after h2 elements will be selected. Both of which must also
share the same parent element.

The paragraph on line 5 is selected as it directly follows after its
sibling heading along with sharing the same parent element, thus
selected.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | h2 + p {&#8230;}                                                        |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 2 | &lt;section&gt;                                                          |
|   |                                                                      |
| 3 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 4 | &lt;h2&gt;&#8230;&lt;/h2&gt;                                                    |
|   |                                                                      |
| 5 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 6 | &lt;div&gt;                                                              |
|   |                                                                      |
| 7 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 8 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 9 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 1 | &lt;/section&gt;                                                         |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Sibling Selectors Example

<b>HTML</b>

+---+-------------------------------------------------------------------+
| 1 | &lt;input type=&quot;checkbox&quot; id=&quot;toggle&quot;&gt;                         |
|   |                                                                   |
| 2 | &lt;label for=&quot;toggle&quot;&gt;&#9776;&lt;/label&gt;                         |
|   |                                                                   |
| 3 | &lt;nav&gt;                                                           |
|   |                                                                   |
| 4 | &lt;ul&gt;                                                            |
|   |                                                                   |
| 5 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Home&lt;/a&gt;&lt;/li&gt;                           |
|   |                                                                   |
| 6 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;About&lt;/a&gt;&lt;/li&gt;                          |
|   |                                                                   |
| 7 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Services&lt;/a&gt;&lt;/li&gt;                       |
|   |                                                                   |
| 8 | &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Contact&lt;/a&gt;&lt;/li&gt;                        |
|   |                                                                   |
| 9 | &lt;/ul&gt;                                                           |
|   |                                                                   |
| 1 | &lt;/nav&gt;                                                          |
| 0 |                                                                   |
|   |                                                                   |
| 1 |                                                                   |
| 1 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

<b>CSS</b>

+---+-------------------------------------------------------------------+
| 1 | input {                                                           |
|   |                                                                   |
| 2 | display: none;                                                    |
|   |                                                                   |
| 3 | }                                                                 |
|   |                                                                   |
| 4 | label,                                                            |
|   |                                                                   |
| 5 | ul {                                                              |
|   |                                                                   |
| 6 | border: 1px solid #cecfd5;                                        |
|   |                                                                   |
| 7 | border-radius: 6px;                                               |
|   |                                                                   |
| 8 | }                                                                 |
|   |                                                                   |
| 9 | label {                                                           |
|   |                                                                   |
| 1 | color: #0087cc;                                                   |
| 0 |                                                                   |
|   | cursor: pointer;                                                  |
| 1 |                                                                   |
| 1 | display: inline-block;                                            |
|   |                                                                   |
| 1 | font-size: 18px;                                                  |
| 2 |                                                                   |
|   | padding: 5px 9px;                                                 |
| 1 |                                                                   |
| 3 | transition: all .15s ease;                                        |
|   |                                                                   |
| 1 | }                                                                 |
| 4 |                                                                   |
|   | label:hover {                                                     |
| 1 |                                                                   |
| 5 | color: #ff7b29;                                                   |
|   |                                                                   |
| 1 | }                                                                 |
| 6 |                                                                   |
|   | input:checked + label {                                           |
| 1 |                                                                   |
| 7 | box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.15);                  |
|   |                                                                   |
| 1 | color: #9799a7;                                                   |
| 8 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 9 | nav {                                                             |
|   |                                                                   |
| 2 | max-height: 0;                                                    |
| 0 |                                                                   |
|   | overflow: hidden;                                                 |
| 2 |                                                                   |
| 1 | transition: all .15s ease;                                        |
|   |                                                                   |
| 2 | }                                                                 |
| 2 |                                                                   |
|   | input:checked &tilde; nav {                                            |
| 2 |                                                                   |
| 3 | max-height: 500px;                                                |
|   |                                                                   |
| 2 | }                                                                 |
| 4 |                                                                   |
|   | ul {                                                              |
| 2 |                                                                   |
| 5 | list-style: none;                                                 |
|   |                                                                   |
| 2 | margin: 8px 0 0 0;                                                |
| 6 |                                                                   |
|   | padding: 0;                                                       |
| 2 |                                                                   |
| 7 | width: 100px;                                                     |
|   |                                                                   |
| 2 | }                                                                 |
| 8 |                                                                   |
|   | li {                                                              |
| 2 |                                                                   |
| 9 | border-bottom: 1px solid #cecfd5;                                 |
|   |                                                                   |
| 3 | }                                                                 |
| 0 |                                                                   |
|   | li:last-child {                                                   |
| 3 |                                                                   |
| 1 | border-bottom: 0;                                                 |
|   |                                                                   |
| 3 | }                                                                 |
| 2 |                                                                   |
|   | a {                                                               |
| 3 |                                                                   |
| 3 | color: #0087cc;                                                   |
|   |                                                                   |
| 3 | display: block;                                                   |
| 4 |                                                                   |
|   | padding: 6px 12px;                                                |
| 3 |                                                                   |
| 5 | text-decoration: none;                                            |
|   |                                                                   |
| 3 | }                                                                 |
| 6 |                                                                   |
|   | a:hover {                                                         |
| 3 |                                                                   |
| 7 | color: #ff7b29;                                                   |
|   |                                                                   |
| 3 | }                                                                 |
| 8 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 9 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 0 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 1 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 2 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 3 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 4 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 5 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 6 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 7 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 8 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 9 |                                                                   |
|   |                                                                   |
| 5 |                                                                   |
| 0 |                                                                   |
|   |                                                                   |
| 5 |                                                                   |
| 1 |                                                                   |
|   |                                                                   |
| 5 |                                                                   |
| 2 |                                                                   |
|   |                                                                   |
| 5 |                                                                   |
| 3 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

### Demo

### Sibling Selectors Overview

  ------------------------------------------------------------------------------------------------------
  <b>[Example]{.mark}</b>   <b>[Classification]{.mark}</b>   <b>[Explanation]{.mark}</b>
  ---------------------- ----------------------------- -------------------------------------------------
  h2 &tilde; p                General Sibling Selector      Selects an element that follows anywhere after
                                                       the prior element, in which both elements share
                                                       the same parent

  h2 + p                 Adjacent Sibling Selector     Selects an element that follows directly after
                                                       the prior element, in which both elements share
                                                       the same parent
  ------------------------------------------------------------------------------------------------------

### Attribute Selectors

Some of the common selectors looked at early may also be defined as
attribute selectors, in which an element is selected based upon its
class or ID value. These class and ID attribute selectors are widely
used and extremely powerful but only the beginning. Other [[attribute
selectors]{.underline}](http://www.css3.info/preview/attribute-selectors/) have
emerged over the years, specifically taking a large leap forward with
CSS3. Now elements can be selected based on whether an attribute is
present and what its value may contain.

### Attribute Present Selector

The first attribute selector identifies an element based on whether it
includes an attribute or not, regardless of any actual value. To select
an element based on if an attribute is present or not, include the
attribute name in square brackets, &lbrack;&rbrack;, within a selector. The square
brackets may or may not follow any qualifier such as an element type or
class, all depending on the level of specificity desired.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;target&rbrack; {&#8230;}                                                   |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;#&quot; target=&quot;&#0095;blank&quot;&gt;&#8230;&lt;/a&gt;                        |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Equals Selector

To identify an element with a specific, and exact matching, attribute
value the same selector from before may be used, however this time
inside of the square brackets following the attribute name, include the
desired matching value. Inside the square brackets should be the
attribute name followed by an equals sign, =, quotations, &quot;&quot;, and
inside of the quotations should be the desired matching attribute value.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;href=&quot;http://google.com/&quot;&rbrack; {&#8230;}                              |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;http://google.com/&quot;&gt;&#8230;&lt;/a&gt;                          |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Contains Selector

When looking to find an element based on part of an attribute value, but
not an exact match, the asterisk character, &ast;, may be used within the
square brackets of a selector. The asterisk should fall just after the
attribute name, directly before the equals sign. Doing so denotes that
the value to follow only needs to appear, or be contained, within the
attribute value.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;href&ast;=&quot;login&quot;&rbrack; {&#8230;}                                         |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;/login.php&quot;&gt;&#8230;&lt;/a&gt;                                  |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Begins With Selector

In addition to selecting an element based on if an attribute value
contains a stated value, it is also possible to select an element based
on what an attribute value begins with. Using a circumflex accent, &Hat;,
within the square brackets of a selector between the attribute name and
equals sign denotes that the attribute value should begin with the
stated value.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;href&Hat;=&quot;https://&quot;&rbrack; {&#8230;}                                      |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;https://chase.com/&quot;&gt;&#8230;&lt;/a&gt;                          |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Ends With Selector

Opposite of the begins with selector, there is also an ends with
attribute selector. Instead of using the circumflex accent, the ends
with attribute selector uses the dollar sign, &#36;, within the square
brackets of a selector between the attribute name and equals sign. Using
the dollar sign denotes that the attribute value needs to end with the
stated value.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;href&#36;=&quot;.pdf&quot;&rbrack; {&#8230;}                                          |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;/docs/menu.pdf&quot;&gt;&#8230;&lt;/a&gt;                              |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Spaced Selector

At times attribute values may be spaced apart, in which only one of the
words needs to be matched in order to make a selection. In this event
using the tilde character, &tilde;, within the square brackets of a selector
between the attribute name and equals sign denotes an attribute value
that should be whitespace-separated, with one word matching the exact
stated value.

<b>CSS</b>

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;rel&tilde;=&quot;tag&quot;&rbrack; {&#8230;}                                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>HTML</b>

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;#&quot; rel=&quot;tag nofollow&quot;&gt;&#8230;&lt;/a&gt;                      |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Hyphenated Selector

When an attribute value is hyphen-separated, rather than
whitespace-separated, the vertical line character, &#0124;, may be used
within the square brackets of a selector between the attribute name and
equals sign. The vertical line denotes that the attribute value may be
hyphen-separated however the hyphen-separated words must begin with the
stated value.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | a&lbrack;lang&#0124;=&quot;en&quot;&rbrack; {&#8230;}                                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;#&quot; lang=&quot;en-US&quot;&gt;&#8230;&lt;/a&gt;                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Selectors Example

**HTML**

+---+-------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                            |
|   |                                                                   |
| 2 | &lt;li&gt;&lt;a href=&quot;#.pdf&quot;&gt;PDF Document&lt;/a&gt;&lt;/li&gt;               |
|   |                                                                   |
| 3 | &lt;li&gt;&lt;a href=&quot;#.doc&quot;&gt;Word Document&lt;/a&gt;&lt;/li&gt;              |
|   |                                                                   |
| 4 | &lt;li&gt;&lt;a href=&quot;#.jpg&quot;&gt;Image File&lt;/a&gt;&lt;/li&gt;                 |
|   |                                                                   |
| 5 | &lt;li&gt;&lt;a href=&quot;#.mp3&quot;&gt;Audio File&lt;/a&gt;&lt;/li&gt;                 |
|   |                                                                   |
| 6 | &lt;li&gt;&lt;a href=&quot;#.mp4&quot;&gt;Video File&lt;/a&gt;&lt;/li&gt;                 |
|   |                                                                   |
| 7 | &lt;/ul&gt;                                                           |
|   |                                                                   |
| 8 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

**CSS**

+---+-------------------------------------------------------------------+
| 1 | ul {                                                              |
|   |                                                                   |
| 2 | list-style: none;                                                 |
|   |                                                                   |
| 3 | margin: 0;                                                        |
|   |                                                                   |
| 4 | padding: 0;                                                       |
|   |                                                                   |
| 5 | }                                                                 |
|   |                                                                   |
| 6 | a {                                                               |
|   |                                                                   |
| 7 | background-position: 0 50%;                                       |
|   |                                                                   |
| 8 | background-repeat: no-repeat;                                     |
|   |                                                                   |
| 9 | color: #0087cc;                                                   |
|   |                                                                   |
| 1 | padding-left: 22px;                                               |
| 0 |                                                                   |
|   | text-decoration: none;                                            |
| 1 |                                                                   |
| 1 | }                                                                 |
|   |                                                                   |
| 1 | a:hover {                                                         |
| 2 |                                                                   |
|   | color: #ff7b29;                                                   |
| 1 |                                                                   |
| 3 | }                                                                 |
|   |                                                                   |
| 1 | a&lbrack;href&#36;=&quot;.pdf&quot;&rbrack; {                                            |
| 4 |                                                                   |
|   | background-image: url(&quot;images/pdf.png&quot;);                        |
| 1 |                                                                   |
| 5 | }                                                                 |
|   |                                                                   |
| 1 | a&lbrack;href&#36;=&quot;.doc&quot;&rbrack; {                                            |
| 6 |                                                                   |
|   | background-image: url(&quot;images/doc.png&quot;);                        |
| 1 |                                                                   |
| 7 | }                                                                 |
|   |                                                                   |
| 1 | a&lbrack;href&#36;=&quot;.jpg&quot;&rbrack; {                                            |
| 8 |                                                                   |
|   | background-image: url(&quot;images/image.png&quot;);                      |
| 1 |                                                                   |
| 9 | }                                                                 |
|   |                                                                   |
| 2 | a&lbrack;href&#36;=&quot;.mp3&quot;&rbrack; {                                            |
| 0 |                                                                   |
|   | background-image: url(&quot;images/audio.png&quot;);                      |
| 2 |                                                                   |
| 1 | }                                                                 |
|   |                                                                   |
| 2 | a&lbrack;href&#36;=&quot;.mp4&quot;&rbrack; {                                            |
| 2 |                                                                   |
|   | background-image: url(&quot;images/video.png&quot;);                      |
| 2 |                                                                   |
| 3 | }                                                                 |
|   |                                                                   |
| 2 |                                                                   |
| 4 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 5 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 6 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 7 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 8 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 9 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 0 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 1 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

### Demo

### Attribute Selectors Overview

  ----------------------------------------------------------------------------------------------------
  **[Example]{.mark}**               **[Classification]{.mark}**   **[Explanation]{.mark}**
  ---------------------------------- ----------------------------- -----------------------------------
  a&lbrack;target&rbrack;                        Attribute Present Selector    Selects an element if the given
                                                                   attribute is present

  a&lbrack;href=&quot;http://google.com/&quot;&rbrack;   Attribute Equals Selector     Selects an element if the given
                                                                   attribute value exactly matches the
                                                                   value stated

  a&lbrack;href&ast;=&quot;login&quot;&rbrack;              Attribute Contains Selector   Selects an element if the given
                                                                   attribute value contains at least
                                                                   once instance of the value stated

  a&lbrack;href&Hat;=&quot;https://&quot;&rbrack;           Attribute Begins With         Selects an element if the given
                                     Selector                      attribute value begins with the
                                                                   value stated

  a&lbrack;href&#36;=&quot;.pdf&quot;&rbrack;               Attribute Ends With Selector  Selects an element if the given
                                                                   attribute value ends with the value
                                                                   stated

  a&lbrack;rel&tilde;=&quot;tag&quot;&rbrack;                 Attribute Spaced Selector     Selects an element if the given
                                                                   attribute value is
                                                                   whitespace-separated with one word
                                                                   being exactly as stated

  a&lbrack;lang&#0124;=&quot;en&quot;&rbrack;                 Attribute Hyphenated Selector Selects an element if the given
                                                                   attribute value is hyphen-separated
                                                                   and begins with the word stated
  ----------------------------------------------------------------------------------------------------

### Pseudo-classes

[[Pseudo-classes]{.underline}](http://coding.smashingmagazine.com/2011/03/30/how-to-use-css3-pseudo-classes/) are
similar to regular classes in HTML however they are not directly stated
within the markup, instead they are dynamically populated as a result of
users' actions or the document structure. The most common pseudo-class,
and one you've likely seen before, is :hover. Notice how this
pseudo-class begins with the colon character, :, as will all other
pseudo-classes.

### Link Pseudo-classes

Some of the more basic pseudo-classes include two revolving around links
specifically. The :link and :visited pseudo-classes define if a link has
or hasn't been visited. To style an anchor which has not been visited
the :link pseudo-class comes into play, where the :visited pseudo-class
styles links that a user has already visited based on their browsing
history.

+---+----------------------------------------------------------------------+
| 1 | a:link {&#8230;}                                                        |
|   |                                                                      |
| 2 | a:visited {&#8230;}                                                     |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### User Action Pseudo-classes

Based on a users' actions different pseudo-classes may be dynamically
applied to an element, of which include the :hover, :active,
and :focus pseudo-classes. The :hover pseudo-class is applied to an
element when a user moves their cursor over the element, most commonly
used with anchor elements. The :active pseudo-class is applied to an
element when a user engages an element, such as clicking on an element.
Lastly, the :focus pseudo-class is applied to an element when a user has
made an element the focus point of the page, often by using the keyboard
to tab from one element to another.

+---+----------------------------------------------------------------------+
| 1 | a:hover {&#8230;}                                                       |
|   |                                                                      |
| 2 | a:active {&#8230;}                                                      |
|   |                                                                      |
| 3 | a:focus {&#8230;}                                                       |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### User Interface State Pseudo-classes

As with the link pseudo-classes there are also some pseudo-classes
generated around the user interface state of elements, particularly
within form elements. These user interface element state pseudo-classes
include :enabled, :disabled, :checked, and :indeterminate.

The :enabled pseudo-class selects an input that is in the default state
of enabled and available for use, where the :disabled pseudo-class
selects an input that has the disabled attribute tied to it. Many
browsers by default will fade out disabled inputs to inform users that
the input is not available for interaction, however those styles may be
adjusted as wished with the :disabled pseudo-class.

+---+----------------------------------------------------------------------+
| 1 | input:enabled {&#8230;}                                                 |
|   |                                                                      |
| 2 | input:disabled {&#8230;}                                                |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

The last two user interface element state pseudo-classes
of :checked and :indeterminate revolve around checkbox and radio button
input elements. The :checked pseudo-class selects checkboxes or radio
buttons that are, as you may expect, checked. When a checkbox or radio
button has neither been selected nor unselected it lives in an
indeterminate state, from which the :indeterminate pseudo-class can be
used to target these elements.

+---+----------------------------------------------------------------------+
| 1 | input:checked {&#8230;}                                                 |
|   |                                                                      |
| 2 | input:indeterminate {&#8230;}                                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Structural & Position Pseudo-classes

A handful of pseudo-classes are structural and position based, in which
they are determined based off where elements reside in the document
tree. These structural and position based pseudo-classes come in a few
different shapes and sizes, each of which provides their own unique
function. Some pseudo-classes have been around longer than others,
however CSS3 brought way of an entire new set of pseudo-classes to
supplement the existing ones.

**:first-child, :last-child, & :only-child**

The first structural and position based pseudo-classes one is likely to
come across are the :first-child, :last-child,
and :only-child pseudo-classes. The :first-child pseudo-class will
select an element if it's the first child within its parent, while
the :last-child pseudo-class will select an element if it's the last
element within its parent. These pseudo-classes are perfect for
selecting the first or last items in a list and so forth. Additionally,
the :only-child will select an element if it is the only element within
a parent. Alternately, the :only-child pseudo-class could be written
as :first-child:last-child, however :only-child holds a lower
specificity.

Here the selector li:first-child identifies the first list item within a
list, while the selector li:last-child identifies the last list item
within a list, thus lines 2 and 10 are selected. The
selector div:only-child is looking for a division which is the single
child of a parent element, without any other other siblings. In this
case line 4 is selected as it is the only division within the specific
list item.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | li:first-child {&#8230;}                                                |
|   |                                                                      |
| 2 | li:last-child {&#8230;}                                                 |
|   |                                                                      |
| 3 | div:only-child {&#8230;}                                                |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 3 | &lt;li&gt;                                                               |
|   |                                                                      |
| 4 | &lt;div&gt;This div will be selected&lt;/div&gt;                             |
|   |                                                                      |
| 5 | &lt;/li&gt;                                                              |
|   |                                                                      |
| 6 | &lt;li&gt;                                                               |
|   |                                                                      |
| 7 | &lt;div&gt;&#8230;&lt;/div&gt;                                                  |
|   |                                                                      |
| 8 | &lt;div&gt;&#8230;&lt;/div&gt;                                                  |
|   |                                                                      |
| 9 | &lt;/li&gt;                                                              |
|   |                                                                      |
| 1 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
| 0 |                                                                      |
|   | &lt;/ul&gt;                                                              |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**:first-of-type, :last-of-type, & :only-of-type**

Finding the first, last, and only children of a parent is pretty
helpful, and often all that is needed. However sometimes you only want
to select the first, last, or only child of a specific type of element.
For example, should you only want to select the first or last paragraph
within an article, or perhaps the only image within an article.
Fortunately this is where the :first-of-type, :last-of-type,
and :only-of-type pseudo-selectors come into place.

The :first-of-type pseudo-class will select the first element of its
type within a parent, while the :last-of-type pseudo-class will select
the last element of its type within a parent.
The :only-of-type pseudo-class will select an element if it is the only
of its type within a parent.

In the example below
the p:first-of-type and p:last-of-type pseudo-classes select the first
and last paragraphs within the article respectively, regardless if they
are actually the first or last children within the article. Lines 3 and
6 are selected, reflecting these selectors.
The img:only-of-type selector identifies the image on line 5 as it is
the only image to appear within the article, thus also selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | p:first-of-type {&#8230;}                                               |
|   |                                                                      |
| 2 | p:last-of-type {&#8230;}                                                |
|   |                                                                      |
| 3 | img:only-of-type {&#8230;}                                              |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;article&gt;                                                          |
|   |                                                                      |
| 2 | &lt;h1&gt;&#8230;&lt;/h1&gt;                                                    |
|   |                                                                      |
| 3 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 4 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 5 | &lt;img src=&quot;#&quot;&gt;&lt;!&#45;&#45; This image will be selected &#45;&#45;&gt;            |
|   |                                                                      |
| 6 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 7 | &lt;h6&gt;&#8230;&lt;/h6&gt;                                                    |
|   |                                                                      |
| 8 | &lt;/article&gt;                                                         |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Lastly there are a few structural and position based pseudo-classes that
select elements based on a number or an algebraic expression. These
pseudo-classes
include :nth-child(n), :nth-last-child(n), :nth-of-type(n),
and :nth-last-of-type(n). All of these unique pseudo-classes are
prefixed with nth and accept a number or expression inside of the
parenthesis, indicated by the character n argument.

The number or expression that falls within the parenthesis determines
exactly what element, or elements, are to be selected. Using a number
outright will count individual elements from the beginning or end of the
document tree and then select one element, while using an expression
will count numerous elements from the beginning or end of the document
tree and select them in groups or multiples.

### Using Pseudo-class Numbers & Expressions

As mentioned, using numbers outright within a pseudo-class will count
from the beginning, or end, of the document tree and select one element
accordingly. For example, the li:nth-child(4) selector will select the
fourth list item within a list. Counting begins with the first list item
and increases by one for each list item, until finally locating and
selecting the fourth item. When using a number outright it must be a
positive number.

[[Expressions for
pseudo-classes]{.underline}](http://reference.sitepoint.com/css/understandingnthchildexpressions) fall
in the format of *a*n, *a*n+*b*, *a*n-*b*, n+*b*, *-*n+*b*,
and *-a*n+*b*. The same expression may be translated and read
as (a×n)±b. The a variable stands for the multiplier in which elements
will be counted in while the b variable stands for where the counting
will begin or take place.

For example, the li:nth-child(3n) selector will identify every third
list item within a list. Using the expression this equates
to 3×0, 3×1, 3×2, and so forth. As you can see the results of this
expression lead to the third, sixth, and every element a multiple of
three being selected.

Additionally, the odd and even keyword values may be used. As expected,
these will select odd or even elements respectively. Should keyword
values not be appealing the expression of 2n+1 would select all odd
elements while the expression of 2n would select all even elements.

Using the li:nth-child(4n+7) selector will identify every fourth list
item starting with the seventh list item. Again, using the expression
this equates to (4×0)+7, (4×1)+7, (4×2)+7, and so forth. The results of
this expression leading to the seventh, eleventh, fifteenth, and every
element that is a multiple of four here on out being selected.

Using the n argument without being prefixed by a number results in
the a variable being interpreted as 1. With
the li:nth-child(n+5) selector every list item will be selected starting
with the fifth list item, leaving the first four list items unselected.
Within the expression this breaks down as (1×0)+5, (1×1)+5, (1×2)+5, and
so forth.

To make things a bit more complicated negative numbers may also be used.
For example, the li:nth-child(6n-4) selector will start counting every
sixth list item starting at negative four, selecting the second, eighth,
and fourteenth list items and so forth. The same
selector, li:nth-child(6n-4), could also be written
as li:nth-child(6n+2), without the use of a negative b variable.

A negative a variable, or a negative n argument, must be followed by a
positive b variable. When preceded by a negative a variable or
negative n argument the b variable identifies how high the counting will
reach. For example, the li:nth-child(-3n+12) selector will select every
third list item within the first twelve list items. The
selector li:nth-child(-n+9) will select the first nine list items within
a list, as the n argument, without any stated a variable, is defaulted
to -1.

### :nth-child(n) & :nth-last-child(n)

With a general understanding of how the pseudo-class numbers and
expressions work let's take a look at the actual pseudo-classes in which
these numbers and expressions may be used, the first of which being
the :nth-child(n) and :nth-last-child(n) pseudo-classes. These
pseudo-classes work a bit like
the :first-child and :last-child pseudo-classes in that they look, and
count, all of the elements within a parent and only select the element
specifically identified. The :nth-child(n) works from the beginning of
the document tree while the :nth-last-child(n) works from the end of the
document tree.

Using the :nth-child(n) pseudo-class, let's look at
the li:nth-child(3n) selector. The selector here will identify every
third list item, thus lines 4 and 7 are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | li:nth-child(3n) {&#8230;}                                              |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 3 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 4 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 5 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 6 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 7 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 8 | &lt;/ul&gt;                                                              |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Using a different expression within the :nth-child(n) pseudo-class will
yield a different selection. The li:nth-child(2n+3) selector, for
example, will identify every second list item starting with the third
and then onward. As a result, the list items lines 4 and 6 are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | li:nth-child(2n+3) {&#8230;}                                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 3 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 4 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 5 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 6 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 7 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 8 | &lt;/ul&gt;                                                              |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Changing the expression again, this time with a negative value, yields
new selection. Here the li:nth-child(-n+4) selector is identifying the
top four list items, leaving the rest of the list items unselected, thus
lines 2 through 5 are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | li:nth-child(-n+4) {&#8230;}                                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 3 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 4 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 5 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 6 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 7 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 8 | &lt;/ul&gt;                                                              |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Adding a negative integer before the n argument changes the selection
again. Here the li:nth-child(-2n+5) selector identifies every second
list item within the first five list items starting with the first list
item, thus the list items on lines 2, 4, and 6 are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | li:nth-child(-2n+5) {&#8230;}                                           |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 3 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 4 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 5 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 6 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 7 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 8 | &lt;/ul&gt;                                                              |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Changing from the :nth-child(n) pseudo-class to
the :nth-last-child(n) pseudo-class switches the direction of counting,
with counting starting from the end of the document tree using
the :nth-last-child(n) pseudo-class.
The li:nth-last-child(3n+2) selector, for example, will identify every
third list item starting from the second to last item in a list, moving
towards the beginning of the list. Here the list items on lines 3 and 6
are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | li:nth-last-child(3n+2) {&#8230;}                                       |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;ul&gt;                                                               |
|   |                                                                      |
| 2 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 3 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 4 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 5 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 6 | &lt;li&gt;This list item will be selected&lt;/li&gt;                         |
|   |                                                                      |
| 7 | &lt;li&gt;&#8230;&lt;/li&gt;                                                    |
|   |                                                                      |
| 8 | &lt;/ul&gt;                                                              |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### :nth-of-type(n) & :nth-last-of-type(n)

The :nth-of-type(n) and :nth-last-of-type(n) pseudo-classes are very
similar to that of
the :nth-child(n) and :nth-last-child(n) pseudo-classes, however instead
of counting every element within a parent
the :nth-of-type(n) and :nth-last-of-type(n) pseudo-classes only count
elements of their own type. For example, when counting paragraphs within
an article, the :nth-of-type(n) and :nth-last-of-type(n) pseudo-classes
will skip any headings, divisions, or miscellaneous elements that are
not paragraphs, while the :nth-child(n) and :nth-last-child(n) would
count every element, no matter its type, only selecting the ones that
match the element within the stated selector. Additionally, all of the
same expression possibilities used within
the :nth-child(n) and :nth-last-child(n) pseudo-classes are also
available within
the :nth-of-type(n) and :nth-last-of-type(n) pseudo-classes.

Using the :nth-of-type(n) pseudo-class within
the p:nth-of-type(3n) selector we are able to identify every third
paragraph within a parent, regardless of other sibling elements within
the parent. Here the paragraphs on lines 5 and 9 are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | p:nth-of-type(3n) {&#8230;}                                             |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;article&gt;                                                          |
|   |                                                                      |
| 2 | &lt;h1&gt;&#8230;&lt;/h1&gt;                                                    |
|   |                                                                      |
| 3 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 4 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 5 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 6 | &lt;h2&gt;&#8230;&lt;/h2&gt;                                                    |
|   |                                                                      |
| 7 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 8 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 9 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 1 | &lt;/article&gt;                                                         |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

As with the :nth-child(n) and :nth-last-child(n) pseudo-classes, the
primary difference between
the :nth-of-type(n) and :nth-last-of-type(n) pseudo-classes is that
the :nth-of-type(n) pseudo-class counts elements from the beginning of
the document tree and the :nth-last-of-type(n) pseudo-class counts
elements from the end of the document tree.

Using the :nth-last-of-type(n) pseudo-class we can write
the p:nth-last-of-type(2n+1) selector which identifies every second
paragraph from the end of a parent element starting with the last
paragraph. Here the paragraphs on lines 4, 7, and 9 are selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | p:nth-last-of-type(2n+1) {&#8230;}                                      |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;article&gt;                                                          |
|   |                                                                      |
| 2 | &lt;h1&gt;&#8230;&lt;/h1&gt;                                                    |
|   |                                                                      |
| 3 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 4 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 5 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 6 | &lt;h2&gt;&#8230;&lt;/h2&gt;                                                    |
|   |                                                                      |
| 7 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 8 | &lt;p&gt;&#8230;&lt;/p&gt;                                                      |
|   |                                                                      |
| 9 | &lt;p&gt;This paragraph will be selected&lt;/p&gt;                           |
|   |                                                                      |
| 1 | &lt;/article&gt;                                                         |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Target Pseudo-class

The :target pseudo-class is used to style elements when an element's ID
attribute value matches that of the URI fragment identifier. The
fragment identifier within a URI can be recognized by the hash
character, #, and what directly follows it. The
URL http://example.com/index.html#hello includes the fragment identifier
of hello. When this identifier matches the ID attribute value of an
element on the page, &lt;section id=&quot;hello&quot;&gt; for example, that element
may be identified and stylized using the :target pseudo-class. Fragment
identifiers are most commonly seen when using [[on page
links]{.underline}](https://learn.shayhowe.com/html-css/getting-to-know-html/#hyperlinks),
or linking to another part of the same page.

Looking at the code below, if a user would visit a page with the URI
fragment identifier of #hello, the section with that same ID attribute
value would be stylized accordingly using the :target pseudo-class. If
the URI fragment identifier changes, and matches the ID attribute value
of another section, that new section may be stylized using the same
selector and pseudo-class from before.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | section:target {&#8230;}                                                |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;section id=&quot;hello&quot;&gt;&#8230;&lt;/section&gt;                             |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Empty Pseudo-class

The :empty pseudo-class allows elements that do not contain children or
text nodes to be selected. Comments, processing instructions, and empty
text nodes are not considered children and are not treated as such.

Using the div:empty pseudo-class will identify divisions without any
children or text nodes. Below the divisions on lines 2 and 3 are
selected, as they are completely empty. Even though the second division
contains a comment, it is not considered to be a child, thus leaving the
division empty. The first division contains text, the fourth division
contains one blank text space, and the last division contains
a strong child element, thus they are all ruled out and are not
selected.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | div:empty {&#8230;}                                                     |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div&gt;Hello&lt;/div&gt;                                                 |
|   |                                                                      |
| 2 | &lt;div&gt;&lt;!&#45;&#45; Coming soon &#45;&#45;&gt;&lt;/div&gt;&lt;!&#45;&#45; This div will be       |
|   | selected &#45;&#45;&gt;                                                       |
| 3 |                                                                      |
|   | &lt;div&gt;&lt;/div&gt;&lt;!&#45;&#45; This div will be selected &#45;&#45;&gt;                |
| 4 |                                                                      |
|   | &lt;div&gt; &lt;/div&gt;                                                     |
| 5 |                                                                      |
|   | &lt;div&gt;&lt;strong&gt;&lt;/strong&gt;&lt;/div&gt;                                 |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Negation Pseudo-class

The negation pseudo-class, :not(x), is a pseudo-class that takes an
argument which is filtered out from the selection to be made.
The p:not(.intro) selector uses the negation pseudo-class to identify
every paragraph element without the class of intro. The paragraph
element is identified at the beginning of the selector followed by
the :not(x) pseudo-class. Inside of the parentheses falls the negation
selector, the class of .intro in this case.

Below, both the div:not(.awesome) and :not(div) selectors use
the :not(x) pseudo-class. The div:not(.awesome) selector identifies any
division without the class of awesome, while the :not(div) selector
identifies any element that isn't a division. As a result the, division
on line 1 is selected, as well as the two sections on lines 3 and 4,
thus they are marked bold. The only element not selected is the division
with the class of awesome, as it falls outside of the two negation
pseudo-classes.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | div:not(.awesome) {&#8230;}                                             |
|   |                                                                      |
| 2 | :not(div) {&#8230;}                                                     |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div&gt;This div will be selected&lt;/div&gt;                             |
|   |                                                                      |
| 2 | &lt;div class=&quot;awesome&quot;&gt;&#8230;&lt;/div&gt;                                |
|   |                                                                      |
| 3 | &lt;section&gt;This section will be selected&lt;/section&gt;                 |
|   |                                                                      |
| 4 | &lt;section class=&quot;awesome&quot;&gt;This section will be                    |
|   | selected&lt;/section&gt;                                                 |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Pseudo-classes Example

**HTML**

+---+-------------------------------------------------------------------+
| 1 | &lt;table&gt;                                                         |
|   |                                                                   |
| 2 | &lt;thead&gt;                                                         |
|   |                                                                   |
| 3 | &lt;tr&gt;                                                            |
|   |                                                                   |
| 4 | &lt;th&gt;Number&lt;/th&gt;                                               |
|   |                                                                   |
| 5 | &lt;th&gt;Player&lt;/th&gt;                                               |
|   |                                                                   |
| 6 | &lt;th&gt;Position&lt;/th&gt;                                             |
|   |                                                                   |
| 7 | &lt;th&gt;Height&lt;/th&gt;                                               |
|   |                                                                   |
| 8 | &lt;th&gt;Weight&lt;/th&gt;                                               |
|   |                                                                   |
| 9 | &lt;/tr&gt;                                                           |
|   |                                                                   |
| 1 | &lt;/thead&gt;                                                        |
| 0 |                                                                   |
|   | &lt;tbody&gt;                                                         |
| 1 |                                                                   |
| 1 | &lt;tr&gt;                                                            |
|   |                                                                   |
| 1 | &lt;td&gt;8&lt;/td&gt;                                                    |
| 2 |                                                                   |
|   | &lt;td&gt;Marco Belinelli&lt;/td&gt;                                      |
| 1 |                                                                   |
| 3 | &lt;td&gt;G&lt;/td&gt;                                                    |
|   |                                                                   |
| 1 | &lt;td&gt;6-5&lt;/td&gt;                                                  |
| 4 |                                                                   |
|   | &lt;td&gt;195&lt;/td&gt;                                                  |
| 1 |                                                                   |
| 5 | &lt;/tr&gt;                                                           |
|   |                                                                   |
| 1 | &lt;tr&gt;                                                            |
| 6 |                                                                   |
|   | &lt;td&gt;5&lt;/td&gt;                                                    |
| 1 |                                                                   |
| 7 | &lt;td&gt;Carlos Boozer&lt;/td&gt;                                        |
|   |                                                                   |
| 1 | &lt;td&gt;F&lt;/td&gt;                                                    |
| 8 |                                                                   |
|   | &lt;td&gt;6-9&lt;/td&gt;                                                  |
| 1 |                                                                   |
| 9 | &lt;td&gt;266&lt;/td&gt;                                                  |
|   |                                                                   |
| 2 | &lt;/tr&gt;                                                           |
| 0 |                                                                   |
|   | &#8230;                                                              |
| 2 |                                                                   |
| 1 | &lt;/tbody&gt;                                                        |
|   |                                                                   |
| 2 | &lt;/table&gt;                                                        |
| 2 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 3 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 4 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 5 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 6 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 7 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 8 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 9 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

**CSS**

+---+-------------------------------------------------------------------+
| 1 | table {                                                           |
|   |                                                                   |
| 2 | border-collapse: separate;                                        |
|   |                                                                   |
| 3 | border-spacing: 0;                                                |
|   |                                                                   |
| 4 | width: 100%;                                                      |
|   |                                                                   |
| 5 | }                                                                 |
|   |                                                                   |
| 6 | th,                                                               |
|   |                                                                   |
| 7 | td {                                                              |
|   |                                                                   |
| 8 | padding: 6px 15px;                                                |
|   |                                                                   |
| 9 | }                                                                 |
|   |                                                                   |
| 1 | th {                                                              |
| 0 |                                                                   |
|   | background: #42444e;                                              |
| 1 |                                                                   |
| 1 | color: #fff;                                                      |
|   |                                                                   |
| 1 | text-align: left;                                                 |
| 2 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 3 | tr:first-child th:first-child {                                   |
|   |                                                                   |
| 1 | border-top-left-radius: 6px;                                      |
| 4 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 5 | tr:first-child th:last-child {                                    |
|   |                                                                   |
| 1 | border-top-right-radius: 6px;                                     |
| 6 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 7 | td {                                                              |
|   |                                                                   |
| 1 | border-right: 1px solid #c6c9cc;                                  |
| 8 |                                                                   |
|   | border-bottom: 1px solid #c6c9cc;                                 |
| 1 |                                                                   |
| 9 | }                                                                 |
|   |                                                                   |
| 2 | td:first-child {                                                  |
| 0 |                                                                   |
|   | border-left: 1px solid #c6c9cc;                                   |
| 2 |                                                                   |
| 1 | }                                                                 |
|   |                                                                   |
| 2 | tr:nth-child(even) td {                                           |
| 2 |                                                                   |
|   | background: #eaeaed;                                              |
| 2 |                                                                   |
| 3 | }                                                                 |
|   |                                                                   |
| 2 | tr:last-child td:first-child {                                    |
| 4 |                                                                   |
|   | border-bottom-left-radius: 6px;                                   |
| 2 |                                                                   |
| 5 | }                                                                 |
|   |                                                                   |
| 2 | tr:last-child td:last-child {                                     |
| 6 |                                                                   |
|   | border-bottom-right-radius: 6px;                                  |
| 2 |                                                                   |
| 7 | }                                                                 |
|   |                                                                   |
| 2 |                                                                   |
| 8 |                                                                   |
|   |                                                                   |
| 2 |                                                                   |
| 9 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 0 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 1 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 2 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 3 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 4 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 5 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 6 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 7 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

### Demo

### Pseudo-classes Overview

  --------------------------------------------------------------------------------------------------
  **[Example]{.mark}**       **[Classification]{.mark}**   **[Explanation]{.mark}**
  -------------------------- ----------------------------- -----------------------------------------
  a:link                     Link Pseudo-class             Selects a link that has not been visited
                                                           by a user

  a:visited                  Link Pseudo-class             Selects a link that has been visited by a
                                                           user

  a:hover                    Action Pseudo-class           Selects an element when a user has
                                                           hovered their cursor over it

  a:active                   Action Pseudo-class           Selects an element when a user has
                                                           engaged it

  a:focus                    Action Pseudo-class           Selects an element when a user has made
                                                           it their focus point

  input:enabled              State Pseudo-class            Selects an element in the default enabled
                                                           state

  input:disabled             State Pseudo-class            Selects an element in the disabled state,
                                                           by way of the disabled attribute

  input:checked              State Pseudo-class            Selects a checkbox or radio button that
                                                           has been checked

  input:indeterminate        State Pseudo-class            Selects a checkbox or radio button that
                                                           neither been checked or unchecked,
                                                           leaving it in an indeterminate state

  li:first-child             Structural Pseudo-class       Selects an element that is the first
                                                           within a parent

  li:last-child              Structural Pseudo-class       Selects an element that is the last
                                                           within a parent

  div:only-child             Structural Pseudo-class       Selects an element that is the only
                                                           element within a parent

  p:first-of-type            Structural Pseudo-class       Selects an element that is the first of
                                                           its type within a parent

  p:last-of-type             Structural Pseudo-class       Selects an element that is the last of
                                                           its type within a parent

  img:only-of-type           Structural Pseudo-class       Selects an element that is the only of
                                                           its type within a parent

  li:nth-child(2n+3)         Structural Pseudo-class       Selects an element that matches the given
                                                           number or expression, counting all
                                                           elements from the beginning of the
                                                           document tree

  li:nth-last-child(3n+2)    Structural Pseudo-class       Selects an element that matches the given
                                                           number or expression, counting all
                                                           elements from the end of the document
                                                           tree

  p:nth-of-type(3n)          Structural Pseudo-class       Selects an element that matches the given
                                                           number or expression, counting only
                                                           elements of its type from the beginning
                                                           of the document tree

  p:nth-last-of-type(2n+1)   Structural Pseudo-class       Selects an element that matches the given
                                                           number or expression, counting only
                                                           elements of its type from the end of the
                                                           document tree

  section:target             Target Pseudo-class           Selects an element whose ID attribute
                                                           value matches that of the URI fragment
                                                           identifier

  div:empty                  Empty Pseudo-class            Selects an element that does not contain
                                                           any children or text nodes

  div:not(.awesome)          Negation Pseudo-class         Selects an element not represented by the
                                                           stated argument
  --------------------------------------------------------------------------------------------------

Pseudo-elements

Pseudo-elements are dynamic elements that don't exist in the document
tree, and when used within selectors
these [[pseudo-elements]{.underline}](http://coding.smashingmagazine.com/2009/08/17/taming-advanced-css-selectors/) allow
unique parts of the page to be stylized. One important point to note,
only one pseudo-element may be used within a selector at a given time.

Textual Pseudo-elements

The first pseudo-elements ever released were
the :first-letter and :first-line textual pseudo-elements.
The :first-letter pseudo-element will identify the first letter of text
within an element, while the :first-line pseudo-element will identify
the first line of text within an element.

In the demonstration below the first letter of the paragraph with the
class of alpha is set in a larger font size and colored orange, as is
the first line of the paragraph with the class of bravo. These
selections are made by use of the :first-letter and :first-line textual
pseudo-elements respectively.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .alpha:first-letter,                                                 |
|   |                                                                      |
| 2 | .bravo:first-line {                                                  |
|   |                                                                      |
| 3 | color: #ff7b29;                                                      |
|   |                                                                      |
| 4 | font-size: 18px;                                                     |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

HTML

+---+----------------------------------------------------------------------+
| 1 | &lt;p class=&quot;alpha&quot;&gt;Lorem ipsum dolor&#8230;&lt;/p&gt;                     |
|   |                                                                      |
| 2 | &lt;p class=&quot;bravo&quot;&gt;Integer eget enim&#8230;&lt;/p&gt;                     |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Textual Pseudo-elements Demo

### Generated Content Pseudo-elements

The :before and :after generated content pseudo-elements create new
inline level pseudo-elements just inside the selected element. Most
commonly these pseudo-elements are used in conjunction with
the content property to add insignificant information to a page, however
that is not always the case. Additional uses of these psuedo-elements
may be to add user interface components to the page without having to
clutter the document with unsemantic elements.

The :before pseudo-element creates a pseudo-element before, or in front
of, the selected element, while the :after pseudo-element creates a
pseudo-element after, or behind, the selected element. These
pseudo-elements appear nested within the selected element, not outside
of it. Below the :after pseudo-element is used to display
the href attribute value of anchor links within parentheses after the
actual links. The information here is helpful, but not ultimately
necessary should a browser not support these pseudo-elements.

**CSS**

+---+----------------------------------------------------------------------+
| 1 | a:after {                                                            |
|   |                                                                      |
| 2 | color: #9799a7;                                                      |
|   |                                                                      |
| 3 | content: &quot; (&quot; attr(href) &quot;)&quot;;                                    |
|   |                                                                      |
| 4 | font-size: 11px;                                                     |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;http://google.com/&quot;&gt;Search the Web&lt;/a&gt;                |
|   |                                                                      |
| 2 | &lt;a href=&quot;http://learn.shayhowe.com/&quot;&gt;Learn How to Build          |
|   | Websites&lt;/a&gt;                                                       |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Generated Content Pseudo-elements Demo

### Fragment Pseudo-element

The ::selection fragment pseudo-element identifies part of the document
that has been selected, or highlighted, by a user's actions. The
selection may then be stylized, however only using
the color, background, background-color, and text-shadow properties. It
is worth noting, the background-image property is ignore. While the
shorthand background property may be used to add a color, any images
will be ignored.

### Single Colon (:) versus Double Colons (::)

The fragment pseudo-element was added with CSS3 and in attempt to
differentiate pseudo-classes from pseudo-elements the double colons were
added to pseudo-elements. Fortunately most browsers will support both
values, single or double colons, for pseudo-elements however
the ::selection pseudo-element must always start with double colons.

When selecting any of the text within the demonstration below the
background will appear orange and any text shadows will be removed
thanks to the ::selection fragment pseudo-element. Also note,
the ::-moz-selection Mozilla prefixed fragment pseudo-element has been
added to ensure the best support for all browsers.

+---+----------------------------------------------------------------------+
| 1 | ::-moz-selection {                                                   |
|   |                                                                      |
| 2 | background: #ff7b29;                                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | ::selection {                                                        |
|   |                                                                      |
| 5 | background: #ff7b29;                                                 |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Fragment Pseudo-element Demo

### Pseudo-elements Example

### **HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;a class=&quot;arrow&quot; href=&quot;#&quot;&gt;Continue Reading&lt;/a&gt;             |
|   |                                                                    |
| 2 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

**CSS**

+---+-------------------------------------------------------------------+
| 1 | .arrow {                                                          |
|   |                                                                   |
| 2 | background: #2db34a;                                              |
|   |                                                                   |
| 3 | color: #fff;                                                      |
|   |                                                                   |
| 4 | display: inline-block;                                            |
|   |                                                                   |
| 5 | height: 30px;                                                     |
|   |                                                                   |
| 6 | line-height: 30px;                                                |
|   |                                                                   |
| 7 | padding: 0 12px;                                                  |
|   |                                                                   |
| 8 | position: relative;                                               |
|   |                                                                   |
| 9 | text-decoration: none;                                            |
|   |                                                                   |
| 1 | }                                                                 |
| 0 |                                                                   |
|   | .arrow:before,                                                    |
| 1 |                                                                   |
| 1 | .arrow:after {                                                    |
|   |                                                                   |
| 1 | content: &quot;&quot;;                                                    |
| 2 |                                                                   |
|   | height: 0;                                                        |
| 1 |                                                                   |
| 3 | position: absolute;                                               |
|   |                                                                   |
| 1 | width: 0;                                                         |
| 4 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 5 | .arrow:before {                                                   |
|   |                                                                   |
| 1 | border-bottom: 15px solid #2db34a;                                |
| 6 |                                                                   |
|   | border-left: 15px solid transparent;                              |
| 1 |                                                                   |
| 7 | border-top: 15px solid #2db34a;                                   |
|   |                                                                   |
| 1 | left: -15px;                                                      |
| 8 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 9 | .arrow:after {                                                    |
|   |                                                                   |
| 2 | border-bottom: 15px solid transparent;                            |
| 0 |                                                                   |
|   | border-left: 15px solid #2db34a;                                  |
| 2 |                                                                   |
| 1 | border-top: 15px solid transparent;                               |
|   |                                                                   |
| 2 | right: -15px;                                                     |
| 2 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 3 | .arrow:hover {                                                    |
|   |                                                                   |
| 2 | background: #ff7b29;                                              |
| 4 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 5 | .arrow:hover:before {                                             |
|   |                                                                   |
| 2 | border-bottom: 15px solid #ff7b29;                                |
| 6 |                                                                   |
|   | border-top: 15px solid #ff7b29;                                   |
| 2 |                                                                   |
| 7 | }                                                                 |
|   |                                                                   |
| 2 | .arrow:hover:after {                                              |
| 8 |                                                                   |
|   | border-left: 15px solid #ff7b29;                                  |
| 2 |                                                                   |
| 9 | }                                                                 |
|   |                                                                   |
| 3 |                                                                   |
| 0 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 1 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 2 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 3 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 4 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 5 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 6 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 7 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 8 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 9 |                                                                   |
|   |                                                                   |
| 4 |                                                                   |
| 0 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

### Demo

### Pseudo-elements Overview

  ------------------------------------------------------------------------------------------------
  **[Example]{.mark}**   **[Classification]{.mark}**   **[Explanation]{.mark}**
  ---------------------- ----------------------------- -------------------------------------------
  .alpha:first-letter    Textual Pseudo-elements       Selects the first letter of text within an
                                                       element

  .bravo:first-line      Textual Pseudo-elements       Selects the first line of text within an
                                                       element

  div:before             Generated Content             Creates a pseudo-element inside the
                                                       selected element at the beginning

  a:after                Generated Content             Creates a pseudo-element inside the
                                                       selected element at the end

  ::selection            Fragment Pseudo-element       Selects the part of a document which has
                                                       been selected, or highlighted, by a users'
                                                       actions
  ------------------------------------------------------------------------------------------------

### Selector Browser Support

While these selectors provide a variety of opportunity and the ability
to do some truly amazing things with CSS, they are at times plagued by
poor browser support. Before doing anything too critical check the
selectors you are wishing to use across your visitor's most common
browsers, and then make the judgment call as to whether they are
appropriate or not.

CSS3.info provides a [[CSS3 Selectors
Test]{.underline}](https://www.css3.info/selectors-test/) tool which
will inform you as to which selectors are supported by the browser in
use. It's also never a bad idea to check browser support directly from
the vendor.

Additionally, [[Selectivizr]{.underline}](http://selectivizr.com/), a
JavaScript utility, provides great support for these selectors in
Internet Explorer 6-8. More support, should it be necessary, can also be
provided by [[jQuery
selectors]{.underline}](http://api.jquery.com/category/selectors/).

### Selector Speed & Performance

It is important to pay attention the speed and performance of selectors,
as using too many intricate selectors can slow down the rendering of a
page. Be attentive and when a selector begins to look a bit foreign
think about revisiting it, and seeing if a better solution can be found.

### Resources & Links

-   [[The 30 CSS Selectors you Must
    Memorize]{.underline}](http://net.tutsplus.com/tutorials/html-css-techniques/the-30-css-selectors-you-must-memorize/) via
    Nettuts+

-   [[Child and Sibling
    Selectors]{.underline}](https://css-tricks.com/child-and-sibling-selectors/) via
    CSS-Tricks

-   [[CSS3 Substring Matching Attribute
    Selectors]{.underline}](http://www.css3.info/preview/attribute-selectors/) via
    CSS3.info

-   [[How To Use CSS3
    Pseudo-Classes]{.underline}](http://coding.smashingmagazine.com/2011/03/30/how-to-use-css3-pseudo-classes/) via
    Smashing Magazine

-   [[Understanding :nth-child Pseudo-class
    Expressions]{.underline}](http://reference.sitepoint.com/css/understandingnthchildexpressions) via
    SitePoint

-   [[Taming Advanced CSS
    Selectors]{.underline}](http://coding.smashingmagazine.com/2009/08/17/taming-advanced-css-selectors/) via
    Smashing Magazine

 

[**Lesson 2** [Detailed
Positioning]{.underline}](https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/)
[**Lesson 4** [Responsive Web
Design]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)

**

[Lesson 4]{.mark} Responsive Web Design

In this Lesson 4

### **HTML**

-   [[Responsive
    Overview]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#responsive-web-design)

-   [[Viewport]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#viewport)

**CSS**

-   [[Flexible
    Layouts]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#flexible-layouts)

-   [[Media
    Queries]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#media-queries)

-   [[Mobile
    First]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#mobile-first)

-   [[Flexible
    Media]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#flexible-media)

**SHARE**

The Internet took off quicker than anyone would have predicted, growing
like crazy. Now, for the past few years, mobile growth has exploded onto
the scene. The growth of mobile Internet usage is also far out pacing
that of general Internet usage growth.

These days it is hard to find someone who doesn't own a mobile device,
or multiple, connected to the Internet. In the UK there are more mobile
phones than people, and should [[trends
continue]{.underline}](http://www.digitalbuzzblog.com/2011-mobile-statistics-stats-facts-marketing-infographic/) mobile
Internet usage will surpass that of desktop Internet usage within the
year.

With the growth in mobile Internet usage comes the question of how to
build websites suitable for all users. The industry response to this
question has become responsive web design, also known as RWD.

### Responsive Overview

Responsive web design is the practice of building a website suitable to
work on every device and every screen size, no matter how large or
small, mobile or desktop. Responsive web design is focused around
providing an intuitive and gratifying experience for everyone. Desktop
computer and cell phone users alike all benefit from responsive
websites.

The [[responsive web
design]{.underline}](http://www.alistapart.com/articles/responsive-web-design/) term
itself was coined, and largely developed, by Ethan Marcotte. A lot of
what is covered in this lesson was first talked about by Ethan online
and in his book [*[Responsive Web
Design]{.underline}*](http://www.abookapart.com/products/responsive-web-design/),
which is worth a read.

![Food Sense Responsive
Layout](./3-25-24/media/image007.png){width="5.0159722222222225in"
height="9.0in"}

Fig. 4

[[Food Sense]{.underline}](http://foodsense.is/) has a beautiful
website, responsive to all different viewport sizes. No matter how large
or small the viewport may be the Food Sense website adjust, creating a
natural user experience.

Responsive vs. Adaptive vs. Mobile

For some the term *responsive* may not be new, and others might be even
more acquainted with the terms *adaptive* or *mobile*. Which may leave
you wondering what exactly is the difference between all of them.

Responsive and adaptive web design are closely related, and often
transposed as one in the same. Responsive generally means to react
quickly and positively to any change, while adaptive means to be easily
modified for a new purpose or situation, such as change. With responsive
design websites continually and fluidly change based on different
factors, such as viewport width, while adaptive websites are built to a
group of preset factors. A combination of the two is ideal, providing
the perfect formula for functional websites. Which term is used
specifically doesn't make a huge difference.

Mobile, on the other hand, generally means to build a separate website
commonly on a new domain solely for mobile users. While this does
occasionally have its place, it normally isn't a great idea. Mobile
websites can be extremely light but they do come with the dependencies
of a new code base and browser sniffing, all of which can become an
obstacle for both developers and users.

Currently the most popular technique lies within responsive web design,
favoring design that dynamically adapts to different browser and device
viewports, changing layout and content along the way. This solution has
the benefits of being all three, responsive, adaptive, and mobile.

### Flexible Layouts

Responsive web design is broken down into three main components,
including flexible layouts, media queries, and flexible media. The first
part, flexible layouts, is the practice of building the layout of a
website with a flexible grid, capable of dynamically resizing to any
width. Flexible grids are built using relative length units, most
commonly percentages or em units. These relative lengths are then used
to declare common grid property values such as width, margin,
or padding.

### Relative Viewport Lengths

CSS3 [[introduced]{.underline}](http://dev.w3.org/csswg/css3-values/#viewport-relative-lengths) some
new relative length units, specifically related to the viewport size of
the browser or device. These new units include vw, vh, vmin, and vmax.
Overall support for these new units isn't great, but it is growing. In
time they look to play a large roll in building responsive websites.

-   vw\
    Viewports width

-   vh\
    Viewports height

-   vmin\
    Minimum of the viewport's height and width

-   vmax\
    Maximum of the viewport's height and width

Flexible layouts do not advocate the use of fixed measurement units,
such as pixels or inches. Reason being, the viewport height and width
continually change from device to device. Website layouts need to adapt
to this change and fixed values have too many constraints. Fortunately,
Ethan pointed out an easy formula to help identify the proportions of a
flexible layout using relative values.

The formula is based around taking the target width of an element and
dividing it by the width of it's parent element. The result is the
relative width of the target element.

+---+----------------------------------------------------------------------+
| 1 | target ÷ context = result                                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Flexible Grid

Let's see how this formula works inside of a two column layout. Below we
have a parent division with the class of container wrapping both
the section and aside elements. The goal is to have the section on the
left and the aside on the right, with equal margins between the two.
Normally the markup and styles for this layout would look a bit like the
following.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;container&quot;&gt;                                          |
|   |                                                                      |
| 2 | &lt;section&gt;&#8230;&lt;/section&gt;                                          |
|   |                                                                      |
| 3 | &lt;aside&gt;&#8230;&lt;/aside&gt;                                              |
|   |                                                                      |
| 4 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .container {                                                         |
|   |                                                                      |
| 2 | width: 538px;                                                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | section,                                                             |
|   |                                                                      |
| 5 | aside {                                                              |
|   |                                                                      |
| 6 | margin: 10px;                                                        |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 | section {                                                            |
|   |                                                                      |
| 9 | float: left;                                                         |
|   |                                                                      |
| 1 | width: 340px;                                                        |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 | aside {                                                              |
|   |                                                                      |
| 1 | float: right;                                                        |
| 2 |                                                                      |
|   | width: 158px;                                                        |
| 1 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Fixed Grid Demo

Using the flexible grid formula we can take all of the fixed units of
length and turn them into relative units. In this example we'll use
percentages but em units would work equally as well. Notice, no matter
how wide the parent container becomes, the section and aside margins and
widths scale proportionally.

+---+----------------------------------------------------------------------+
| 1 | section,                                                             |
|   |                                                                      |
| 2 | aside {                                                              |
|   |                                                                      |
| 3 | margin: 1.858736059%; /&ast; 10px ÷ 538px = .018587361 &ast;/              |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | section {                                                            |
|   |                                                                      |
| 6 | float: left;                                                         |
|   |                                                                      |
| 7 | width: 63.197026%; /&ast; 340px ÷ 538px = .63197026 &ast;/                 |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | aside {                                                              |
|   |                                                                      |
| 1 | float: right;                                                        |
| 0 |                                                                      |
|   | width: 29.3680297%; /&ast; 158px ÷ 538px = .293680297 &ast;/               |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Flexible Grid Demo

Taking the flexible layout concept, and formula, and reapplying it to
all parts of a grid will create a completely dynamic website, scaling to
every viewport size. For even more control within a flexible layout, you
can also leverage the min-width, max-width, min-height,
and max-height properties.

The flexible layout approach alone isn't enough. At times the width of a
browser viewport may be so small that even scaling the the layout
proportionally will create columns that are too small to effectively
display content. Specifically, when the layout gets too small, or too
large, text may become illegible and the layout may begin to break. In
this event, media queries can be used to help build a better experience.

### Media Queries

Media queries were built as an extension to media types commonly found
when targeting and including styles. Media queries provide the ability
to specify different styles for individual browser and device
circumstances, the width of the viewport or device orientation for
example. Being able to apply uniquely [[targeted
styles]{.underline}](https://css-tricks.com/css-media-queries/) opens up
a world of opportunity and leverage to responsive web design.

### Initializing Media Queries

There are a couple different ways to use media queries, using
the @media rule inside of an existing style sheet, importing a new style
sheet using the @import rule, or by linking to a separate style sheet
from within the HTML document. Generally speaking it is recommend to use
the @media rule inside of an existing style sheet to avoid any
additional HTTP requests.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Separate CSS File &#45;&#45;&gt;                                       |
|   |                                                                      |
| 2 | &lt;link href=&quot;styles.css&quot; rel=&quot;stylesheet&quot; media=&quot;all and        |
|   | (max-width: 1024px)&quot;&gt;                                              |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | /&ast; &#0064;media Rule &ast;/                                                 |
|   |                                                                      |
| 2 | &#0064;media all and (max-width: 1024px) {&#8230;}                           |
|   |                                                                      |
| 3 | /&ast; &#0064;import Rule &ast;/                                                |
|   |                                                                      |
| 4 | &#0064;import url(styles.css) all and (max-width: 1024px) {&#8230;}          |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Each media query may include a media type followed by one or more
expressions. Common media types include all, screen, print, tv,
and braille. The HTML5 specification includes new media types, even
including 3d-glasses. Should a media type not be specified the media
query will default the media type to screen.

The media query expression that follows the media type may include
different media features and values, which then allocate to be true or
false. When a media feature and value allocate to true, the styles are
applied. If the media feature and value allocate to false the styles are
ignored.

### Logical Operators in Media Queries

Logical operators in media queries help build powerful expressions.
There are three different logical operators available for use within
media queries, including and, not, and only.

Using the and logical operator within a media query allows an extra
condition to be added, making sure that a browser or devices does
both a, b, c, and so forth. Multiple individual media queries can be
comma separated, acting as an unspoken or operator. The example below
selects all media types between 800 and 1024 pixels wide.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media all and (min-width: 800px) and (max-width: 1024px) {&#8230;}    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

The not logical operator negates the query, specifying any query but the
one identified. In the example below the expression applies to any
device that does not have a color screen. Black and white or monochrome
screens would apply here for example.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media not screen and (color) {&#8230;}                                |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

The only logical operator is a new operator and is not recognized by
user agents using the HTML4 algorithm, thus hiding the styles from
devices or browsers that don't support media queries. Below, the
expression selects only screens in a portrait orientation that have a
user agent capable of rending media queries.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media only screen and (orientation: portrait) {&#8230;}               |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Omitting a Media Type

When using the not and only logical operators the media type may be left
off. In this case the media type is defaulted to all.

### Media Features in Media Queries

Knowing the media query syntax and how logical operators work is a great
introduction to media queries but the true work comes with media
features. Media features identify what attributes or properties will be
targeted within the media query expression.

### Height & Width Media Features

One of the most common media features revolves around determining a
height or width for a device or browser viewport. The height and width
may be found by using the height and width media features. Each of these
media features may then also be prefixed with the min or max qualifiers,
building a feature such as min-width or max-width.

The height and width features are based off the height and width of the
viewport rendering area, the browser window for example. Values for
these height and width media features may be any length unit, relative
or absolute.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media all and (min-width: 320px) and (max-width: 780px) {&#8230;}     |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Within responsive design the most commonly used features
include min-width and max-width. These help build responsive websites on
desktops and mobile devices equally, avoiding any confusion with device
features.

### Using Minimum & Maximum Prefixes

The min and max prefixes can be used on quite a few media features.
The min prefix indicates a values of *greater than or equal to* while
the max prefix indicates a value of *less than or equal to*.
Using min and max prefixes avoid any conflict with the general HTML
syntax, specifically not using the &lt; and &gt; symbols.

### Orientation Media Feature

The orientation media feature determines if a device is in
the landscape or portrait orientation. The landscape mode is triggered
when the display is wider than taller, and the portrait mode is
triggered when the display is taller than wider. This media feature
plays a large part with mobile devices.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media all and (orientation: landscape) {&#8230;}                      |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Aspect Ratio Media Features

The aspect-ratio and device-aspect-ratio features specifies
the width/height pixel ratio of the targeted rendering area or output
device. The min and max prefixes are available to use with the different
aspect ratio features, identifying a ratio above or below that of which
is stated.

The value for the aspect ratio feature consist of two positive integers
separated by a forward slash. The first integer identifies the width in
pixels while the second integer identifies the height in pixels.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media all and (min-device-aspect-ratio: 16/9) {&#8230;}               |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Pixel Ratio Media Features

In addition to the aspect ratio media features there are
also pixel-ratio media features. These features do include
the device-pixel-ratio feature as well as min and max prefixes.
Specifically, the pixel ratio feature is great for identifying high
definition devices, including retina displays. Media queries for doing
so look like the following.

+---+-------------------------------------------------------------------+
| 1 | &#0064;media only screen and (-webkit-min-device-pixel-ratio: 1.3),    |
|   | only screen and (min-device-pixel-ratio: 1.3) {&#8230;}              |
| 2 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

### Resolution Media Feature

The resolution media feature specifies the resolution of the output
device in pixel density, also known as dots per inch or DPI.
The resolution media feature does accept the min and max prefixes.
Additionally, the resolution media feature will accept dots per pixel
(1.3dppx), dots per centimeter (118dpcm), and other length based
resolution values.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media print and (min-resolution: 300dpi) {&#8230;}                    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Other Media Features

Other media features include identifying available output colors with
use of the color, color-index, and monochrome features, identifying
bitmap devices with the grid feature, and identifying the scanning
process of a television with the scan feature. These features are less
common but equally as helpful when needed.

### Media Query Browser Support

Unfortunately media queries do not work within Internet Explorer 8 and
below, as well as other legacy browsers. There are, however, a couple
suitable polyfills written in Javascript.

[[Respond.js]{.underline}](https://github.com/scottjehl/Respond/) is a
lightweight polyfill that only looks for min/max-width media types,
which is perfect should those be the only media query types
used. [[CSS3-MediaQueries.js]{.underline}](https://code.google.com/p/css3-mediaqueries-js/) is
a more developed, and heavier, polyfill offering support for a larger
array of more complex media queries. Additionally, keep in mind any
polyfill can have performance concerns, and potentially slow down
websites. Make sure that any given polyfill is worth the performance
trade off.

### Media Queries Demo

Using media queries we will now rewrite the flexible layout we built
previously. One of the current problems within the demo appears when the
aside width becomes uselessly small within smaller viewports. Adding a
media query for viewports under 420 pixels wide we can change the layout
by turning off the floats and changing the widths of
the section and aside.

+---+----------------------------------------------------------------------+
| 1 | &#0064;media all and (max-width: 420px) {                                 |
|   |                                                                      |
| 2 | section, aside {                                                     |
|   |                                                                      |
| 3 | float: none;                                                         |
|   |                                                                      |
| 4 | width: auto;                                                         |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

![Demo without Media
Queries](./3-25-24/media/image008.png){width="3.4131944444444446in"
height="1.2118055555555556in"}

**Fig. 4.**Without any media queries the section and aside become quite
small. Perhaps too small to even contain any real content.

![Demo with Media
Queries](./3-25-24/media/image009.png){width="3.4131944444444446in"
height="2.2881944444444446in"}

**Fig. 4.**Using media queries to remove the floats and change their
widths, the section and aside are now able to span the full width of the
viewport, allowing breathing room for any existing content.

### Identifying Breakpoints

Your instinct might be to write media query breakpoints around common
viewport sizes as determined by different device resolutions, such
as 320px, 480px, 768px, 1024px, 1224px, and so forth. This is
a **bad** idea.

When building a responsive website it should adjust to an array of
different viewport sizes, regardless of the device. Breakpoints should
only be introduced when a website starts to break, look weird, or the
experience is being hampered.

Additionally, new devices and resolutions are being released all of the
time. Trying to keep up with these changes could be an endless process.

### Mobile First

One popular technique with using media queries is called *mobile first*.
The [[mobile
first]{.underline}](https://abookapart.com/products/mobile-first) approach
includes using styles targeted at smaller viewports as the default
styles for a website, then use media queries to add styles as the
viewport grows.

The operating belief behind mobile first design is that a user on a
mobile device, commonly using a smaller viewport, shouldn't have to load
the styles for a desktop computer only to have them over written with
mobile styles later. Doing so is a waste of bandwidth. Bandwidth that is
precious to any users looking for a snappy website.

The mobile first approach also advocates designing with the constraints
of a mobile user in mind. Before too long, the majority of Internet
consumption will be done on a mobile device. Plan for them accordingly
and develop intrinsic mobile experiences.

A breakout of mobile first media queries might look abit like the
following.

+---+----------------------------------------------------------------------+
| 1 | /&ast; Default styles first then media queries &ast;/                      |
|   |                                                                      |
| 2 | &#0064;media screen and (min-width: 400px) {&#8230;}                         |
|   |                                                                      |
| 3 | &#0064;media screen and (min-width: 600px) {&#8230;}                         |
|   |                                                                      |
| 4 | &#0064;media screen and (min-width: 1000px) {&#8230;}                        |
|   |                                                                      |
| 5 | &#0064;media screen and (min-width: 1400px) {&#8230;}                        |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Additionally, downloading unnecessary media assets can be stopped by
using media queries. Generally speaking, avoiding CSS3 shadows,
gradients, transforms, and animations within mobile styles isn't a bad
idea either. When used excessively, they cause heavy loading and can
even reduce a device's battery life.

+---+----------------------------------------------------------------------+
| 1 | /&ast; Default media &ast;/                                                |
|   |                                                                      |
| 2 | body {                                                               |
|   |                                                                      |
| 3 | background: #ddd;                                                    |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | /&ast; Media for larger devices &ast;/                                     |
|   |                                                                      |
| 6 | &#0064;media screen and (min-width: 800px) {                              |
|   |                                                                      |
| 7 | body {                                                               |
|   |                                                                      |
| 8 | background-image: url(&quot;bg.png&quot;) 50% 50% no-repeat;                 |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | }                                                                    |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Mobile First Demo

Adding media queries to our previous example, we overwrote a handful of
styles in order to have a better layout on viewports under 420 pixels
wide. Rewriting this code to use the mobile styles first by default then
adding media queries to adjust for viewports over 420 pixels wide we
build the following:

+---+----------------------------------------------------------------------+
| 1 | section,                                                             |
|   |                                                                      |
| 2 | aside {                                                              |
|   |                                                                      |
| 3 | margin: 1.858736059%;                                                |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | &#0064;media all and (min-width: 420px) {                                 |
|   |                                                                      |
| 6 | .container {                                                         |
|   |                                                                      |
| 7 | max-width: 538px;                                                    |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | section {                                                            |
|   |                                                                      |
| 1 | float: left;                                                         |
| 0 |                                                                      |
|   | width: 63.197026%;                                                   |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 | aside {                                                              |
| 2 |                                                                      |
|   | float: right;                                                        |
| 1 |                                                                      |
| 3 | width: 29.3680297%;                                                  |
|   |                                                                      |
| 1 | }                                                                    |
| 4 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Mobile First Demo

Notice, this is the same amount of code as before. The only exception
here is that mobile devices only have to render only **one** CSS
declaration. All of the other styles are deferred, only loading on
larger viewports and done so without overwriting any initial styles.

### Viewport

Mobile devices generally do a pretty decent job of displaying websites
these days. Sometimes they could use a little assistance though,
particularly around identifying
the [[viewport]{.underline}](http://dev.opera.com/articles/view/an-introduction-to-meta-viewport-and-viewport/) size,
scale, and resolution of a website. To remedy this, Apple invented
the viewport meta tag.

![Website without Viewport Meta
Tag](./3-25-24/media/image010.png){width="3.3368055555555554in"
height="4.336805555555555in"}

**Fig. 4.** Although this demo has media queries, many mobile devices
still do not know the initial width or scale of the website. Therefore,
they may not interrupt media queries.

### Viewport Height & Width

Using the viewport meta tag with either the height or width values will
define the height or width of the viewport respectively. Each value
accepts either a positive integer or keyword. For the height property
the keyword device-height value is accepted, and for the width property
the keyword device-width is accepted. Using these keywords will inherit
the device's default height and width value.

For the best results, and the best looking website, it is recommend that
you use the device defaults by applying
the device-height and device-width values.

+---+----------------------------------------------------------------------+
| 1 | &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width&quot;&gt;            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

![Website with Viewport Meta
Tag](./3-25-24/media/image011.png){width="3.3368055555555554in"
height="4.336805555555555in"}

**Fig. 4.** Letting devices know the intended width of the
website, device-width in this case, allows the website to be sized
properly and to pick up any qualifying media queries.

### Viewport Scale

To control how a website is scaled on a mobile device, and how users can
continue to scale a website, use
the minimum-scale, maximum-scale, initial-scale,
and user-scalable properties.

The initial-scale of a website should be set to 1 as this defines the
ratio between the device height, while in a portrait orientation, and
the viewport size. Should a device be in landscape mode this would be
the ratio between the device width and the viewport size. Values
for initial-scale should always be a positive integer between 0 and 10.

+---+----------------------------------------------------------------------+
| 1 | &lt;meta name=&quot;viewport&quot; content=&quot;initial-scale=2&quot;&gt;               |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

![Viewport Scale Meta
Tag](./3-25-24/media/image012.png){width="3.3368055555555554in"
height="4.336805555555555in"}

**Fig. 4.** Using an integer above 1 will zoom the website to be larger
than the default scale. Generally speaking, this value will most
commonly be set to 1.

The minimum-scale and maximum-scale values determine how small and how
large a viewport may be scaled. When using minimum-scale the value
should be a positive integer lower than or equal to the initial-scale.
Using the same reasoning, the maximum-scale value should be a positive
integer greater than or equal to the initial-scale. Values for both of
these must also be between 0 and 10.

+---+----------------------------------------------------------------------+
| 1 | &lt;meta name=&quot;viewport&quot; content=&quot;minimum-scale=0&quot;&gt;               |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Generally speaking, these values should not be set to the same value as
the initial-scale. This would disable any zooming, which can be
accomplished instead by using the user-scalable value. Setting
the user-scalable value to no will disable any zooming. Alternatively,
setting the user-scalable value to yes will turn on zooming.

Turning off the ability to scale a website is a **bad idea**. It harms
accessibility and usability, preventing those with disabilities from
viewing a website as desired.

+---+----------------------------------------------------------------------+
| 1 | &lt;meta name=&quot;viewport&quot; content=&quot;user-scalable=yes&quot;&gt;             |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Viewport Resolution

Letting the browser decide how to scale a website based off any viewport
scale values usually does the trick. When more control is needed,
specifically over the resolution of a device,
the target-densitydpi value may be used. The target-densitydpi viewport
accepts a handful of values
including device-dpi, high-dpi, medium-dpi, low-dpi, or an actual DPI
number.

Using the target-densitydpi viewport value is rare, but extremely
helpful when pixel by pixel control is needed.

+---+----------------------------------------------------------------------+
| 1 | &lt;meta name=&quot;viewport&quot; content=&quot;target-densitydpi=device-dpi&quot;&gt;  |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Combining Viewport Values

The viewport meta tag will accept individual values as well as multiple
values, allowing multiple viewport properties to be set at once. Setting
multiple values requires comma separating them within
the content attribute value. One of the recommended viewport values is
outlined below, using both the width and initial-scale properties.

+---+----------------------------------------------------------------------+
| 1 | &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,               |
|   | initial-scale=1&quot;&gt;                                                  |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

![Website with Viewport Meta
Tag](./3-25-24/media/image011.png){width="3.3368055555555554in"
height="4.336805555555555in"}

**Fig. 4** A combination
of width=device-width and initial-scale=1 provide the initial size and
zoom commonly required.

### CSS Viewport Rule

Since the viewport meta tag revolves so heavily around setting the
styles of how a website should be rendered it has been recommend to move
the viewport from a meta tag with HTML to an @ rule within CSS. This
helps keep the style separated from content, providing a more semantic
approach.

Currently some browsers have already implemented the @viewport rule,
however support isn't great across the board. The previously
recommended viewport meta tag would look like the
following @viewport rule in CSS.

+---+--------------------------------------------------------------------+
| 1 | &#0064;viewport {                                                       |
|   |                                                                    |
| 2 | width: device-width;                                               |
|   |                                                                    |
| 3 | zoom: 1;                                                           |
|   |                                                                    |
| 4 | }                                                                  |
|   |                                                                    |
| 5 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Flexible Media

The final, equally important aspect to responsive web design involves
flexible media. As viewports begin to change size media doesn't always
follow suit. Images, videos, and other media types need to be scalable,
changing their size as the size of the viewport changes.

One quick way to make media scalable is by using the max-width property
with a value of 100%. Doing so ensures that as the viewport gets smaller
any media will scale down according to its containers width.

+---+----------------------------------------------------------------------+
| 1 | img, video, canvas {                                                 |
|   |                                                                      |
| 2 | max-width: 100%;                                                     |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Flexible Media Demo

### Flexible Embedded Media

Unfortunately the max-width property doesn't work well for all instances
of media, specifically around iframes and embedded media. When it comes
to third party websites, such as YouTube, who use iframes for embedded
media this is a huge disappointment. Fortunately, there is a [[work
around]{.underline}](http://www.alistapart.com/articles/creating-intrinsic-ratios-for-video/).

To get embedded media to be fully responsive, the embedded element needs
to be absolutely positioned within a parent element. The parent element
needs to have a width of 100% so that it may scale based on the width of
the viewport. The parent element also needs to have a height of 0 to
trigger the hasLayout mechanism within Internet Explorer.

Padding is then given to the bottom of the parent element, the value of
which is set in the same aspect ratio of the video. This allows the
height of the parent element to be proportionate to that of it's width.
Remember the responsive design formula from before? If a video has an
aspect ratio of 16:9, 9 divided by 16 equals .5625, thus requiring a
bottom padding of 56.25%. Padding on the bottom and not the top is
specifically used to prevent Internet Explorer 5.5 from breaking, and
treating the parent element as an absolutely positioned element.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure&gt;                                                           |
|   |                                                                      |
| 2 | &lt;iframe                                                             |
|   | src=&quot;https://www.youtube.com/embed/Sv3xVOs7_No&quot;&gt;&lt;/iframe&gt;       |
| 3 |                                                                      |
|   | &lt;/figure&gt;                                                          |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | figure {                                                             |
|   |                                                                      |
| 2 | height: 0;                                                           |
|   |                                                                      |
| 3 | padding-bottom: 56.25%; /&ast; 16:9 &ast;/                                 |
|   |                                                                      |
| 4 | position: relative;                                                  |
|   |                                                                      |
| 5 | width: 100%;                                                         |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | iframe {                                                             |
|   |                                                                      |
| 8 | height: 100%;                                                        |
|   |                                                                      |
| 9 | left: 0;                                                             |
|   |                                                                      |
| 1 | position: absolute;                                                  |
| 0 |                                                                      |
|   | top: 0;                                                              |
| 1 |                                                                      |
| 1 | width: 100%;                                                         |
|   |                                                                      |
| 1 | }                                                                    |
| 2 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Flexible Embedded Media Demo

For security reasons CodePen doesn't allow iframes within embedded code
samples, however you may [[review and edit this
code]{.underline}](https://codepen.io/shayhowe/pen/cbmsI) on their
website.

100% Wide Container

75% Wide Container

50% Wide Container

### Resources & Links

-   [[Responsive Web
    Design]{.underline}](http://www.alistapart.com/articles/responsive-web-design/) via
    A List Apart

-   [[Viewport Percentage
    Lengths]{.underline}](http://dev.w3.org/csswg/css3-values/#viewport-relative-lengths) via
    W3C

-   [[CSS Media
    Queries]{.underline}](https://css-tricks.com/css-media-queries/) via
    CSS-Tricks

-   [[Mobile
    First]{.underline}](https://abookapart.com/products/mobile-first) via
    Luke Wroblewski

-   [[An Introduction to Meta Viewport and
    &#0064;viewport]{.underline}](http://dev.opera.com/articles/view/an-introduction-to-meta-viewport-and-viewport/) via
    Dev.Opera

 [**Lesson 3** [Complex
Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/complex-selectors/)
[**Lesson 5**
[Preprocessors]{.underline}](https://learn.shayhowe.com/advanced-html-css/preprocessors/)

[Lesson 5]{.mark} Preprocessors

In this Lesson 5

**HTML**

-   [[Haml]{.underline}](https://learn.shayhowe.com/advanced-html-css/preprocessors/#haml)

**CSS**

-   [[SCSS & Sass]{.underline}](https://learn.shayhowe.com/advanced-html-css/preprocessors/#scss-sass)

-   [[Other
    Preprocessors]{.underline}](https://learn.shayhowe.com/advanced-html-css/preprocessors/#other-preprocessors)

**SHARE**

In time writing HTML and CSS may feel a bit taxing, requiring a lot of
the same tasks to be completed over and over again. Tasks such as
closing tags in HTML or repetitively having to looking up hexadecimal
color values in CSS.

These different tasks, while commonly small, do add up to quite a bit of
inefficiency. Fortunately these, and a handful of other inefficiencies,
have been recognized and preprocessor solutions have risen to the
challenge.

A preprocessor is a program that takes one type of data and converts it
to another type of data. In the case of HTML and CSS, some of the more
popular preprocessor languages
include [[Haml]{.underline}](http://haml.info/) and [[Sass]{.underline}](http://sass-lang.com/).
Haml is processed into HTML and Sass is processed into CSS.

Upon setting out to solve some of the more common problems, Haml and
Sass found many additional ways to empower HTML and CSS, not only by
removing the inefficiencies but also in creating ways to make building
websites easier and more logical. The popularity of preprocessors have
also brought along different frameworks to support them, one of the more
popular being Compass.

### Haml

Haml, known as [[HTML abstraction markup
language]{.underline}](http://haml.info/docs/yardoc/file.REFERENCE.html),
is a markup language with the single goal of providing the ability to
write beautiful markup. Serving as its own markup language, code written
in Haml is later processed to HTML. Haml promotes DRY and well
structured markup, providing a pleasing experience for anyone having to
write or read it.

### Installation

Haml requires Ruby to be compiled to HTML, so the first step to using it
is to ensure that Ruby is installed. Fortunately for those on Mac OS X
Ruby comes preinstalled, and those on a Windows machine may
visit [[Windows Installer]{.underline}](http://rubyinstaller.org/) for
directions. Upon confirming Ruby is installed the gem install
haml command needs to be run from the command line, using Terminal or
the alike command line program, to install Haml.

+---+----------------------------------------------------------------------+
| 1 | gem install haml                                                     |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Files written in the Haml markup should be saved with the file extension
of .haml. To then convert these files from Haml to HTML the haml command
below needs to be run to compile each individual file.

+---+----------------------------------------------------------------------+
| 1 | haml index.haml index.html                                           |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

In the example above, the file index.haml is converted to HTML and saved
as index.html within the same directory. This command has to be run
within the same directory the files reside in. Should the command be run
outside this directory the path where the files reside need to be
included within the command. At any time the command haml &#45;&#45;help may be
run to see a list of different available options.

### Watching a File or Directory

Unfortunately Haml doesn't provide a way to watch a file, or directory,
for changes without the use of another dependency.

Inside of a Rails application a Haml dependency may be added in the
Gemfile, thus automatically compiling Haml files to HTML upon any
changes. There are a few desktop applications available for those not
using Rails, one of the more popular
being [[CodeKit]{.underline}](https://codekitapp.com/).

On top of Haml CodeKit also supports other preprocessors, which may also
come in handy.

### Doctype

The first part to writing a document in Haml is knowing what type
of doctype is to be used. When working with HTML documents, the general
document type is going to be the HTML5 doctype. In Haml document types
are identified with three exclamation points, !!! followed by any
specifics if necessary.

The default doctype in Haml is the HTML 1.0 Transitional document type
so in order to make this the HTML5 doctype the number five has to be
passed in after the exclamation points, !!! 5.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | !!! 5                                                                |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;!DOCTYPE html&gt;                                                    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Declaring Elements

One of the defining features of Haml is its syntax, and how to [[declare
and
nest]{.underline}](https://coderwall.com/p/aivizg/introduction-to-haml--2) elements.
HTML elements generally have opening and closing tags, however within
Haml elements only have one tag, the opening. Elements are initialized
with a percent sign, %, and then indented to identify nesting.
Indentation with Haml can be accomplish with one or more spaces, however
what is important is that the indentation remain consistent. Hard tabs
or spaces cannot be mixes together, and the same number of tabs or
spaces must be the same throughout an entire document.

Removing the need for both opening and closing tags, as well as
mandating the structure with indentation creates an easy to follow
outline. At any given time the markup can be scanned and changed without
struggle.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %body                                                                |
|   |                                                                      |
| 2 | %header                                                              |
|   |                                                                      |
| 3 | %h1 Hello World                                                      |
|   |                                                                      |
| 4 | %section                                                             |
|   |                                                                      |
| 5 | %p Lorem ipsum dolor sit amet.                                       |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;body&gt;                                                             |
|   |                                                                      |
| 2 | &lt;header&gt;                                                           |
|   |                                                                      |
| 3 | &lt;h1&gt;Hello World&lt;/h1&gt;                                             |
|   |                                                                      |
| 4 | &lt;/header&gt;                                                          |
|   |                                                                      |
| 5 | &lt;section&gt;                                                          |
|   |                                                                      |
| 6 | &lt;p&gt;Lorem ipsum dolor sit amet.&lt;/p&gt;                               |
|   |                                                                      |
| 7 | &lt;/section&gt;                                                         |
|   |                                                                      |
| 8 | &lt;/body&gt;                                                            |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Handling Text

Text within Haml can be placed on the same line as the declared element,
or indented below the element. Text cannot be both on the same line as
the declared element and nested below it, it has to be either or. The
example from above could be rewritten as the following:

+---+--------------------------------------------------------------------+
| 1 | %body                                                              |
|   |                                                                    |
| 2 | %header                                                            |
|   |                                                                    |
| 3 | %h1                                                                |
|   |                                                                    |
| 4 | Hello World                                                        |
|   |                                                                    |
| 5 | %section                                                           |
|   |                                                                    |
| 6 | %p                                                                 |
|   |                                                                    |
| 7 | Lorem ipsum dolor sit amet.                                        |
|   |                                                                    |
| 8 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Attributes

Attributes, as with elements, are declared a bit differently in Haml.
Attributes are declared directly after the element in either {} or (),
all depending if you wish to use Ruby or HTML syntax. Ruby style
attributes will use the standard hash syntax inside of {}, while HTML
style attributes will use standard HTML syntax inside of ().

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %img{:src =&gt; &quot;shay.jpg&quot;, :alt =&gt; &quot;Shay Howe&quot;}                  |
|   |                                                                      |
| 2 | %img{src: &quot;shay.jpg&quot;, alt: &quot;Shay Howe&quot;}                          |
|   |                                                                      |
| 3 | %img(src=&quot;shay.jpg&quot; alt=&quot;Shay Howe&quot;)                             |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;img src=&quot;shay.jpg&quot; alt=&quot;Shay Howe&quot;&gt;                           |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Classes & IDs

If you wish to, Class and ID attributes may be declared the same as all
other attributes, however they may also be treated a bit differently.
Rather than listing out the class or ID attribute name and value
inside {} or () the value can be identified directly after the element.
Using either a . for classes or a # for an ID the value can be added
directly after the element.

Additionally, attributes may be mixed and matched, chaining them
together in the appropriate format. Classes are to be separated with
a . and other attributes may be added using one of the previously
outlined formats.

### **Haml**

+---+----------------------------------------------------------------------+
| 1 | %section.feature                                                     |
|   |                                                                      |
| 2 | %section.feature.special                                             |
|   |                                                                      |
| 3 | %section#hello                                                       |
|   |                                                                      |
| 4 | %section#hello.feature(role=&quot;region&quot;)                              |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;section class=&quot;feature&quot;&gt;&lt;/section&gt;                            |
|   |                                                                      |
| 2 | &lt;section class=&quot;feature special&quot;&gt;&lt;/section&gt;                    |
|   |                                                                      |
| 3 | &lt;section id=&quot;hello&quot;&gt;&lt;/section&gt;                                 |
|   |                                                                      |
| 4 | &lt;section class=&quot;feature&quot; id=&quot;hello&quot;                             |
|   | role=&quot;region&quot;&gt;&lt;/section&gt;                                        |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Division Classes & IDs

In the event a class or ID is used on a div the %div may be omitted, and
the class or ID value can be used outright. Again, classes are to be
identified with a . and IDs are to be identified with a #.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | .awesome                                                             |
|   |                                                                      |
| 2 | .awesome.lesson                                                      |
|   |                                                                      |
| 3 | #getting-started.lesson                                              |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;awesome&quot;&gt;&lt;/div&gt;                                    |
|   |                                                                      |
| 2 | &lt;div class=&quot;awesome lesson&quot;&gt;&lt;/div&gt;                             |
|   |                                                                      |
| 3 | &lt;div class=&quot;lesson&quot; id=&quot;getting-started&quot;&gt;&lt;/div&gt;              |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Boolean Attributes

Boolean attributes are handled just as they would be within Ruby or
HTML, all depending on the syntax being used.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %input{:type =&gt; &quot;checkbox&quot;, :checked =&gt; true}                    |
|   |                                                                      |
| 2 | %input(type=&quot;checkbox&quot; checked=true)                               |
|   |                                                                      |
| 3 | %input(type=&quot;checkbox&quot; checked)                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;input type=&quot;checkbox&quot; checked&gt;                                  |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Escaping Text

One of the benefits of Haml is the ability to evaluate and run Ruby,
however this isn't always the desired action. Text, and lines of code,
can be escaped by using a backslash, \&#0044; allowing the text to be
rendered explicitly without being executed.

In the example below, the first instance of = &#0064;author is executed Ruby,
pulling the authors name from the application. The second instance,
starting with the backslash, is escaped text, printing it as is, without
execution.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | .author                                                              |
|   |                                                                      |
| 2 | = &#0064;author                                                           |
|   |                                                                      |
| 3 | \\= &#0064;author                                                         |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;author&quot;&gt;                                             |
|   |                                                                      |
| 2 | Shay Howe                                                            |
|   |                                                                      |
| 3 | = &#0064;author                                                           |
|   |                                                                      |
| 4 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Text Escaping Alternatives

Occasionally escaping text doesn't quite do the job and Ruby is needed
to generate the desired output. One popular instance of this is when
trying to include a period directly after a link, but not as part of the
anchor text. Putting the period on a new line isn't acceptable as it
will be treated as an empty class value, causing a compiling error.
Adding a backslash before the period will escape the character however
it places a blank space between the last word and the period. Again, not
producing the desired output.

In these cases a Ruby helper comes in handy. In the example below, the
helper is used to place a period directly after the last word but still
outside of the anchor text.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %p                                                                   |
|   |                                                                      |
| 2 | Shay is                                                              |
|   |                                                                      |
| 3 | = succeed &quot;.&quot; do                                                   |
|   |                                                                      |
| 4 | %a{:href =&gt; &quot;#&quot;} awesome                                          |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;p&gt;Shay is &lt;a href=&quot;#&quot;&gt;awesome&lt;/a&gt;.&lt;/p&gt;                    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Comments

As with elements and attributes, comments are handled a bit differently
in Haml as well. Simply enough, code can be commented out with the use
of a single forward slash, /. Individual lines may be commented out with
the use of a forward slash at the beginning of the line, and blocks of
code can be commented out by being nested underneath a forward slash.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %div                                                                 |
|   |                                                                      |
| 2 | / Commented line                                                     |
|   |                                                                      |
| 3 | Actual line                                                          |
|   |                                                                      |
| 4 | /                                                                    |
|   |                                                                      |
| 5 | %div                                                                 |
|   |                                                                      |
| 6 | Commented block                                                      |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div&gt;                                                              |
|   |                                                                      |
| 2 | &lt;!&#45;&#45; Commented line &#45;&#45;&gt;                                          |
|   |                                                                      |
| 3 | Actual line                                                          |
|   |                                                                      |
| 4 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 5 | &lt;!&#45;&#45;                                                               |
|   |                                                                      |
| 6 | &lt;div&gt;                                                              |
|   |                                                                      |
| 7 | Commented block                                                      |
|   |                                                                      |
| 8 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 9 | &#45;&#45;&gt;                                                                |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Conditional Comments

Conditional comments are also handled differently in Haml. To create a
conditional comment use square brackets, &lbrack;&rbrack;, around the condition.
These square brackets need to be placed directly after the forward
slash.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | /&lbrack;if lt IE 9&rbrack;                                                      |
|   |                                                                      |
| 2 | %script{:src =&gt; &quot;html5shiv.js&quot;}                                   |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45;&lbrack;if lt IE 9&rbrack;&gt;                                               |
|   |                                                                      |
| 2 | &lt;script src=&quot;html5shiv.js&quot;&gt;&lt;/script&gt;                           |
|   |                                                                      |
| 3 | &lt;&#0033;[endif&rbrack;&#45;&#45;&gt;                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Silent Comments

Haml also provides the ability to create Haml specific comments, or
silent comments. Silent comments differ from general HTML comments in
that upon being complied any content within a silent comment is
completely removed from the page, and is not displayed in the output.
Silent comments are initialized with a dash then the number sign, -#. As
with other comments, silent comments may be used to remove one line or
multiple lines with the use of nesting.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %div                                                                 |
|   |                                                                      |
| 2 | -# Removed line                                                      |
|   |                                                                      |
| 3 | Actual line                                                          |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div&gt;                                                              |
|   |                                                                      |
| 2 | Actual line                                                          |
|   |                                                                      |
| 3 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Filters

Haml provides a handful of filters, allowing different types of input to
be used inside of Haml. Filters are identified with a colon followed by
the name of the filter, :markdown for example, with all of the content
to be filtered nested underneath.

### Common Filters

Below are some of the more common filters, with the more popular ones of
the group being :css and :javascript.

-   :cdata

-   :coffee

-   :css

-   :erb

-   :escaped

-   :javascript

-   :less

-   :markdown

-   :maruku

-   :plain

-   :preserve

-   :ruby

-   :sass

-   :scss

-   :textile

### Javascript Filter

**Haml**

+---+----------------------------------------------------------------------+
| 1 | :javascript                                                          |
|   |                                                                      |
| 2 | &#36;(&#39;button&#39;).on(&#39;click&#39;, function(event) {                       |
|   |                                                                      |
| 3 | &#36;(&#39;p&#39;).hide(&#39;slow&#39;);                                            |
|   |                                                                      |
| 4 | });                                                                  |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;script&gt;                                                           |
|   |                                                                      |
| 2 | &#36;(&#39;button&#39;).on(&#39;click&#39;, function(event) {                       |
|   |                                                                      |
| 3 | &#36;(&#39;p&#39;).hide(&#39;slow&#39;);                                            |
|   |                                                                      |
| 4 | });                                                                  |
|   |                                                                      |
| 5 | &lt;/script&gt;                                                          |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### CSS & Sass Filters

**Haml**

+---+----------------------------------------------------------------------+
| 1 | :css                                                                 |
|   |                                                                      |
| 2 | .container {                                                         |
|   |                                                                      |
| 3 | margin: 0 auto;                                                      |
|   |                                                                      |
| 4 | width: 960px;                                                        |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | :sass                                                                |
|   |                                                                      |
| 7 | .container                                                           |
|   |                                                                      |
| 8 | margin: 0 auto                                                       |
|   |                                                                      |
| 9 | width: 960px                                                         |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;style&gt;                                                            |
|   |                                                                      |
| 2 | .container {                                                         |
|   |                                                                      |
| 3 | margin: 0 auto;                                                      |
|   |                                                                      |
| 4 | width: 960px;                                                        |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | &lt;/style&gt;                                                           |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Ruby Interpolation

As previously mentioned Haml can evaluate Ruby, and there may
occasionally be times where Ruby needs to be evaluated inside of plain
text. In this event Ruby needs to be interpolated, accomplished by
wrapping the necessary Ruby code inside .

Below is an example of Ruby being interpolated as part of a class name.

**Haml**

+---+----------------------------------------------------------------------+
| 1 | %div{:class =&gt; &quot;student-#{@student.name}&quot;}                        |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;student-shay&quot;&gt;                                       |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### SCSS & Sass

SCSS and Sass are preprocessing languages which are compiled to CSS,
resembling Haml a bit in that they make writing code easier, and provide
quite a bit of leverage in doing so. Individually SCSS and Sass come
from the same origin however they are technical different syntaxes.

Sass, [[Syntactically Awesome
Stylesheets]{.underline}](https://sass-lang.com/documentation/), came
first and is a strict indented syntax. SCSS, Sassy CSS, followed shortly
after providing the same firing power of Sass but with a more flexible
syntax, including the ability to write plain CSS.

### Installation

As with Haml, SCSS and Sass
are [[compiled]{.underline}](http://sassmeister.com/) using Ruby
therefore Ruby needs to be installed to produce CSS files. Please follow
the directions from before to install, or ensure Ruby is installed.

Once Ruby is installed the gem install sass command needs to be run from
the command line to install SCSS and Sass.

+---+----------------------------------------------------------------------+
| 1 | gem install sass                                                     |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Files written in SCSS or Sass need to have the .scss or .sass file
extensions respectively. To convert either of these file types
to .css the following sass command needs to be run.

+---+----------------------------------------------------------------------+
| 1 | sass styles.sass styles.css                                          |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

The command above takes the styles.sass Sass file and compiles it to
the styles.css file. As with Haml, these file names are paths and need
to be executed respectively. The above command works when those files
reside within the directory from which the command is run, should the
files reside outside of the directory their path needs to be explicitly
stated within the command.

Should changes to a file be ongoing Sass can watch the file and
recompile the CSS every time a change takes place. To watch a Sass file
the following sass command may be run.

+---+----------------------------------------------------------------------+
| 1 | sass &#45;&#45;watch styles.sass:styles.css                                 |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Additionally, instead of compiling or watching individual files, Sass is
capable of compiling and watching entire directories of files. For
example, to watch an entire directory of Sass files and convert them to
CSS the sass command below may be run.

+---+----------------------------------------------------------------------+
| 1 | sass &#45;&#45;watch assets/sass:public/css                                 |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Converting Files from SCSS to Sass & Vice Versa

On top of being able to convert SCSS and Sass files to CSS you can also
convert files from SCSS to Sass and vice versa. To do so
the sass commands below may be used to convert a SCSS file to Sass, and
then a Sass file to SCSS respectively.

+---+--------------------------------------------------------------------+
| 1 | &#0035; Convert Sass to SCSS                                            |
|   |                                                                    |
| 2 | sass-convert styles.sass styles.scss                               |
|   |                                                                    |
| 3 | &#0035; Convert SCSS to Sass                                            |
|   |                                                                    |
| 4 | sass-convert styles.scss styles.sass                               |
|   |                                                                    |
| 5 |                                                                    |
|   |                                                                    |
| 6 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Syntax

As previously mentioned the primary difference between SCSS and Sass is
their syntax, and their difference in severity. The syntax of SCSS isn't
much different than that of regular CSS. In fact, standard CSS will run
inside of SCSS. Sass on the other hand is fairly strict, and any
indenting or character errors will prohibit the styles from compiling.
Sass omits all curly brackets, {}, and semicolons, ;, relying on
indentation and clear line breaks for formatting.

**SCSS**

+---+----------------------------------------------------------------------+
| 1 | .new {                                                               |
|   |                                                                      |
| 2 | color: #ff7b29;                                                      |
|   |                                                                      |
| 3 | font-weight: bold;                                                   |
|   |                                                                      |
| 4 | span {                                                               |
|   |                                                                      |
| 5 | text-transform: uppercase;                                           |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Sass**

+---+----------------------------------------------------------------------+
| 1 | .new                                                                 |
|   |                                                                      |
| 2 | color: #ff7b29                                                       |
|   |                                                                      |
| 3 | font-weight: bold                                                    |
|   |                                                                      |
| 4 | span                                                                 |
|   |                                                                      |
| 5 | text-transform: uppercase                                            |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .new {                                                               |
|   |                                                                      |
| 2 | color: #ff7b29;                                                      |
|   |                                                                      |
| 3 | font-weight: bold;                                                   |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | .new span {                                                          |
|   |                                                                      |
| 6 | text-transform: uppercase;                                           |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Using SCSS vs. Sass

Deciding on whether to use SCSS or Sass boils down to personal
preference, and is a decision to be made based on what is best for a
specific team and project. There are pros and cons to each syntax, all
of which are fair.

Personally, I prefer the Sass syntax as it requires less characters and
provides, I believe, a cleaner syntax. Sass will not allow straight CSS
input as SCSS does, and will not put up with any composition errors.
Sass has a bit more of a learning curve, however a learning curve I see
well worth the ease of manageable styles.

Moving forward the examples in this lesson will use Sass, however they
may also all be accomplished with SCSS.

### Nesting

In the syntax example above you will notice how selectors may be nested
inside of one another to create compound selectors. The nesting quickly
outlines identifiable selectors, however it is important not to go
overboard. Do **not** nest selectors for unapparent reasons or go
overboard nesting one selector under the prior one. Using specific
selectors without raising specificity is important.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | .portfolio                                                           |
|   |                                                                      |
| 2 | border: 1px solid #9799a7                                            |
|   |                                                                      |
| 3 | ul                                                                   |
|   |                                                                      |
| 4 | list-style: none                                                     |
|   |                                                                      |
| 5 | li                                                                   |
|   |                                                                      |
| 6 | float: left                                                          |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .portfolio {                                                         |
|   |                                                                      |
| 2 | border: 1px solid #9799a7;                                           |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .portfolio ul {                                                      |
|   |                                                                      |
| 5 | list-style: none;                                                    |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .portfolio li {                                                      |
|   |                                                                      |
| 8 | float: left;                                                         |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Nesting Properties

On top of nesting selectors it is also possible to nest properties. Some
of the most popular uses of this may be seen with font, margin, padding,
and border properties. As with the decision of SCSS versus Sass, this is
very much a personal decision. Many feel that shorthand values are fine
and breaking out values in this longer format is unnecessary. Ultimately
your decision is up to personal preference.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | div                                                                  |
|   |                                                                      |
| 2 | font:                                                                |
|   |                                                                      |
| 3 | family: Baskerville, Palatino, serif                                 |
|   |                                                                      |
| 4 | style: italic                                                        |
|   |                                                                      |
| 5 | weight: normal                                                       |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | div {                                                                |
|   |                                                                      |
| 2 | font-family: Baskerville, Palatino, serif;                           |
|   |                                                                      |
| 3 | font-style: italic;                                                  |
|   |                                                                      |
| 4 | font-weight: normal;                                                 |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Nested Media Queries

Individual media queries may also be nested inside of a selector,
changing property values based off a media condition.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | .container                                                           |
|   |                                                                      |
| 2 | width: 960px                                                         |
|   |                                                                      |
| 3 | &#0064;media screen and (max-width: 960px)                                |
|   |                                                                      |
| 4 | width: 100%                                                          |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .container {                                                         |
|   |                                                                      |
| 2 | width: 960px;                                                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | &#0064;media screen and (max-width: 960px) {                              |
|   |                                                                      |
| 5 | .container {                                                         |
|   |                                                                      |
| 6 | width: 100%;                                                         |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Parent Selector

Sass provides a way to add styles to a previous selector with the use of
the parent selector, implemented by using an ampersand, &. Most commonly
the parent selector is used in conjunction with a pseudo class, such
as :hover, however it doesn't have to be. Additionally the parent
selector could be used to bind additional selectors to its parent, such
as &.featured.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | a                                                                    |
|   |                                                                      |
| 2 | color: #0087cc                                                       |
|   |                                                                      |
| 3 | &:hover                                                              |
|   |                                                                      |
| 4 | color: #ff7b29                                                       |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | a {                                                                  |
|   |                                                                      |
| 2 | color: #0087cc;                                                      |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | a:hover {                                                            |
|   |                                                                      |
| 5 | color: #ff7b29;                                                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Parent Key Selector

The parent selector may also be used as the key selector, adding
qualifying selectors to make compound selectors. There are an abundance
of ways to use the parent selector as the key selector but perhaps one
of the most beneficial is inside of feature detection.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | .btn                                                                 |
|   |                                                                      |
| 2 | background: linear-gradient(#fff, #9799a7)                           |
|   |                                                                      |
| 3 | .no-cssgradients &                                                   |
|   |                                                                      |
| 4 | background: url(&quot;gradient.png&quot;) 0 0 repeat-x                       |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .btn {                                                               |
|   |                                                                      |
| 2 | background: linear-gradient(#fff, #9799a7);                          |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .no-cssgradients .btn {                                              |
|   |                                                                      |
| 5 | background: url(&quot;gradient.png&quot;) 0 0 repeat-x;                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Comments

Sass handles comments very similar to that of Haml. The standard CSS
syntax, /&ast; &#8230; &ast;/, for comments works as intended within Sass however
there is also a syntax for silent comments to completely remove a
comment or lines of code from being compiled.

The syntax for silent comments is two forward slashes, //, and any
content on that line or nested below it will be omitted from
computation. Notice in the example below how the // Omitted comment line
is not rendered in the compiled CSS.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | /&ast; Normal comment &ast;/                                               |
|   |                                                                      |
| 2 | div                                                                  |
|   |                                                                      |
| 3 | background: #333                                                     |
|   |                                                                      |
| 4 | // Omitted comment                                                   |
|   |                                                                      |
| 5 | strong                                                               |
|   |                                                                      |
| 6 | display: block                                                       |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | /&ast; Normal comment &ast;/                                               |
|   |                                                                      |
| 2 | div {                                                                |
|   |                                                                      |
| 3 | background: #333;                                                    |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | strong {                                                             |
|   |                                                                      |
| 6 | display: block;                                                      |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Variables

Variables are one of the more sought after features of CSS that Sass
provides. With Sass you can define variables and then reuse them as
necessary.

Variables are defined with a dollar sign, &#36;, followed by the variable
name. Between the variable name and value is a colon followed by an
empty space, such as &#36;font-base: 1em. As for the value of the variable,
it may be a number, string, color, boolean, null, or a list of values
separated by spaces or commas.

### **Sass**

+---+----------------------------------------------------------------------+
| 1 | &#36;font-base: 1em                                                     |
|   |                                                                      |
| 2 | &#36;serif: &quot;Helvetica Neue&quot;, Arial, &quot;Lucida Grande&quot;, sans-serif    |
|   |                                                                      |
| 3 | p                                                                    |
|   |                                                                      |
| 4 | font: &#36;font-base &#36;serif                                            |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | p {                                                                  |
|   |                                                                      |
| 2 | font: 1em &quot;Helvetica Neue&quot;, Arial, &quot;Lucida Grande&quot;, sans-serif;  |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Variable Interpolation

For the most part variables may be used anywhere inside of a Sass
document. However, they may occasionally need to be interpolated using
the syntax. A few instances of where variables need to be interpolated
include when being used in a class name, property name, or inside a
string of plain text.

### **Sass**

+---+----------------------------------------------------------------------+
| 1 | &#36;location: chicago                                                  |
|   |                                                                      |
| 2 | &#36;offset: left                                                       |
|   |                                                                      |
| 3 | .#{&#36;location}                                                       |
|   |                                                                      |
| 4 | #{&#36;offset}: 20px                                                    |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .chicago {                                                           |
|   |                                                                      |
| 2 | left: 20px;                                                          |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Calculations

Sass also has the ability to do calculations in a variety of different
manners. Calculations can handle most problems, such as addition,
subtraction, division, multiplication, and rounding.

Addition can be done by using the plus sign, +, and may be completed
with or without units of measurement. When done with units, the unit
tied to the first number in the equation is the unit that will be used
in the computed value. For example, ten pixels plus one inch will equal
106 pixels. Subtraction is handled the same way as addition but with the
minus sign, -, instead.

Multiplication is completed with the asterisk sign, &ast;, however only one
of the numbers, if any, may include a unit of measurement. Using the
percent sign, %, will return the remainder of the two numbers upon being
divided, and as with multiplication, only allows one number, if any, to
have a unit.

### **Sass**

+---+----------------------------------------------------------------------+
| 1 | width: 40px + 6                                                      |
|   |                                                                      |
| 2 | width: 40px - 6                                                      |
|   |                                                                      |
| 3 | width: 40px &ast; 6                                                     |
|   |                                                                      |
| 4 | width: 40px % 6                                                      |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | width: 46px;                                                         |
|   |                                                                      |
| 2 | width: 34px;                                                         |
|   |                                                                      |
| 3 | width: 240px;                                                        |
|   |                                                                      |
| 4 | width: 4px;                                                          |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Division

Division is a bit trickier in Sass as the forward slash, /, used to
perform division is already used in some CSS property values. Generally
speaking, division will take place when any part of the value uses a
variable, if the value is wrapped in parentheses, or if the value is
used as part of another equation.

When using one unit of measurement in division the value will reside in
that unit. When using two units of measurement, however, the resulting
value will be unitless.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | width: 100px / 10                                                    |
|   |                                                                      |
| 2 | width: (100px / 10)                                                  |
|   |                                                                      |
| 3 | width: (100px / 10px)                                                |
|   |                                                                      |
| 4 | &#36;width: 100px                                                       |
|   |                                                                      |
| 5 | width: &#36;width / 10                                                  |
|   |                                                                      |
| 6 | width: 5px - 100px / 10                                              |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | width: 100px/10;                                                     |
|   |                                                                      |
| 2 | width: 10px;                                                         |
|   |                                                                      |
| 3 | width: 10;                                                           |
|   |                                                                      |
| 4 | width: 10px;                                                         |
|   |                                                                      |
| 5 | width: -5px;                                                         |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Detailed Math

As one may expect, Sass is also capable of combining multiple math
operations. Sass also recognizes which operations to execute first based
on the use of parentheses.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#36;grid: 16                                                           |
|   |                                                                      |
| 2 | &#36;column: 40px                                                       |
|   |                                                                      |
| 3 | &#36;gutter: 20px                                                       |
|   |                                                                      |
| 4 | &#36;container: (&#36;column &ast; &#36;grid) + (&#36;gutter &ast; &#36;grid)             |
|   |                                                                      |
| 5 | width: &#36;container                                                   |
|   |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | width: 960px;                                                        |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Number Functions

By default Sass includes a handful of [[built in
functions]{.underline}](https://sass-lang.com/documentation/modules/math),
many of which are used to manipulate number values as wished.

The percentage() function turns a value into a percentage.
The round() function rounds a value to the closest whole number,
defaulting to rounding up where necessary. The ceil() function rounds a
value up to the closest whole number, and the floor() function rounds a
value down to the closest whole number. Lastly, the abs() function finds
the absolute value of a given number.

-   percentage()

-   round()

-   ceil()

-   floor()

-   abs()

**Sass**

+---+----------------------------------------------------------------------+
| 1 | width: percentage(2.5)                                               |
|   |                                                                      |
| 2 | width: round(2.5px)                                                  |
|   |                                                                      |
| 3 | width: ceil(2.5px)                                                   |
|   |                                                                      |
| 4 | width: floor(2.5px)                                                  |
|   |                                                                      |
| 5 | width: abs(-2.5px)                                                   |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | width: 250%;                                                         |
|   |                                                                      |
| 2 | width: 3px;                                                          |
|   |                                                                      |
| 3 | width: 3px;                                                          |
|   |                                                                      |
| 4 | width: 2px;                                                          |
|   |                                                                      |
| 5 | width: 2.5px;                                                        |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Color

Sass provides quite a bit of assistance in working with colors,
providing a handful of different features to alter and manipulate
colors. One of the more popular color features in Sass is the ability to
change a hexadecimal color, or variable, and convert it into an RGBa
value.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | color: rgba(#8ec63f, .25)                                            |
|   |                                                                      |
| 2 | &#36;green: #8ec63f                                                     |
|   |                                                                      |
| 3 | color: rgba(&#36;green, .25)                                            |
|   |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | color: rgba(142, 198, 63, .25);                                      |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Color Operations

On top of numbers, math may additionally be performed on colors using
addition, subtraction, multiplication, and division. These computations
are performed on the red, green, and blue components, changing them as
intended.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | color: #8ec63f + #666                                                |
|   |                                                                      |
| 2 | color: #8ec63f &ast; 2                                                  |
|   |                                                                      |
| 3 | color: rgba(142, 198, 63, .75) / rgba(255, 255, 255, .75)            |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | color: #f4ffa5;                                                      |
|   |                                                                      |
| 2 | color: #ffff7e;                                                      |
|   |                                                                      |
| 3 | color: rgba(0, 0, 0, .75);                                           |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Color Alterations

Using color operators to perform calculations is helpful but can be a
bit challenging as well. In this case color alterations may be a better
option. Color alterations provide the ability to inverse colors, find
complementary colors, mix colors together, or find the grayscale value
of a color.

-   invert()

-   complement()

-   mix()

-   grayscale()

**Sass**

+---+----------------------------------------------------------------------+
| 1 | color: invert(#8ec63f)                                               |
|   |                                                                      |
| 2 | color: complement(#8ec63f)                                           |
|   |                                                                      |
| 3 | color: mix(#8ec63f, #fff)                                            |
|   |                                                                      |
| 4 | color: mix(#8ec63f, #fff, 10%)                                       |
|   |                                                                      |
| 5 | color: grayscale(#8ec63f)                                            |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | color: #7139c0;                                                      |
|   |                                                                      |
| 2 | color: #773fc6;                                                      |
|   |                                                                      |
| 3 | color: #c6e29f;                                                      |
|   |                                                                      |
| 4 | color: #f3f9eb;                                                      |
|   |                                                                      |
| 5 | color: #838383;                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### HSLa Color Alterations

HSLa color alterations take things a step further, adding in even more
alterations. Some of the more popular HSLa color alterations
include lighten(), darken(), saturate(), and desaturate().

-   lighten()

-   darken()

-   saturate()

-   desaturate()

-   adjust-hue()

-   fade-in()

-   fade-out()

**Sass**

+---+----------------------------------------------------------------------+
| 1 | color: lighten(#8ec63f, 50%)                                         |
|   |                                                                      |
| 2 | color: darken(#8ec63f, 30%)                                          |
|   |                                                                      |
| 3 | color: saturate(#8ec63f, 75%)                                        |
|   |                                                                      |
| 4 | color: desaturate(#8ec63f, 25%)                                      |
|   |                                                                      |
| 5 | color: adjust-hue(#8ec63f, 30)                                       |
|   |                                                                      |
| 6 | color: adjust-hue(#8ec63f, -30)                                      |
|   |                                                                      |
| 7 | color: fade-in(rgba(142, 198, 63, 0), .4)                            |
|   |                                                                      |
| 8 | color: fade-out(#8ec63f, .4)                                         |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | color: white;                                                        |
|   |                                                                      |
| 2 | color: #3b5319;                                                      |
|   |                                                                      |
| 3 | color: #98ff06;                                                      |
|   |                                                                      |
| 4 | color: #89a75e;                                                      |
|   |                                                                      |
| 5 | color: #4ac63f;                                                      |
|   |                                                                      |
| 6 | color: #c6bb3f;                                                      |
|   |                                                                      |
| 7 | color: rgba(142, 198, 63, 0.4);                                      |
|   |                                                                      |
| 8 | color: rgba(142, 198, 63, 0.6);                                      |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Color Manipulation

Outside of altering colors Sass can also directly manipulate colors.
Manipulating colors provides the most control over how to finely tune
specific color properties. With this control also comes complexity,
which is why color manipulations are a bit less common than color
alterations.

-   change-color() --- Set any property of a color\
    &#36;color, &lbrack;&#36;red&rbrack;, &lbrack;&#36;green&rbrack;, &lbrack;&#36;blue&rbrack;, &lbrack;&#36;hue&rbrack;,
    &lbrack;&#36;saturation&rbrack;, &lbrack;&#36;lightness&rbrack;, &lbrack;&#36;alpha&rbrack;

-   adjust-color() --- Incrementally manipulate any property of a color\
    &#36;color, &lbrack;&#36;red&rbrack;, &lbrack;&#36;green&rbrack;, &lbrack;&#36;blue&rbrack;, &lbrack;&#36;hue&rbrack;,
    &lbrack;&#36;saturation&rbrack;, &lbrack;&#36;lightness&rbrack;, &lbrack;&#36;alpha&rbrack;

-   scale-color() --- Fluidly scale any percentage based on property of
    a color\
    &#36;color, &lbrack;&#36;red&rbrack;, &lbrack;&#36;green&rbrack;, &lbrack;&#36;blue&rbrack;, &lbrack;&#36;saturation&rbrack;,
    &lbrack;&#36;lightness&rbrack;, &lbrack;&#36;alpha&rbrack;

**Sass**

+---+----------------------------------------------------------------------+
| 1 | color: change-color(#8ec63f, &#36;red: 60, &#36;green: 255)                |
|   |                                                                      |
| 2 | color: adjust-color(#8ec63f, &#36;hue: 300, &#36;lightness: 50%)           |
|   |                                                                      |
| 3 | color: scale-color(#8ec63f, &#36;lightness: 25%, &#36;alpha: 30%)          |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | color: #3cff3f;                                                      |
|   |                                                                      |
| 2 | color: white;                                                        |
|   |                                                                      |
| 3 | color: #aad46f;                                                      |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Extends

Extends provide a way to easily share and reuse styles without having to
explicitly repeat code or use additional classes, providing a perfect
way to keep code modular. Both elements and class selectors may be used
as an extend, and there is even a placeholder selector built just for
extends.

Extends are established by using the @extend rule followed by the
selector to extend. Instead of duplicating the property and values, the
original selector receives and additional selector, that of which is
from the selector calling the extend.

In all, this provides a way to quickly reuse code without driving up
code weight. Additionally, extends parley nicely with OOCSS and SMACSS.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | .alert                                                               |
|   |                                                                      |
| 2 | border-radius: 10px                                                  |
|   |                                                                      |
| 3 | padding: 10px 20px                                                   |
|   |                                                                      |
| 4 | .alert-error                                                         |
|   |                                                                      |
| 5 | &#0064;extend .alert                                                      |
|   |                                                                      |
| 6 | background: #f2dede                                                  |
|   |                                                                      |
| 7 | color: #b94a48                                                       |
|   |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .alert,                                                              |
|   |                                                                      |
| 2 | .alert-error {                                                       |
|   |                                                                      |
| 3 | border-radius: 10px;                                                 |
|   |                                                                      |
| 4 | padding: 10px 20px;                                                  |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | .alert-error {                                                       |
|   |                                                                      |
| 7 | background: #f2dede;                                                 |
|   |                                                                      |
| 8 | color: #b94a48;                                                      |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Placeholder Selector Extend

To avoid building a bunch of unused classes purely for extends we can
use what is known as a placeholder selector. The placeholder selector is
initialized with a percentage sign, %, and is never directly compiled
into CSS. Instead, it is used to attach selectors to when it is called
with an extend. In the refined example below notice how
the .alert selector never makes its way into the CSS.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | %alert                                                               |
|   |                                                                      |
| 2 | border-radius: 10px                                                  |
|   |                                                                      |
| 3 | padding: 10px 20px                                                   |
|   |                                                                      |
| 4 | .alert-error                                                         |
|   |                                                                      |
| 5 | &#0064;extend %alert                                                      |
|   |                                                                      |
| 6 | background: #f2dede                                                  |
|   |                                                                      |
| 7 | color: #b94a48                                                       |
|   |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .alert-error {                                                       |
|   |                                                                      |
| 2 | border-radius: 10px;                                                 |
|   |                                                                      |
| 3 | padding: 10px 20px;                                                  |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | .alert-error {                                                       |
|   |                                                                      |
| 6 | background: #f2dede;                                                 |
|   |                                                                      |
| 7 | color: #b94a48;                                                      |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Element Selector Extend

As with classes, extends also work with standard element selectors too.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | h2                                                                   |
|   |                                                                      |
| 2 | color: #9c6                                                          |
|   |                                                                      |
| 3 | span                                                                 |
|   |                                                                      |
| 4 | text-decoration: underline                                           |
|   |                                                                      |
| 5 | .sub-heading                                                         |
|   |                                                                      |
| 6 | &#0064;extend h2                                                          |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | h2, .sub-heading {                                                   |
|   |                                                                      |
| 2 | color: #9c6;                                                         |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | h2 span, .sub-heading span {                                         |
|   |                                                                      |
| 5 | text-decoration: underline;                                          |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Mixins

Mixins provide a way to easily template properties and values, then
share them amongst different selectors. Mixins differ from extends as
mixins allow arguments to be passed in where extends are fixed values.

Mixins are identified using the @mixin rule followed by any potential
arguments, then any styles are outlined below the rule. To call a mixin
from within a selector use the plus sign, +, followed by the name of the
mixin and any desired argument values if needed.

It is worth nothing that SCSS handles mixins a bit different. Instead of
using a plus sign to call a mixin SCSS use an @include rule.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#0064;mixin btn(&#36;color, &#36;color-hover)                                  |
|   |                                                                      |
| 2 | color: &#36;color                                                       |
|   |                                                                      |
| 3 | &:hover                                                              |
|   |                                                                      |
| 4 | color: &#36;color-hover                                                 |
|   |                                                                      |
| 5 | .btn                                                                 |
|   |                                                                      |
| 6 | +btn(&#36;color: #fff, &#36;color-hover: #9799a7)                          |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .btn {                                                               |
|   |                                                                      |
| 2 | color: #fff;                                                         |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .btn:hover {                                                         |
|   |                                                                      |
| 5 | color: #9799a7;                                                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Default Arguments

Using the same example from above we can also specify default argument
values, which may be over written if wished.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#0064;mixin btn(&#36;color: #fff, &#36;color-hover: #9799a7)                   |
|   |                                                                      |
| 2 | color: &#36;color                                                       |
|   |                                                                      |
| 3 | &:hover                                                              |
|   |                                                                      |
| 4 | color: &#36;color-hover                                                 |
|   |                                                                      |
| 5 | .btn                                                                 |
|   |                                                                      |
| 6 | +btn(&#36;color-hover: #9799a7)                                         |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .btn {                                                               |
|   |                                                                      |
| 2 | color: #fff;                                                         |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .btn:hover {                                                         |
|   |                                                                      |
| 5 | color: #9799a7;                                                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Variable Arguments

When one or more values need to be passed to an argument the variable
name may end with &#8230; inside of the mixin. In the example below with
box shadows we can pass in comma separated values to the mixin.

+---+----------------------------------------------------------------------+
| 1 | &#0064;mixin box-shadow(&#36;shadow&#8230;)                                     |
|   |                                                                      |
| 2 | -webkit-box-shadow: &#36;shadow                                         |
|   |                                                                      |
| 3 | -moz-box-shadow: &#36;shadow                                            |
|   |                                                                      |
| 4 | box-shadow: &#36;shadow                                                 |
|   |                                                                      |
| 5 | .shadows                                                             |
|   |                                                                      |
| 6 | +box-shadow(0 1px 2px #cecfd5, inset 0 0 5px #cecfd5)                |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .shadows {                                                           |
|   |                                                                      |
| 2 | -moz-box-shadow: 0 1px 2px #cecfd5, inset 0 0 5px #cecfd5;           |
|   |                                                                      |
| 3 | -webkit-box-shadow: 0 1px 2px #cecfd5, inset 0 0 5px #cecfd5;        |
|   |                                                                      |
| 4 | box-shadow: 0 1px 2px #cecfd5, inset 0 0 5px #cecfd5;                |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Imports

One of nicest parts of Sass is its ability to import
multiple .scss or .sass files and condense them into one single file.
Condensing all of the files into one allows for multiple stylesheets to
be used for better organization without the worry of numerous HTTP
request.

Instead of referencing all of the different stylesheets within an HTML
document only reference the one Sass file importing all of the other
stylesheets.

In the following examples, all three
files &#0095;normalize.sass, &#0095;grid.sass, and &#0095;typography.sass are all
compiled into one file. In the event that the Sass file importing all
the other files is named styles.sass, and it is compiled
into styles.css, then only styles.css needs to be referenced within the
HTML document.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#0064;import &quot;normalize&quot;                                               |
|   |                                                                      |
| 2 | &#0064;import &quot;grid&quot;, &quot;typography&quot;                                    |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;link href=&quot;styles.css&quot; rel=&quot;stylesheet&quot;&gt;                      |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Loops & Conditionals

For a bit more intricate styling Sass supports different control
directives. Its important to understand these directives are not
intended for everyday styling but for creating detailed mixins and
helpers. Many of these will look familiar as they are borrowed from
other programming languages.

### Operators

Some loops and conditionals will require operators to determine their
behavior, of which can be broken down into relational and comparison
operators. Relational operators looks at the relationship between two
entities, while comparison operators determine equality or different
between to entities.

-   &lt;\
    Less than

-   &gt;\
    Greater than

-   ==\
    Equal to

-   &lt;=\
    Less than or equal to

-   &gt;=\
    Greather than or equal to

-   !=\
    Not equal to

+---+----------------------------------------------------------------------+
| 1 | // Relational Operators                                              |
|   |                                                                      |
| 2 | 6 &lt; 10 // true                                                      |
|   |                                                                      |
| 3 | 4 &lt;= 60 // true                                                     |
|   |                                                                      |
| 4 | 8 &gt; 2 // true                                                       |
|   |                                                                      |
| 5 | 10 &gt;= 10 // true                                                    |
|   |                                                                      |
| 6 | // Comparison Operators                                              |
|   |                                                                      |
| 7 | #fff == white // true                                                |
|   |                                                                      |
| 8 | 10 + 30 == 40 // true                                                |
|   |                                                                      |
| 9 | normal != bold // true                                               |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### If Function

The @if rule test an expressions then loads the styles beneath that
expression should it return anything other than false or null. The
initial if statement may be proceeded by several else if statements and
one else statement. Once a statement is successful identified the styles
directly tied to it will be applied.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#36;shay: awesome                                                      |
|   |                                                                      |
| 2 | .shay                                                                |
|   |                                                                      |
| 3 | &#0064;if &#36;shay == awesome                                               |
|   |                                                                      |
| 4 | background: #ff7b29                                                  |
|   |                                                                      |
| 5 | &#0064;else if &#36;shay == cool                                             |
|   |                                                                      |
| 6 | background: #0087cc                                                  |
|   |                                                                      |
| 7 | &#0064;else                                                               |
|   |                                                                      |
| 8 | background: #333                                                     |
|   |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .shay {                                                              |
|   |                                                                      |
| 2 | background: #ff7b29;                                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### For Loop

The @for rule outputs different sets of styles based off of a counter
variable. There are two different forms available for for loops, those
being to and through. The first, @for &#36;i from 1 to 3 for example, will
output styles up to, but not including, 3. The other form, @for &#36;i from
1 through 3, will output styles up to, and including, 3.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#0064;for &#36;col from 1 to 6                                              |
|   |                                                                      |
| 2 | .col-#{&#36;col}                                                        |
|   |                                                                      |
| 3 | width: 40px &ast; &#36;col                                                 |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .col-1 {                                                             |
|   |                                                                      |
| 2 | width: 40px;                                                         |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .col-2 {                                                             |
|   |                                                                      |
| 5 | width: 80px;                                                         |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .col-3 {                                                             |
|   |                                                                      |
| 8 | width: 120px;                                                        |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | .col-4 {                                                             |
| 0 |                                                                      |
|   | width: 160px;                                                        |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 | .col-5 {                                                             |
| 2 |                                                                      |
|   | width: 200px;                                                        |
| 1 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Each Loop

Simply enough, the @each rule returns styles for each item in a list.
List may include multiple comma separated items.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#0064;each &#36;class in uxd, rails, html, css                              |
|   |                                                                      |
| 2 | .#{&#36;class}-logo                                                     |
|   |                                                                      |
| 3 | background: url(&quot;/img/#{&#36;class}.jpg&quot;)                             |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | .uxd-logo {                                                          |
|   |                                                                      |
| 2 | background: url(&quot;/img/uxd.jpg&quot;);                                   |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .rails-logo {                                                        |
|   |                                                                      |
| 5 | background: url(&quot;/img/rails.jpg&quot;);                                 |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .html-logo {                                                         |
|   |                                                                      |
| 8 | background: url(&quot;/img/html.jpg&quot;);                                  |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | .css-logo {                                                          |
| 0 |                                                                      |
|   | background: url(&quot;/img/css.jpg&quot;);                                   |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### While Loop

The @while rule repeatedly returns styles until the statement becomes
false. The directive accepts a handful of different operators and the
counter variable can be finely controlled allowing for precise looping.

**Sass**

+---+----------------------------------------------------------------------+
| 1 | &#36;heading: 1                                                         |
|   |                                                                      |
| 2 | &#0064;while &#36;heading &lt;= 6                                              |
|   |                                                                      |
| 3 | h#{&#36;heading}                                                        |
|   |                                                                      |
| 4 | font-size: 2em - (&#36;heading &ast; .25em)                                |
|   |                                                                      |
| 5 | &#36;heading: &#36;heading + 1                                             |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**Compiled CSS**

+---+----------------------------------------------------------------------+
| 1 | h1 {                                                                 |
|   |                                                                      |
| 2 | font-size: 1.75em;                                                   |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | h2 {                                                                 |
|   |                                                                      |
| 5 | font-size: 1.5em;                                                    |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | h3 {                                                                 |
|   |                                                                      |
| 8 | font-size: 1.25em;                                                   |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | h4 {                                                                 |
| 0 |                                                                      |
|   | font-size: 1em;                                                      |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 | h5 {                                                                 |
| 2 |                                                                      |
|   | font-size: 0.75em;                                                   |
| 1 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 1 | h6 {                                                                 |
| 4 |                                                                      |
|   | font-size: 0.5em;                                                    |
| 1 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Other Preprocessors

Haml and Sass are far from the only preprocessing languages available,
including JavaScript preprocessors as well. Some of the other popular
preprocessors
including [[Jade]{.underline}](http://jade-lang.com/), [[Slim]{.underline}](http://slim-lang.com/), [[LESS]{.underline}](http://lesscss.org/),
and [[CoffeeScript]{.underline}](http://coffeescript.org/).

In the interest of brevity Haml and Sass were the only preprocessors
covered in this lesson. They were also chosen because they are built
using Ruby and fit right into Ruby on Rails applications. They've also
got tremendous community support.

When it comes to choosing which, if any, preprocessor to use it is
important to consider what is best for your team and project. Projects
built in Node.js may likely better benefit from Jade. The most important
aspect to consider, though, is what your team is accustomed to using. Do
your research for each project and make the most educated decision.

### Resources & Links

-   [[Haml]{.underline}](http://haml.info/) --- HTML Abstraction Markup
    Language

-   [[Sass]{.underline}](http://sass-lang.com/) --- Syntactically
    Awesome Stylesheets

-   [[Haml Documentation
    Reference]{.underline}](http://haml.info/docs/yardoc/file.REFERENCE.html)

-   [[Sass Documentation
    Reference]{.underline}](https://sass-lang.com/documentation/)

-   [[Sass Playground]{.underline}](http://sassmeister.com/) via
    SassMeister

-   [[SassScript
    Function]{.underline}](https://sass-lang.com/documentation/modules) via
    Sass Documentation

[**Lesson 4** [Responsive Web
Design]{.underline}](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)
[**Lesson 6**
[jQuery]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/)

[Lesson 6]{.mark} jQuery

In this Lesson 6

**JAVASCRIPT**

-   [[JavaScript
    Intro]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#javascript)

-   [[jQuery
    Intro]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#jquery)

-   [[Selectors]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#selectors)

-   [[Traversing]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#traversing)

-   [[Manipulation]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#manipulation)

-   [[Events]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#events)

-   [[Effects]{.underline}](https://learn.shayhowe.com/advanced-html-css/jquery/#effects)

**SHARE**

In part of being a web designer or front end developer you will commonly
run into JavaScript, often referred to as JS, and jQuery. Within the top
10,000 websites JavaScript is used within [[over
92%]{.underline}](https://trends.builtwith.com/docinfo/Javascript) of
them, and jQuery is used within in [[over
63%]{.underline}](https://trends.builtwith.com/javascript/jQuery) of
them. Needless to say, they are fairly popular. You may even aspire
to [[write]{.underline}](http://jsforcats.com/) JavaScript or jQuery to
build your own behaviors at one point or another.

If you are asking what exactly are JavaScript and jQuery fear not, this
lesson gives a brief overview of JavaScript and then takes a look at
jQuery.

JavaScript Intro

[[JavaScript]{.underline}](https://developer.mozilla.org/en-US/docs/JavaScript/A_re-introduction_to_JavaScript) provides
the ability to add interactivity to a website, and help enrich the user
experience. HTML provides a page with **structure** and CSS provides a
page with **appearance**, JavaScript provide a page with **behavior**.

Like CSS, JavaScript should be saved in an external file with
the .js file extension, and then referenced within an HTML document
using the script element. Where the JavaScript reference is placed with
HTML depends on when it should be executed. Generally speaking, the best
place to reference JavaScript files is right before the
closing &lt;/body&gt; tag so that the JavaScript file is loaded after all of
the HTML has been parsed. However, at times, JavaScript is needed to
help render HTML and determine it's behavior, thus may be referenced
within a documents head.

+---+----------------------------------------------------------------------+
| 1 | &lt;script src=&quot;script.js&quot;&gt;&lt;/script&gt;                              |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Values & Variables

Part of the fundamentals of JavaScript include values and variables.
Values, in general, are the different types of values that JavaScript
will recognize, while variables are used to store and share these
values.

Values may include strings of text, true or false Booleans,
numbers, undefined, null, or other values such as functions or objects.

One popular way variables are defined is with the var keyword, followed
by the variable name, an equal sign (=), then the value, ending with a
semicolon (;). The variable name must begin with a letter, underscore
(&#0095;), or dollar sign (&#36;). Variables cannot begin with numbers, although
they may be used subsequently, and they cannot use hyphens whatsoever.
Additionally, JavaScript is case sensitive so letters
include a through z in both lower and uppercase.

The common convention around naming variables is to
use [[camelCase]{.underline}](https://en.wikipedia.org/wiki/CamelCase),
without the use of any dashes or underscores. camelCase consist of
combining words while removing spaces, capitalizing the beginning of
each new word except for the initial word. For
example, shay_is_awesome would more commonly named shayIsAwesome.

+---+----------------------------------------------------------------------+
| 1 | var theStarterLeague = 125;                                          |
|   |                                                                      |
| 2 | var food_truck = &#39;Coffee&#39;;                                         |
|   |                                                                      |
| 3 | var mixtape01 = true;                                                |
|   |                                                                      |
| 4 | var vinyl = &lbrack;&#39;Miles Davis&#39;, &#39;Frank Sinatra&#39;, &#39;Ray Charles&#39;&rbrack;; |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Statements

As a whole, JavaScript is a set of statements, of which are executed by
the browser in the sequence they are written. These statements provide
commands which determine the different behaviors to be taken. Statements
come in all different shapes and sizes, with multiple statements
separated with semicolons, ;. New statements should begin on a new line,
and indentation should be used when nesting statements for better
legibility, but is not required.

+---+----------------------------------------------------------------------+
| 1 | log(polaroid);                                                       |
|   |                                                                      |
| 2 | return(&#39;bicycle lane&#39;);                                            |
|   |                                                                      |
| 3 | alert(&#39;Congratulations, you &#39; + outcome);                          |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Functions

Adding to the fundamentals of JavaScript, it is important to take a look
at functions. Functions provide a way to perform a set of scripted
behaviors now, or saved for later, and depending on the function they
may even accept different arguments.

A function is defined by using the function keyword followed by the
function name, a list of commas separated arguments wrapped in
parentheses, if necessary, and then the JavaScript statement, or
statements, that defines the function enclosed in curly braces, {}.

+---+----------------------------------------------------------------------+
| 1 | function sayHello(name) {                                            |
|   |                                                                      |
| 2 | return(&#39;Hello &#39; + name);                                           |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Arrays

As you may have recognized, some values may be returned as an array.
Arrays include a way to store a list of items, or values. Arrays are
helpful for many reasons, one being the ability to be traversed with
different methods and operators. Additionally, depending on the
situation, arrays can be used to store, and return, a variety of
different values.

Generally speaking arrays are identified within square brackets, &lbrack;&rbrack;,
with comma separated items. The items start at 0 and increase from
there. When identifying the third item in a list it is actually
identified as &lbrack;2&rbrack;.

### Objects

JavaScript is also built on the foundation of objects, which are a
collection of key and value pairs. For example, there may be an object
named school which includes the keys, also known as
properties, name, location, students, and teachers, and their values.

In the example below the variable school is set up as an object to hold
multiple properties. Each property has a key and value. The entire
object is wrapped inside of curly braces, {}, with comma separated
properties, each having a key followed by a colon and value.

+---+----------------------------------------------------------------------+
| 1 | // Object                                                            |
|   |                                                                      |
| 2 | var school = {                                                       |
|   |                                                                      |
| 3 | name: &#39;The Starter League&#39;,                                        |
|   |                                                                      |
| 4 | location: &#39;Merchandise Mart&#39;,                                      |
|   |                                                                      |
| 5 | students: 120,                                                       |
|   |                                                                      |
| 6 | teachers: &lbrack;&#39;Jeff&#39;, &#39;Raghu&#39;, &#39;Carolyn&#39;, &#39;Shay&#39;&rbrack;             |
|   |                                                                      |
| 7 | };                                                                   |
|   |                                                                      |
| 8 | // Array                                                             |
|   |                                                                      |
| 9 | var school = &lbrack;&#39;Austin&#39;, &#39;Chicago&#39;, &#39;Portland&#39;&rbrack;;              |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

![Web Inspector Console](./3-25-24/media/image013.png){width="5.0in"
height="3.201388888888889in"}

Fig. 6

Using the developer tools built into the Chrome web browser, JavaScript
may be run from within the console.

### jQuery Intro

With a basic understanding of JavaScript and some of it's foundations,
it is time to take a look at jQuery. jQuery is an open source JavaScript
library written by John Resig that simplifies the interaction between
HTML, CSS, and JavaScript. Since 2006, when jQuery was released, it has
taken off, being used by websites and companies large and small.

What has made jQuery so popular is it's [[ease of
use]{.underline}](https://tutsplus.com/course/30-days-to-learn-jquery/),
with selections resembling CSS and a comprehensible separation of
behavior. The benefits of jQuery are massive, however for our purpose we
will only be considered about the ability to find elements and perform
actions with them.

### Getting Started with jQuery

The first step to using jQuery is to reference it from within a HTML
document. As previously mentioned with JavaScript, this is done using
the script element just before the closing &lt;/body&gt; tag. Since jQuery
is it's own library it is best to keep it separate from all the other
JavaScript being written.

When referencing jQuery there are a few options, specifically as whether
to use the minified or uncompressed version, and as whether to use a
content delivery network, CDN, such as [[Google hosted
libraries]{.underline}](https://developers.google.com/speed/libraries/devguide).
If the code being written is for a live, production environment it is
encouraged to use the minified version for better loading times.
Additionally, using a CDN like Google also helps with loading time, and
potential caching benefits.

+---+----------------------------------------------------------------------+
| 1 | &lt;script                                                             |
|   | src=&quot;//aja                                                          |
| 2 | x.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js&quot;&gt;&lt;/script&gt; |
|   |                                                                      |
| 3 | &lt;script src=&quot;script.js&quot;&gt;&lt;/script&gt;                              |
+===+======================================================================+
+---+----------------------------------------------------------------------+

In the code sample above, notice the second script element referencing a
second JavaScript file. All of the custom, handwritten JavaScript and
jQuery should be written in this file. Additionally, this file is
specifically placed after the jQuery file so that it may reference
jQuery functions already defined.

### Where is the leading http?

You may have noticed that there isn't a leading http within Google CDN
reference example above. The http has been omitted intentionally to
allow for both http and https connections. When working locally, without
the benefit of a web server, the leading http will need to be included
to prevent attempting to locate the file on the systems local disk
drive.

### jQuery Object

jQuery comes with it's own object, the dollar sign, &#36;, also known
as jQuery. The &#36; object is specifically made for selecting an element
and then returning that element node to perform an action on it. These
selections and actions should be written in a new file, referenced
outside of the actual jQuery library.

+---+----------------------------------------------------------------------+
| 1 | &#36;();                                                                |
|   |                                                                      |
| 2 | jQuery();                                                            |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Document Ready

Before trigging any jQuery to traverse and manipulate a page it is best
to wait until the DOM is finished loading. Fortunately jQuery has a
ready event, .ready(), which can be called when the HTML document is
ready to be altered. By placing all of our other custom written jQuery
inside of this function we can guarantee that it will not be executed
until the page has loaded and the DOM is ready.

+---+----------------------------------------------------------------------+
| 1 | &#36;(document).ready(function(event){                                  |
|   |                                                                      |
| 2 | // jQuery code                                                       |
|   |                                                                      |
| 3 | });                                                                  |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Selectors

As previously mentioned, one of the core concepts of jQuery is
to [[select
elements]{.underline}](http://api.jquery.com/category/selectors/) and
perform an action. jQuery has done a great job of making the task of
selecting an element, or elements, extremely easy by mimicking that of
CSS. On top of the general CSS selectors, jQuery has support for all of
the unique CSS3 selectors, which work regardless of which browser is
being used.

Invoking the jQuery object, &#36;(), containing a selector will return that
DOM node to manipulate it. The selector falls within the
parentheses, (&#39;&#8230;&#39;), and may select elements just like that of CSS.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;.feature&#39;); // Class selector                                  |
|   |                                                                      |
| 2 | &#36;(&#39;li strong&#39;); // Descendant selector                            |
|   |                                                                      |
| 3 | &#36;(&#39;em, i&#39;); // Multiple selector                                  |
|   |                                                                      |
| 4 | &#36;(&#39;a&lbrack;target=&quot;&#0095;blank&quot;&rbrack;&#39;); // Attribute selector               |
|   |                                                                      |
| 5 | &#36;(&#39;p:nth-child(2)&#39;); // Pseudo-class selector                     |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### This Selection Keyword

When working inside of a jQuery function you may want to select the
element in which was referenced inside of the original selector. In this
event the this keyword may be used to refer to the element selected in
the current handler.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;div&#39;).click(function(event){                                   |
|   |                                                                      |
| 2 | &#36;(this);                                                            |
|   |                                                                      |
| 3 | });                                                                  |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### jQuery Selection Filters

Should CSS selectors not be enough there are also
custom [[filters]{.underline}](http://api.jquery.com/category/selectors/jquery-selector-extensions/) built
into jQuery to help out. These filters are an extension to CSS3 and
provide more control over selecting an element or its relatives.

+---+--------------------------------------------------------------------+
| 1 | &#36;(&#39;div:has(strong)&#39;);                                           |
|   |                                                                    |
| 2 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

As they stand these filters may be used inside of the selector, however
not being native to the DOM they are a bit slow. The best results with
using these filters is accomplished by using the :filter() method, which
is part of the traversing feature in jQuery.

### Traversing

At times the general CSS selectors alone don't cut it and a little more
detailed control is desired. Fortunately jQuery provides a handful of
methods for traversing up and down the DOM tree, filtering and selecting
elements as necessary.

To get started with filtering elements inside the DOM a general
selection needs to be made, from which will be traversed from
relatively. In the example below the original selection finds all of
the div elements in the DOM, which are then filtered using
the .not() method. With this specific method all of the div elements
without a class of type or collection will be selected.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;div&#39;).not(&#39;.type, .collection&#39;);                             |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Chaining Methods

For even more control as to which elements are selected different
traversing methods may be chained together simply by using a dot
in-between them.

The code sample below uses both the .not() method and
the .parent() method. Combined together this will only select the parent
elements of div elements without a class of type or collection.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;div&#39;).not(&#39;.type, .collection&#39;).parent();                    |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Traversing Methods

jQuery has quite a
few [[traversing]{.underline}](http://api.jquery.com/category/traversing/) methods
available to use. In general, they all fall into three categories,
filtering, miscellaneous traversing, and DOM tree traversing. The
specific methods within each category may be seen below.

### Filtering

-   .eq()

-   .filter()

-   .first()

-   .has()

-   .is()

-   .last()

-   .map()

-   .not()

-   .slice()

### Miscellaneous Traversing

-   .add()

-   .andSelf()

-   .contents()

-   .end()

### DOM Tree Traversal

-   .children()

-   .closest()

-   .find()

-   .next()

-   .nextAll()

-   .nextUntil()

-   .offsetParent()

-   .parent()

-   .parents()

-   .parentsUntil()

-   .prev()

-   .prevAll()

-   .prevUntil()

-   .siblings()

### Manipulation

Selecting and traversing elements in the DOM is only part of what jQuery
offers, one other major part is what is possible with those elements
once found. One possibility is
to [[manipulate]{.underline}](http://api.jquery.com/category/manipulation/) these
elements, by either reading, adding, or changing attributes or styles.
Additionally, elements may be altered in the DOM, changing their
placement, removing them, adding new elements, and so forth. Overall the
options to manipulate elements are fairly vast.

### Getting & Setting

The manipulation methods to follow are most commonly used in one of two
directives, that being *getting* or *setting* information. Getting
information revolves around using a selector in addition with a method
to determine what piece of information is to be retrieved. Additionally,
the same selector and method may also be used to set a piece of
information.

+---+----------------------------------------------------------------------+
| 1 | // Gets the value of the alt attribute                               |
|   |                                                                      |
| 2 | &#36;(&#39;img&#39;).attr(&#39;alt&#39;);                                           |
|   |                                                                      |
| 3 | // Sets the value of the alt attribute                               |
|   |                                                                      |
| 4 | &#36;(&#39;img&#39;).attr(&#39;alt&#39;, &#39;Wild kangaroo&#39;);                        |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

In the examples and snippets to follow methods will primarily be used in
a setting mode, however they may also be able to be used in a getting
mode as well.

### Attribute Manipulation

One part of elements able to be inspected and manipulated are
attributes. A few options include the ability to add, remove, or change
an attribute or its value. In the examples below the .addClass() method
is used to add a class to all even list items, the .removeClass() method
is used to remove all classes from any paragraphs, and lastly
the .attr() method is used to find the value of the title attribute of
any abbr element and set it to Hello World.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;li:even&#39;).addClass(&#39;even-item&#39;);                             |
|   |                                                                      |
| 2 | &#36;(&#39;p&#39;).removeClass();                                             |
|   |                                                                      |
| 3 | &#36;(&#39;abbr&#39;).attr(&#39;title&#39;, &#39;Hello World&#39;);                       |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Attribute Manipulation Methods

-   .addClass()

-   .attr()

-   .hasClass()

-   .prop()

-   .removeAttr()

-   .removeClass()

-   .removeProp()

-   .toggleClass()

-   .val()

### Style Manipulation

On top of manipulating attributes, the style of an element may also be
manipulated using a variety of methods. When reading or setting the
height, width, or position of an element there are a handful of special
methods available, and for all other style manipulations
the .css() method can handle any CSS alterations.

The .css() method in particular may be used to set one property, or
many, and the syntax for each varies. To set one property, the property
name and value should each be in quotations and comma separated. To set
multiple properties, the properties should be nested inside of curly
brackets with the property name in camel case, removing any hyphens
where necessary, followed by a colon and then the quoted value. Each of
the property and value pairs need to be comma separated.

The height, width, or position methods all default to using pixel
values, however other units of measurement may be used. As seen below,
to change the unit of measurement identify the value then use a plus
sign followed by the quoted unit of measurement.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;h1 span&#39;).css(&#39;font-size&#39;, &#39;normal&#39;);                      |
|   |                                                                      |
| 2 | &#36;(&#39;div&#39;).css({                                                    |
|   |                                                                      |
| 3 | fontSize: &#39;13px&#39;,                                                  |
|   |                                                                      |
| 4 | background: &#39;#f60&#39;                                                 |
|   |                                                                      |
| 5 | });                                                                  |
|   |                                                                      |
| 6 | &#36;(&#39;header&#39;).height(200);                                          |
|   |                                                                      |
| 7 | &#36;(&#39;.extend&#39;).height(30 + &#39;em&#39;);                                 |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Style Manipulation Methods

-   .css()

-   .height()

-   .innerHeight()

-   .innerWidth()

-   .offset()

-   .outerHeight()

-   .outerWidth()

-   .position()

-   .scrollLeft()

-   .scrollTop()

-   .width()

### DOM Manipulation

Lastly, we are able to inspect and manipulate the DOM, changing the
placement of elements, adding and removing elements, as well as flat out
altering elements. The options here are deep and varied, allowing for
any potential changes to be made inside the DOM.

Each individual DOM manipulation method has it's own syntax but a few of
them are outlined below. The .prepend() method is adding a
new h3 element just inside any section, the .after() method is adding a
new em element just after the link, and the .text() method is replacing
the text of any h1 elements with the text Hello World.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;section&#39;).prepend(&#39;&lt;h3&gt;Featured&lt;/h3&gt;&#39;);                  |
|   |                                                                      |
| 2 | &#36;(&#39;a&lbrack;target=&quot;&#0095;blank&quot;&rbrack;&#39;).after(&#39;&lt;em&gt;New window.&lt;/em&gt;&#39;); |
|   |                                                                      |
| 3 | &#36;(&#39;h1&#39;).text(&#39;Hello World&#39;);                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### DOM Manipulation Methods

-   .after()

-   .append()

-   .appendTo()

-   .before()

-   .clone()

-   .detach()

-   .empty()

-   .html()

-   .insertAfter()

-   .insertBefore()

-   .prepend()

-   .prependTo()

-   .remove()

-   .replaceAll()

-   .replaceWith()

-   .text()

-   .unwrap()

-   .wrap()

-   .wrapAll()

-   .wrapInner()

### Events

One of the beauties of jQuery is the ability to easily add [[event
handlers]{.underline}](http://api.jquery.com/category/events/), which
are methods that are called only upon a specific event or action taking
place. For example, the method of adding a class to an element can be
set to only occur upon that element being clicked on.

Below is a standard selector, grabbing all of the list items.
The .click() event method is bound to the list item selector, setting up
an action to take place upon clicking any list item. Inside
the .click() event method is a function, which ensures any actions
inside the event method are to be executed. The parentheses directly
after the function are available to pass in parameters for the function,
in which the event object is used in this example.

Inside of the function is another selector with the .addClass() method
bound to it. Now, when a list item is clicked on that list item, via
the this keyword, receives the class of saved-item.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;li&#39;).click(function(event){                                    |
|   |                                                                      |
| 2 | &#36;(this).addClass(&#39;saved-item&#39;);                                   |
|   |                                                                      |
| 3 | });                                                                  |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Event Flexibility

The .click() event method, along with a handful of other event methods,
is actually a [[shorthand
method]{.underline}](http://jqfundamentals.com/chapter/events) which
uses the .on() method introduced in jQuery 1.7. The .on() method
provides quite a bit of flexibility, using automatic delegation for
elements that get added to the page dynamically.

Making use of the .on() method the first argument should be the native
event name while the second argument should be the event handler
function. Looking at the example from before, the .on() method is called
in place of the .click() method. Now the click event name is passed in
as the first argument inside the .on() method with the event handler
function staying the same as before.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;li&#39;).on(&#39;click&#39;, function(event){                            |
|   |                                                                      |
| 2 | &#36;(this).addClass(&#39;saved-item&#39;);                                   |
|   |                                                                      |
| 3 | });                                                                  |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Nesting Events

It is possible to have multiple event handlers and triggers, nesting one
inside another. As an example, below the .on() event method is passed
the hover argument, thus being called when hovering over any element
with the class of pagination. Upon calling the .on() event
the .click() event is called on the anchor with the up ID.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;.pagination&#39;).on(&#39;hover&#39;, function(event){                   |
|   |                                                                      |
| 2 | &#36;(&#39;a#up&#39;).click();                                                |
|   |                                                                      |
| 3 | });                                                                  |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Event Demo

Using an alert message as a demo, the following code snippets show how
to create an alert message and then removing that message based upon
clicking the close icon.

**HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;div class=&quot;notice-warning&quot;&gt;                                   |
|   |                                                                    |
| 2 | &lt;div class=&quot;notice-close&quot;&gt;&#215;&lt;/div&gt;                       |
|   |                                                                    |
| 3 | &lt;strong&gt;Warning!&lt;/strong&gt; I&#8217;m about to lose my cool.     |
|   |                                                                    |
| 4 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 5 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

**JavaScript**

+---+--------------------------------------------------------------------+
| 1 | &#36;(&#39;.notice-close&#39;).on(&#39;click&#39;, function(event){               |
|   |                                                                    |
| 2 | &#36;(&#39;.notice-warning&#39;).remove();                                  |
|   |                                                                    |
| 3 | });                                                                |
|   |                                                                    |
| 4 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Demo

### Event Methods

jQuery provides quite a few methods, all of which are based around
registering user behaviors as they interact with the browser. These
methods register quite a few events, most popularly, but not limited to,
browser, form, keyboard, and mouse events. The most popular of these
methods include:

### Browser Events

-   .resize()

-   .scroll()

### Document Loading

-   .ready()

### Event Handler Attachment

-   .off()

-   .on()

-   .one()

-   jQuery.proxy()

-   .trigger()

-   .triggerHandler()

-   .unbind()

-   .undelegate()

### Event Object

-   event.currentTarget

-   event.preventDefault()

-   event.stopPropagation()

-   event.target

-   event.type

### Form Events

-   .blur()

-   .change()

-   .focus()

-   .select()

-   .submit()

### Keyboard Events

-   .focusin()

-   .focusout()

-   .keydown()

-   .keypress()

-   .keyup()

### Mouse Events

-   .click()

-   .dblclick()

-   .focusin()

-   .focusout()

-   .hover()

-   .mousedown()

-   .mouseenter()

-   .mouseleave()

-   .mousemove()

-   .mouseout()

-   .mouseover()

-   .mouseup()

### Effects

Next to events, jQuery also provides a handful of customizable effects.
These effects come by the way of different methods, including event
methods for showing and hiding content, fading content in and out, or
sliding content up and down. All of these are ready to use methods and
may be customized as best see fit.

Each effect method has it's own syntax so it is best to reference the
jQuery [[effects
documentation]{.underline}](http://api.jquery.com/category/effects/) for
specific syntax around each method. Most commonly though, effects
generally accept a duration, easing, and the ability to specify a
callback function.

### jQuery CSS Animations

Custom animations of different CSS properties can be accomplished in
jQuery, although this is a little less relevant as CSS can now handle
animations itself. CSS animations offer better performance from a
browser processing standpoint and are preferred where possible. jQuery
animation effects, with the help of Modernizr, make for a perfect backup
solution to any browser not supporting CSS animations.

### Effect Duration

Using the .show() method as an example, the first parameter available to
optionally pass in to the method is the duration, which can be
accomplished using a keyword or milliseconds value. The
keyword slow defaults to 600 milliseconds, while the
keyword fast defaults to 200 milliseconds. Using a keyword value is
fine, but millisecond values may also be passed in directly. Keyword
values must be quoted while millisecond values do not.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;.error&#39;).show();                                               |
|   |                                                                      |
| 2 | &#36;(&#39;.error&#39;).show(&#39;slow&#39;);                                       |
|   |                                                                      |
| 3 | &#36;(&#39;.error&#39;).show(500);                                            |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Effect Easing

In addition to setting the duration in which an effect takes place the
easing, or speed at which an animation progresses at during different
times within the animation, may also be set. By default jQuery has two
keyword values for easing, the default value is swing with the
additional value being linear. The default swing value starts the
animation at a slow pace, picking up speed during the animation, and
then slows down again before completion. The linear value runs the
animation at one constant pace for the entire duration.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;.error&#39;).show(&#39;slow&#39;, &#39;linear&#39;);                           |
|   |                                                                      |
| 2 | &#36;(&#39;.error&#39;).show(500, &#39;linear&#39;);                                |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### jQuery UI

The two easing values that come with jQuery may be extend with the use
of different plug-ins, of which may offer additional values. One of the
most popular plug-ins is the [[jQuery
UI]{.underline}](http://jqueryui.com/) suite.

On top of new easing values jQuery UI also provides a handful other
interactions, effects, widgets, and other helpful resources worth taking
a look at.

### Effect Callback

When an animation is completed it is possible to run another function,
called a callback function. The callback function should be placed after
the duration or easing, if either exist. Inside this function new events
or effects may be placed, each following their own required syntax.

+---+----------------------------------------------------------------------+
| 1 | &#36;(&#39;.error&#39;).show(&#39;slow&#39;, &#39;linear&#39;, function(event){           |
|   |                                                                      |
| 2 | &#36;(&#39;.error .status&#39;).text(&#39;Continue&#39;);                           |
|   |                                                                      |
| 3 | });                                                                  |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Effect Syntax

As previously mentioned, each effect method has it's own syntax which
can be found in the jQuery [[effects
documentation]{.underline}](http://api.jquery.com/category/effects/).
The duration, easing, and callback parameters outlined here are common,
but not available on every method. It is best to review the syntax of a
method should you have any questions around it.

### Effects Demo

Taking the same events demo from above, the .remove() method is now used
as part of a callback function on the .fadeOut() method. Using
the .fadeOut() method allows for the alert message to gradually fade out
rather than quickly disappearing, then be removed from the DOM after the
animation is complete.

### **HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;div class=&quot;notice-warning&quot;&gt;                                   |
|   |                                                                    |
| 2 | &lt;div class=&quot;notice-close&quot;&gt;&#215;&lt;/div&gt;                       |
|   |                                                                    |
| 3 | &lt;strong&gt;Warning!&lt;/strong&gt; I&#8217;m about to lose my cool.     |
|   |                                                                    |
| 4 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 5 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

**JavaScript**

+---+-------------------------------------------------------------------+
| 1 | &#36;(&#39;.notice-close&#39;).on(&#39;click&#39;, function(event){              |
|   |                                                                   |
| 2 | &#36;(&#39;.notice-warning&#39;).fadeOut(&#39;slow&#39;, function(event){        |
|   |                                                                   |
| 3 | &#36;(this).remove();                                                |
|   |                                                                   |
| 4 | });                                                               |
|   |                                                                   |
| 5 | });                                                               |
|   |                                                                   |
| 6 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

### Demo

### Basic Effects

-   .hide()

-   .show()

-   .toggle()

### Custom Effects

-   .animate()

-   .clearQueue()

-   .delay()

-   .dequeue()

-   jQuery.fx.interval

-   jQuery.fx.off

-   .queue()

-   .stop()

### Fading Effects

-   .fadeIn()

-   .fadeOut()

-   .fadeTo()

-   .fadeToggle()

### Sliding Effects

-   .slideDown()

-   .slideToggle()

-   .slideUp()

### Slide Demo

**HTML**

+---+-------------------------------------------------------------------+
| 1 | &lt;div class=&quot;panel&quot;&gt;                                           |
|   |                                                                   |
| 2 | &lt;div class=&quot;panel-stage&quot;&gt;&lt;/div&gt;                             |
|   |                                                                   |
| 3 | &lt;a href=&quot;#&quot; class=&quot;panel-tab&quot;&gt;Open                          |
|   | &lt;span&gt;&#9660;&lt;/span&gt;&lt;/a&gt;                                    |
| 4 |                                                                   |
|   | &lt;/div&gt;                                                          |
| 5 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

**JavaScript**

+---+-------------------------------------------------------------------+
| 1 | &#36;(&#39;.panel-tab&#39;).on(&#39;click&#39;, function(event){                 |
|   |                                                                   |
| 2 | event.preventDefault();                                           |
|   |                                                                   |
| 3 | &#36;(&#39;.panel-stage&#39;).slideToggle(&#39;slow&#39;, function(event){       |
|   |                                                                   |
| 4 | if(&#36;(this).is(&#39;:visible&#39;)){                                    |
|   |                                                                   |
| 5 | &#36;(&#39;.panel-tab&#39;).html(&#39;Close &lt;span&gt;&#9650;&lt;/span&gt;&#39;);      |
|   |                                                                   |
| 6 | } else {                                                          |
|   |                                                                   |
| 7 | &#36;(&#39;.panel-tab&#39;).html(&#39;Open &lt;span&gt;&#9660;&lt;/span&gt;&#39;);       |
|   |                                                                   |
| 8 | }                                                                 |
|   |                                                                   |
| 9 | });                                                               |
|   |                                                                   |
| 1 | });                                                               |
| 0 |                                                                   |
|   |                                                                   |
| 1 |                                                                   |
| 1 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

Demo

Tabs Demo

**HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;ul class=&quot;tabs-nav&quot;&gt;                                          |
|   |                                                                    |
| 2 | &lt;li&gt;&lt;a href=&quot;#tab-1&quot;&gt;Features&lt;/a&gt;&lt;/li&gt;                   |
|   |                                                                    |
| 3 | &lt;li&gt;&lt;a href=&quot;#tab-2&quot;&gt;Details&lt;/a&gt;&lt;/li&gt;                    |
|   |                                                                    |
| 4 | &lt;/ul&gt;                                                            |
|   |                                                                    |
| 5 | &lt;div class=&quot;tabs-stage&quot;&gt;                                       |
|   |                                                                    |
| 6 | &lt;div id=&quot;tab-1&quot;&gt;&#8230;&lt;/div&gt;                                   |
|   |                                                                    |
| 7 | &lt;div id=&quot;tab-2&quot;&gt;&#8230;&lt;/div&gt;                                   |
|   |                                                                    |
| 8 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 9 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

**JavaScript**

+---+--------------------------------------------------------------------+
| 1 | // Show the first tab by default                                   |
|   |                                                                    |
| 2 | &#36;(&#39;.tabs-stage div&#39;).hide();                                    |
|   |                                                                    |
| 3 | &#36;(&#39;.tabs-stage div:first&#39;).show();                              |
|   |                                                                    |
| 4 | &#36;(&#39;.tabs-nav li:first&#39;).addClass(&#39;tab-active&#39;);               |
|   |                                                                    |
| 5 | // Change tab class and display content                            |
|   |                                                                    |
| 6 | &#36;(&#39;.tabs-nav a&#39;).on(&#39;click&#39;, function(event){                 |
|   |                                                                    |
| 7 | event.preventDefault();                                            |
|   |                                                                    |
| 8 | &#36;(&#39;.tabs-nav li&#39;).removeClass(&#39;tab-active&#39;);                  |
|   |                                                                    |
| 9 | &#36;(this).parent().addClass(&#39;tab-active&#39;);                        |
|   |                                                                    |
| 1 | &#36;(&#39;.tabs-stage div&#39;).hide();                                    |
| 0 |                                                                    |
|   | &#36;(&#36;(this).attr(&#39;href&#39;)).show();                                |
| 1 |                                                                    |
| 1 | });                                                                |
|   |                                                                    |
| 1 |                                                                    |
| 2 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 3 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 4 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Demo

### Resources & Links

-   [[JavaScript For Cats]{.underline}](http://jsforcats.com/)

-   [[A Re-introduction to
    JavaScript]{.underline}](https://developer.mozilla.org/en-US/docs/JavaScript/A_re-introduction_to_JavaScript) via
    Mozilla Developer Network

-   [[30 Days to Learn
    jQuery]{.underline}](https://tutsplus.com/course/30-days-to-learn-jquery/) via
    Tuts+ Premium

-   [[Google Hosted
    Libraries]{.underline}](https://developers.google.com/speed/libraries/devguide)

-   [[jQuery Documentation]{.underline}](http://docs.jquery.com/)

-   [[jQuery Fundamentals]{.underline}](http://jqfundamentals.com/) via
    Bocoup

-   [[jQuery UI]{.underline}](http://jqueryui.com/)

[**Lesson 5**
[Preprocessors]{.underline}](https://learn.shayhowe.com/advanced-html-css/preprocessors/)
[**Lesson 7**
[Transforms]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/)

[Lesson 7]{.mark} Transforms

In this Lesson 7

GitlabGitLab is the most comprehensive AI-powered DevSecOps Platform.
Software. Faster.

**CSS**

-   [[Transform
    Syntax]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#transform-syntax)

-   [[2D
    Transforms]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#two-dimensional-transforms)

-   [[Combining
    Transforms]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#combining-transforms)

-   [[Transform
    Origin]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#transform-origin)

-   [[Perspective]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#perspective)

-   [[3D
    Transforms]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#three-dimensional-transforms)

-   [[Transform
    Style]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#transform-style)

-   [[Backface
    Visibility]{.underline}](https://learn.shayhowe.com/advanced-html-css/css-transforms/#backface-visibility)

**SHARE**

With CSS3 came new ways to position and alter elements. Now general
layout techniques can be revisited with alternative ways to size,
position, and change elements. All of these new techniques are made
possible by the transform property.

The transform property comes in two different settings, two-dimensional
and three-dimensional. Each of these come with their own individual
properties and values.

Within this lesson we'll take a look at both two-dimensional and
three-dimensional transforms. Generally speaking, browser support for
the transform property isn't great, but it is getting better every day.
For the best support vendor prefixes are encouraged, however you may
need to download the nightly version
of [[Chrome]{.underline}](https://tools.google.com/dlpage/chromesxs/) to
see all of these transforms in action.

### Transform Syntax

The actual syntax for the transform property is quite simple, including
the transform property followed by the value. The value specifies the
transform type followed by a specific amount inside parentheses.

+---+----------------------------------------------------------------------+
| 1 | div {                                                                |
|   |                                                                      |
| 2 | -webkit-transform: scale(1.5);                                       |
|   |                                                                      |
| 3 | -moz-transform: scale(1.5);                                          |
|   |                                                                      |
| 4 | -o-transform: scale(1.5);                                            |
|   |                                                                      |
| 5 | transform: scale(1.5);                                               |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Notice how the transform property includes multiple vendor prefixes to
gain the best support across all browsers. The un-prefixed declaration
comes last to overwrite the prefixed versions, should a browser fully
support the transform property.

In the interest of brevity, the remainder of this lesson will not
include vendor prefixes. They are, however, strongly encouraged for any
code in a production environment. Over time we will be able to remove
these prefixes, however keeping them in is the safest approach for the
time being.

### 2D Transforms

Elements may be distorted, or transformed, on both a two-dimensional
plane or a three-dimensional plane. Two-dimensional transforms work on
the x and y axes, known as horizontal and vertical axes.
Three-dimensional transforms work on both the x and y axes, as well as
the z axis. These three-dimensional transforms help define not only the
length and width of an element, but also the depth. We'll start by
discussing how to [[transform
elements]{.underline}](http://www.css3files.com/transform/) on a
two-dimensional plane, and then work our way into three-dimensional
transforms.

### 2D Rotate

The transform property accepts a handful of different values.
The rotate value provides the ability to rotate an element
from 0 to 360 degrees. Using a positive value will rotate an element
clockwise, and using a negative value will rotate the element
counterclockwise. The default point of rotation is the center of the
element, 50% 50%, both horizontally and vertically. Later we will
discuss how you can change this default point of rotation.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: rotate(20deg);                                            |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: rotate(-55deg);                                           |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Rotate Demo

The gray box behind the rotated element symbolizes the original position
of the element. Additionally, upon hover the box will rotate 360 degrees
horizontally. As the lesson progresses, keep an eye out for the gray box
within each demonstration as a reference to the element's original
position and the horizontal rotation to help demonstrate an elements
alteration and depth.

### 2D Scale

Using the scale value within the transform property allows you to change
the appeared size of an element. The default scale value is 1, therefore
any value between .99 and .01 makes an element appear smaller while any
value greater than or equal to 1.01 makes an element appear larger.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: scale(.75);                                               |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: scale(1.25);                                              |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Scale Demo

It is possible to scale only the height or width of an element using
the scaleX and scaleY values. The scaleX value will scale the width of
an element while the scaleY value will scale the height of an element.
To scale both the height and width of an element but at different sizes,
the x and y axis values may be set simultaneously. To do so, use
the scale transform declaring the x axis value first, followed by a
comma, and then the y axis value.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box-3&quot;&gt;Box 3&lt;/figure&gt;                           |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: scaleX(.5);                                               |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: scaleY(1.15);                                             |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box-3 {                                                             |
|   |                                                                      |
| 8 | transform: scale(.5, 1.15);                                          |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Multiple Scaling Demo

### 2D Translate

The translate value works a bit like that of relative positioning,
pushing and pulling an element in different directions without
interrupting the normal flow of the document. Using the translateX value
will change the position of an element on the horizontal axis while
using the translateY value will change the position of an element on the
vertical axis.

As with the scale value, to set both the x and y axis values at once,
use the translate value and declare the x axis value first, followed by
a comma, and then the y axis value.

The distance values used within the translate value may be any general
length measurement, most commonly pixels or percentages. Positive values
will push an element down and to the right of its default position while
negative values will pull an element up and to the left of its default
position.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box-3&quot;&gt;Box 3&lt;/figure&gt;                           |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: translateX(-10px);                                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: translateY(25%);                                          |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box-3 {                                                             |
|   |                                                                      |
| 8 | transform: translate(-10px, 25%);                                    |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Translate Demo

### 2D Skew

The last transform value in the group, skew, is used to distort elements
on the horizontal axis, vertical axis, or both. The syntax is very
similar to that of the scale and translate values. Using the skewX value
distorts an element on the horizontal axis while the skewY value
distorts an element on the vertical axis. To distort an element on both
axes the skew value is used, declaring the x axis value first, followed
by a comma, and then the y axis value.%p

The distance calculation of the skew value is measured in units of
degrees. Length measurements, such as pixels or percentages, do not
apply here.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box-3&quot;&gt;Box 3&lt;/figure&gt;                           |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: skewX(5deg);                                              |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: skewY(-20deg);                                            |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box-3 {                                                             |
|   |                                                                      |
| 8 | transform: skew(5deg, -20deg);                                       |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Skew Demo

### Combining Transforms

It is common for multiple transforms to be used at once, rotating and
scaling the size of an element at the same time for example. In this
event multiple transforms can be combined together. To combine
transforms, list the transform values within the transform property one
after the other without the use of commas.

Using multiple transform declarations will not work, as each declaration
will overwrite the one above it. The behavior in that case would be the
same as if you were to set the height of an element numerous times.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: rotate(25deg) scale(.75);                                 |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: skew(10deg, 20deg) translateX(20px);                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Combining Transforms Demo

Behind every transform there is also a matrix explicitly defining the
behavior of the transform. Using the rotate, scale, transition,
and skew values provide an easy way to establish this matrix. However,
should you be mathematically inclined, and prefer to take a [[deeper
dive]{.underline}](http://dev.opera.com/articles/view/understanding-the-css-transforms-matrix/) into
transforms, try your hand at using the matrix property.

### 2D Cube Demo

**HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;div class=&quot;cube&quot;&gt;                                             |
|   |                                                                    |
| 2 | &lt;figure class=&quot;side top&quot;&gt;1&lt;/figure&gt;                          |
|   |                                                                    |
| 3 | &lt;figure class=&quot;side left&quot;&gt;2&lt;/figure&gt;                         |
|   |                                                                    |
| 4 | &lt;figure class=&quot;side right&quot;&gt;3&lt;/figure&gt;                        |
|   |                                                                    |
| 5 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 6 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

**CSS**

+---+--------------------------------------------------------------------+
| 1 | .cube {                                                            |
|   |                                                                    |
| 2 | position: relative;                                                |
|   |                                                                    |
| 3 | }                                                                  |
|   |                                                                    |
| 4 | .side {                                                            |
|   |                                                                    |
| 5 | height: 95px;                                                      |
|   |                                                                    |
| 6 | position: absolute;                                                |
|   |                                                                    |
| 7 | width: 95px;                                                       |
|   |                                                                    |
| 8 | }                                                                  |
|   |                                                                    |
| 9 | .top {                                                             |
|   |                                                                    |
| 1 | background: #9acc53;                                               |
| 0 |                                                                    |
|   | transform: rotate(-45deg) skew(15deg, 15deg);                      |
| 1 |                                                                    |
| 1 | }                                                                  |
|   |                                                                    |
| 1 | .left {                                                            |
| 2 |                                                                    |
|   | background: #8ec63f;                                               |
| 1 |                                                                    |
| 3 | transform: rotate(15deg) skew(15deg, 15deg) translate(-50%, 100%); |
|   |                                                                    |
| 1 | }                                                                  |
| 4 |                                                                    |
|   | .right {                                                           |
| 1 |                                                                    |
| 5 | background: #80b239;                                               |
|   |                                                                    |
| 1 | transform: rotate(-15deg) skew(-15deg, -15deg) translate(50%,      |
| 6 | 100%);                                                             |
|   |                                                                    |
| 1 | }                                                                  |
| 7 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 8 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 9 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 0 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 1 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Demo

### Transform Origin

As previously mentioned, the default transform origin is the dead center
of an element, both 50% horizontally and 50% vertically. To change this
default origin position the transform-origin property may be used.

The transform-origin property can accept one or two values. When only
one value is specified, that value is used for both the horizontal and
vertical axes. If two values are specified, the first is used for the
horizontal axis and the second is used for the vertical axis.

Individually the values are treated like that of a background image
position, using either a length or keyword value. That said, 0 0 is the
same value as top left, and 100% 100% is the same value as bottom right.
More specific values can also be set, for example 20px 50px would set
the origin to 20 pixels across and 50 pixels down the element.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box-3&quot;&gt;Box 3&lt;/figure&gt;                           |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box-4&quot;&gt;Box 3&lt;/figure&gt;                           |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: rotate(15deg);                                            |
|   |                                                                      |
| 3 | transform-origin: 0 0;                                               |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | .box-2 {                                                             |
|   |                                                                      |
| 6 | transform: scale(.5);                                                |
|   |                                                                      |
| 7 | transform-origin: 100% 100%;                                         |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | .box-3 {                                                             |
|   |                                                                      |
| 1 | transform: skewX(20deg);                                             |
| 0 |                                                                      |
|   | transform-origin: top left;                                          |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 | .box-4 {                                                             |
| 2 |                                                                      |
|   | transform: scale(.75) translate(-10px, -10px);                       |
| 1 |                                                                      |
| 3 | transform-origin: 20px 50px;                                         |
|   |                                                                      |
| 1 | }                                                                    |
| 4 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transform Origin Demo

Notably, the transform-origin property does run into some issues when
also using the translate transform value. Since both of them are
attempting to position the element, their values can collide. Use the
two of these with caution, always checking to make sure the desired
outcome is achieved.

### Perspective

In order for three-dimensional transforms to work the elements need a
perspective from which to transform. The perspective for each element
can be thought of as a *vanishing point*, similar to that which can be
seen in three-dimensional drawings.

The perspective of an element can be set in two different ways. One way
includes using the perspective value within the transform property on
individual elements, while the other includes using
the perspective property on the parent element residing over child
elements being transformed.

Using the perspective value within the transform property works great
for transforming one element from a single, unique perspective. When you
want to transform a group of elements all with the same perspective, or
vanishing point, apply the perspective property to their parent element.

The example below shows a handful of elements all transformed using
their individual perspectives with the perspective value.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box&quot;&gt;Box 1&lt;/figure&gt;                             |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box&quot;&gt;Box 2&lt;/figure&gt;                             |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box&quot;&gt;Box 3&lt;/figure&gt;                             |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | transform: perspective(200px) rotateX(45deg);                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Perspective Value Demo

The following example shows a handful of elements, side by side, all
transformed using the same perspective, accomplished by using
the perspective property on their direct parent element.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;group&quot;&gt;                                              |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box&quot;&gt;Box 1&lt;/figure&gt;                             |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box&quot;&gt;Box 2&lt;/figure&gt;                             |
|   |                                                                      |
| 4 | &lt;figure class=&quot;box&quot;&gt;Box 3&lt;/figure&gt;                             |
|   |                                                                      |
| 5 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .group {                                                             |
|   |                                                                      |
| 2 | perspective: 200px;                                                  |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box {                                                               |
|   |                                                                      |
| 5 | transform: rotateX(45deg);                                           |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Perspective Property Demo

### Perspective Depth Value

The perspective value can be set as none or a length measurement.
The none value turns off any perspective, while the length value will
set the depth of the perspective. The higher the value, the further away
the perspective appears, thus creating a fairly low intensity
perspective and a small three-dimensional change. The lower the value
the closer the perspective appears, thus creating a high intensity
perspective and a large three-dimensional change.

Imagine yourself standing 10 feet away from a 10 foot cube as compared
to standing 1,000 feet away from the same cube. At 10 feet, your
distance to the cube is the same as the dimensions of the cube,
therefore the perspective shift is much greater than it will be at 1,000
feet, where the dimensions of the cube are only one one-hundredth of
your distance to the cube. The same thinking applies to perspective
depth values.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: perspective(100px) rotateX(45deg);                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: perspective(1000px) rotateX(45deg);                       |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Perspective Depth Value Demo

### Perspective Origin

As with setting a transform-origin you can also set
a perspective-origin. The same values used for
the transform-origin property may also be used with
the perspective-origin property, and maintain the same relationship to
the element. The large difference between the two falls where the origin
of a transform determines the coordinates used to calculate the change
of a transform, while the origin of a perspective identifies the
coordinates of the vanishing point of a transform.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;original original-1&quot;&gt;                                |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box&quot;&gt;Box 1&lt;/figure&gt;                             |
|   |                                                                      |
| 3 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 4 | &lt;div class=&quot;original original-2&quot;&gt;                                |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box&quot;&gt;Box 2&lt;/figure&gt;                             |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 | &lt;div class=&quot;original original-3&quot;&gt;                                |
|   |                                                                      |
| 8 | &lt;figure class=&quot;box&quot;&gt;Box 3&lt;/figure&gt;                             |
|   |                                                                      |
| 9 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .original {                                                          |
|   |                                                                      |
| 2 | perspective: 200px;                                                  |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box {                                                               |
|   |                                                                      |
| 5 | transform: rotateX(45deg);                                           |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .original-1 {                                                        |
|   |                                                                      |
| 8 | perspective-origin: 0 0;                                             |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | .original-2 {                                                        |
| 0 |                                                                      |
|   | perspective-origin: 75% 75%;                                         |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 | .original-3 {                                                        |
| 2 |                                                                      |
|   | perspective-origin: 20px 40px;                                       |
| 1 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Perspective Origin Demo

### 3D Transforms

Working with two-dimensional transforms we are able to alter elements on
the horizontal and vertical axes, however there is another axis along
which we can transform elements. Using [[three-dimensional
transforms]{.underline}](http://24ways.org/2010/intro-to-css-3d-transforms) we
can change elements on the z axis, giving us control of depth as well as
length and width.

### 3D Rotate

So far we've discussed how to rotate an object either clockwise or
counterclockwise on a flat plane. With three-dimensional transforms we
can rotate an element around any axes. To do so, we use three
new transform values, including rotateX, rotateY, and rotateZ.

Using the rotateX value allows you to rotate an element around
the x axis, as if it were being bent in half horizontally. Using
the rotateY value allows you to rotate an element around the y axis, as
if it were being bent in half vertically. Lastly, using
the rotateZ value allows an element to be rotated around the z axis.

As with the general rotate value before, positive values will rotate the
element around its dedicated axis clockwise, while negative values will
rotate the element counterclockwise.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 | &lt;figure class=&quot;box-3&quot;&gt;Box 3&lt;/figure&gt;                           |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: perspective(200px) rotateX(45deg);                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: perspective(200px) rotateY(45deg);                        |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box-3 {                                                             |
|   |                                                                      |
| 8 | transform: perspective(200px) rotateZ(45deg);                        |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### 3D Rotate Demo

### 3D Scale

By using the scaleZ three-dimensional transform elements may be scaled
on the z axis. This isn't extremely exciting when no other
three-dimensional transforms are in place, as there is nothing in
particular to scale. In the demonstration below the elements are being
scaled up and down on the z axis, however the rotateX value is added in
order to see the behavior of the scaleZ value. When removing
the rotateX in this case, the elements will appear to be unchanged.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: perspective(200px) scaleZ(1.75) rotateX(45deg);           |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: perspective(200px) scaleZ(.25) rotateX(45deg);            |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### 3D Scale Demo

### 3D Translate

Elements may also be translated on the z axis using
the translateZ value. A negative value here will push an element further
away on the z axis, resulting in a smaller element. Using a positive
value will pull an element closer on the z axis, resulting in a larger
element.

While this may appear to be very similar to that of the two-dimensional
transform scale value, it is actually quite different. The transform is
taking place on the z axis, not the x or y axes. When working with
three-dimensional transforms, being able to move an element on
the z axis does have great benefits, like when building the cube below
for example.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: perspective(200px) translateZ(-50px);                     |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | transform: perspective(200px) translateZ(50px);                      |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### 3D Translate Demo

### 3D Skew

Skew is the one two-dimensional transform that **cannot** be transformed
on a three-dimensional scale. Elements may be skewed on
the x and y axis, then transformed three-dimensionally as wished, but
they cannot be skewed on the z axis.

### Shorthand 3D Transforms

As with combining two-dimensional transforms, there are also properties
to write out shorthand three-dimensional transforms. These properties
include rotate3d, scale3d, transition3d, and matrix3d. These properties
do require a bit more math, as well as a
strong [[understanding]{.underline}](https://developer.mozilla.org/en/CSS/transform-function) of
the matrices behind each transform. Should you be interested in looking
a bit deeper into them, please do!

### Transform Style

On occasion three-dimensional transforms will be applied on an element
that is nested within a parent element which is also being transformed.
In this event, the nested, transformed elements will not appear in their
own three-dimensional space. To allow nested elements to transform in
their own three-dimensional plane use the transform-style property with
the preserve-3d value.

The transform-style property needs to be placed on the parent element,
above any nested transforms. The preserve-3d value allows the
transformed children elements to appear in their own three-dimensional
plane while the flat value forces the transformed children elements to
lie flat on the two-dimensional plane.

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;rotate three-d&quot;&gt;                                     |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box&quot;&gt;Box 1&lt;/figure&gt;                             |
|   |                                                                      |
| 3 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 4 | &lt;div class=&quot;rotate&quot;&gt;                                             |
|   |                                                                      |
| 5 | &lt;figure class=&quot;box&quot;&gt;Box 2&lt;/figure&gt;                             |
|   |                                                                      |
| 6 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .rotate {                                                            |
|   |                                                                      |
| 2 | transform: perspective(200px) rotateY(45deg);                        |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .three-d {                                                           |
|   |                                                                      |
| 5 | transform-style: preserve-3d;                                        |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box {                                                               |
|   |                                                                      |
| 8 | transform: rotateX(15deg) translateZ(20px);                          |
|   |                                                                      |
| 9 | transform-origin: 0 0;                                               |
|   |                                                                      |
| 1 | }                                                                    |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transform Style Demo

To see an additional example of the transform-style property in action
check out the
WebKit [[explanation]{.underline}](http://www.webkit.org/blog-files/3d-transforms/transform-style.html).

### Backface Visibility

When working with three-dimensional transforms, elements will
occasionally be transformed in a way that causes them to face away from
the screen. This may be caused by setting the rotateY(180deg) value for
example. By default these elements are shown from the back. So if you
prefer not to see these elements at all, set
the backface-visibility property to hidden, and you will hide the
element whenever it is facing away from the screen.

The other value to backface-visibility is visible which is the default
value, always displaying an element, no matter which direction it faces.

In the demonstration below notice how the second box isn't displayed
because backface-visibility: hidden; declaration has been set.
The backface-visibility property takes even more significance when
using [[animations]{.underline}](https://css-tricks.com/almanac/properties/b/backface-visibility/).

**HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;figure class=&quot;box-1&quot;&gt;Box 1&lt;/figure&gt;                           |
|   |                                                                      |
| 2 | &lt;figure class=&quot;box-2&quot;&gt;Box 2&lt;/figure&gt;                           |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

**CSS**

+---+----------------------------------------------------------------------+
| 1 | .box-1 {                                                             |
|   |                                                                      |
| 2 | transform: rotateY(180deg);                                          |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .box-2 {                                                             |
|   |                                                                      |
| 5 | backface-visibility: hidden;                                         |
|   |                                                                      |
| 6 | transform: rotateY(180deg);                                          |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Backface Visibility Demo

### 3D Cube Demo

**HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;div class=&quot;cube-container&quot;&gt;                                   |
|   |                                                                    |
| 2 | &lt;div class=&quot;cube&quot;&gt;                                             |
|   |                                                                    |
| 3 | &lt;figure class=&quot;side front&quot;&gt;1&lt;/figure&gt;                        |
|   |                                                                    |
| 4 | &lt;figure class=&quot;side back&quot;&gt;2&lt;/figure&gt;                         |
|   |                                                                    |
| 5 | &lt;figure class=&quot;side left&quot;&gt;3&lt;/figure&gt;                         |
|   |                                                                    |
| 6 | &lt;figure class=&quot;side right&quot;&gt;4&lt;/figure&gt;                        |
|   |                                                                    |
| 7 | &lt;figure class=&quot;side top&quot;&gt;5&lt;/figure&gt;                          |
|   |                                                                    |
| 8 | &lt;figure class=&quot;side bottom&quot;&gt;6&lt;/figure&gt;                       |
|   |                                                                    |
| 9 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 1 | &lt;/div&gt;                                                           |
| 0 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 1 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

**CSS**

+---+-------------------------------------------------------------------+
| 1 | .cube-container {                                                 |
|   |                                                                   |
| 2 | height: 200px;                                                    |
|   |                                                                   |
| 3 | perspective: 300;                                                 |
|   |                                                                   |
| 4 | position: relative;                                               |
|   |                                                                   |
| 5 | width: 200px;                                                     |
|   |                                                                   |
| 6 | }                                                                 |
|   |                                                                   |
| 7 | .cube {                                                           |
|   |                                                                   |
| 8 | height: 100%;                                                     |
|   |                                                                   |
| 9 | position: absolute;                                               |
|   |                                                                   |
| 1 | transform: translateZ(-100px);                                    |
| 0 |                                                                   |
|   | transform-style: preserve-3d;                                     |
| 1 |                                                                   |
| 1 | width: 100%;                                                      |
|   |                                                                   |
| 1 | }                                                                 |
| 2 |                                                                   |
|   | .side {                                                           |
| 1 |                                                                   |
| 3 | background: rgba(45, 179, 74, .3);                                |
|   |                                                                   |
| 1 | border: 2px solid #2db34a;                                        |
| 4 |                                                                   |
|   | height: 196px;                                                    |
| 1 |                                                                   |
| 5 | position: absolute;                                               |
|   |                                                                   |
| 1 | width: 196px;                                                     |
| 6 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 7 | .front {                                                          |
|   |                                                                   |
| 1 | transform: translateZ(100px);                                     |
| 8 |                                                                   |
|   | }                                                                 |
| 1 |                                                                   |
| 9 | .back {                                                           |
|   |                                                                   |
| 2 | transform: rotateX(180deg) translateZ(100px);                     |
| 0 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 1 | .left {                                                           |
|   |                                                                   |
| 2 | transform: rotateY(-90deg) translateZ(100px);                     |
| 2 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 3 | .right {                                                          |
|   |                                                                   |
| 2 | transform: rotateY(90deg) translateZ(100px);                      |
| 4 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 5 | .top {                                                            |
|   |                                                                   |
| 2 | transform: rotateX(90deg) translateZ(100px);                      |
| 6 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 7 | .bottom {                                                         |
|   |                                                                   |
| 2 | transform: rotateX(-90deg) translateZ(100px);                     |
| 8 |                                                                   |
|   | }                                                                 |
| 2 |                                                                   |
| 9 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 0 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 1 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 2 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 3 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 4 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 5 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 6 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 7 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 8 |                                                                   |
|   |                                                                   |
| 3 |                                                                   |
| 9 |                                                                   |
+===+===================================================================+
+---+-------------------------------------------------------------------+

<h3>Demo</h3>

<h3>Resources & Links</h3>

<ul>
  <li><a href="http://www.css3files.com/transform/">
    Transform Property</a> via CSS3 Files</li>
  <li><a href="http://dev.opera.com/articles/view/understanding-the-css-transforms-matrix/">
    Understanding the CSS Transforms Matrix</a> via Dev.Opera</li>
  <li><a href="http://24ways.org/2010/intro-to-css-3d-transforms">
    An Introduction to CSS 3-D Transforms</a> via 24 Ways</li>
  <li><a href="https://developer.mozilla.org/en/CSS/transform-function">
    Transform Function</a> via Mozilla Developer Network</li>
  <li><a href="http://www.webkit.org/blog-files/3d-transforms/transform-style.html">
    Transform Style</a> via WebKit</li>
  <li><a href="https://css-tricks.com/almanac/properties/b/backface-visibility/">
    Backface Visibility</a> via CSS-Tricks</li>
</ul>

[<b>Lesson 6</b>] <a href="https://learn.shayhowe.com/advanced-html-css/jquery/">jQuery</a>
[<b>Lesson 8</b>] <a href="https://learn.shayhowe.com/advanced-html-css/transitions-animations/">Transitions &amp; Animations</a>

[Lesson 8] Transitions & Animations

In this Lesson 8

GitlabGitLab is the only place where enterprises build mission‑critical
software.

<b>CSS**

-   [[Transitions]{.underline}](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#transitions)

-   [[Shorthand
    Transitions]{.underline}](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#shorthand-transitions)

-   [[Animations]{.underline}](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#animations)

-   [[Customizing
    Animations]{.underline}](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#customizing-animations)

-   [[Shorthand
    Animations]{.underline}](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#shorthand-animations)

<b>SHARE**

One evolution with CSS3 was the ability to write behaviors for
transitions and animations. Front end developers have been asking for
the ability to design these interactions within HTML and CSS, without
the use of JavaScript or Flash, for years. Now their wish has come true.

With CSS3 transitions you have the potential to alter the appearance and
behavior of an element whenever a state change occurs, such as when it
is hovered over, focused on, active, or targeted.

Animations within CSS3 allow the appearance and behavior of an element
to be altered in multiple keyframes. Transitions provide a change from
one state to another, while animations can set multiple points of
transition upon different keyframes.

### Transitions

As mentioned, for
a [[transition]{.underline}](http://www.alistapart.com/articles/understanding-css3-transitions/) to
take place, an element must have a change in state, and different styles
must be identified for each state. The easiest way for determining
styles for different states is by using the :hover, :focus, :active,
and :target pseudo-classes.

There are four transition related properties in total,
including transition-property, transition-duration, transition-timing-function,
and transition-delay. Not all of these are required to build a
transition, with the first three are the most popular.

In the example below the box will change its background color over the
course of 1 second in a linear fashion.

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | transition-property: background;                                     |
|   |                                                                      |
| 4 | transition-duration: 1s;                                             |
|   |                                                                      |
| 5 | transition-timing-function: linear;                                  |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 | .box:hover {                                                         |
|   |                                                                      |
| 8 | background: #ff7b29;                                                 |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transition Demo

### Vendor Prefixes

The code above, as with the rest of the code samples in this lesson, are
not vendor prefixed. This is intentionally un-prefixed in the interest
of keeping the code snippet small and comprehensible. For the best
support across all browsers, use vendor prefixes.

For reference, the prefixed version of the code above would look like
the following.

+---+--------------------------------------------------------------------+
| 1 | .box {                                                             |
|   |                                                                    |
| 2 | background: #2db34a;                                               |
|   |                                                                    |
| 3 | -webkit-transition-property: background;                           |
|   |                                                                    |
| 4 | -moz-transition-property: background;                              |
|   |                                                                    |
| 5 | -o-transition-property: background;                                |
|   |                                                                    |
| 6 | transition-property: background;                                   |
|   |                                                                    |
| 7 | -webkit-transition-duration: 1s;                                   |
|   |                                                                    |
| 8 | -moz-transition-duration: 1s;                                      |
|   |                                                                    |
| 9 | -o-transition-duration: 1s;                                        |
|   |                                                                    |
| 1 | transition-duration: 1s;                                           |
| 0 |                                                                    |
|   | -webkit-transition-timing-function: linear;                        |
| 1 |                                                                    |
| 1 | -moz-transition-timing-function: linear;                           |
|   |                                                                    |
| 1 | -o-transition-timing-function: linear;                             |
| 2 |                                                                    |
|   | transition-timing-function: linear;                                |
| 1 |                                                                    |
| 3 | }                                                                  |
|   |                                                                    |
| 1 | .box:hover {                                                       |
| 4 |                                                                    |
|   | background: #ff7b29;                                               |
| 1 |                                                                    |
| 5 | }                                                                  |
|   |                                                                    |
| 1 |                                                                    |
| 6 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 7 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 8 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 9 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Transitional Property

The transition-property property determines exactly what properties will
be altered in conjunction with the other transitional properties. By
default, all of the properties within an element's different states will
be altered upon change. However, only the properties identified within
the transition-property value will be affected by any transitions.

In the example above, the background property is identified in
the transition-property value. Here the background property is the only
property that will change over the duration of 1 second in
a linear fashion. Any other properties included when changing an
element's state, but not included within the transition-property value,
will not receive the transition behaviors as set by
the transition-duration or transition-timing-function properties.

If multiple properties need to be transitioned they may be comma
separated within the transition-property value. Additionally, the
keyword value all may be used to transition all properties of an
element.

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | border-radius: 6px                                                   |
|   |                                                                      |
| 4 | transition-property: background, border-radius;                      |
|   |                                                                      |
| 5 | transition-duration: 1s;                                             |
|   |                                                                      |
| 6 | transition-timing-function: linear;                                  |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 | .box:hover {                                                         |
|   |                                                                      |
| 9 | background: #ff7b29;                                                 |
|   |                                                                      |
| 1 | border-radius: 50%;                                                  |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transition Property Demo

### Transitional Properties

It is important to note, <b>not all properties may be transitioned**,
only properties that have an identifiable halfway point. Colors, font
sizes, and the alike may be transitioned from one value to another as
they have recognizable values in-between one another.
The display property, for example, may not be transitioned as it does
not have any midpoint. A handful of the more popular transitional
properties include the following.

-   background-color

-   background-position

-   border-color

-   border-width

-   border-spacing

-   bottom

-   clip

-   color

-   crop

-   font-size

-   font-weight

-   height

-   left

-   letter-spacing

-   line-height

-   margin

-   max-height

-   max-width

-   min-height

-   min-width

-   opacity

-   outline-color

-   outline-offset

-   outline-width

-   padding

-   right

-   text-indent

-   text-shadow

-   top

-   vertical-align

-   visibility

-   width

-   word-spacing

-   z-index

### Transition Duration

The duration in which a transition takes place is set using
the transition-duration property. The value of this property can be set
using general timing values, including seconds (s) and milliseconds
(ms). These timing values may also come in fractional
measurements, .2s for example.

When transitioning multiple properties you can set multiple durations,
one for each property. As with the transition-property property value,
multiple durations can be declared using comma separated values. The
order of these values when identifying individual properties and
durations does matter. For example, the first property identified within
the transition-property property will match up with the first time
identified within the transition-duration property, and so forth.

If multiple properties are being transitioned with only one duration
value declared, that one value will be the duration of all the
transitioned properties.

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | border-radius: 6px;                                                  |
|   |                                                                      |
| 4 | transition-property: background, border-radius;                      |
|   |                                                                      |
| 5 | transition-duration: .2s, 1s;                                        |
|   |                                                                      |
| 6 | transition-timing-function: linear;                                  |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 | .box:hover {                                                         |
|   |                                                                      |
| 9 | background: #ff7b29;                                                 |
|   |                                                                      |
| 1 | border-radius: 50%;                                                  |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transition Duration Demo

### Transition Timing

The transition-timing-function property is used to set the speed in
which a transition will move. Knowing the duration from
the transition-duration property a transition can have multiple speeds
within a single duration. A few of the more popular keyword values for
the transition-timing-function property
include linear, ease-in, ease-out, and ease-in-out.

The linear keyword value identifies a transition moving in a constant
speed from one state to another. The ease-in value identifies a
transition that starts slowly and speeds up throughout the transition,
while the ease-out value identifies a transition that starts quickly and
slows down throughout the transition. The ease-in-out value identifies a
transition that starts slowly, speeds up in the middle, then slows down
again before ending.

Each timing function has a [[cubic-bezier
curve]{.underline}](http://www.roblaplaca.com/examples/bezierBuilder/) behind
it, which can be specifically set using the cubic-bezier(x1, y1, x2,
y2) value. Additional values include step-start, step-stop, and a
uniquely identified steps(number_of_steps, direction) value.

When transitioning multiple properties, you can identify multiple timing
functions. These timing function values, as with other transition
property values, may be declared as comma separated values.

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | border-radius: 6px;                                                  |
|   |                                                                      |
| 4 | transition-property: background, border-radius;                      |
|   |                                                                      |
| 5 | transition-duration: .2s, 1s;                                        |
|   |                                                                      |
| 6 | transition-timing-function: linear, ease-in;                         |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 | .box:hover {                                                         |
|   |                                                                      |
| 9 | background: #ff7b29;                                                 |
|   |                                                                      |
| 1 | border-radius: 50%;                                                  |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transition Timing Demo

### Transition Delay

On top of declaring the transition property, duration, and timing
function, you can also set a delay with the transition-delay property.
The delay sets a time value, seconds or milliseconds, that determines
how long a transition should be stalled before executing. As with all
other transition properties, to delay numerous transitions, each delay
can be declared as comma separated values.

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | border-radius: 6px                                                   |
|   |                                                                      |
| 4 | transition-property: background, border-radius;                      |
|   |                                                                      |
| 5 | transition-duration: .2s, 1s;                                        |
|   |                                                                      |
| 6 | transition-timing-function: linear, ease-in;                         |
|   |                                                                      |
| 7 | transition-delay: 0s, 1s;                                            |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | .box:hover {                                                         |
|   |                                                                      |
| 1 | background: #ff7b29;                                                 |
| 0 |                                                                      |
|   | border-radius: 50%;                                                  |
| 1 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Transition Delay Demo

### Shorthand Transitions

Declaring every transition property individually can become quite
intensive, especially with vendor prefixes. Fortunately there is a
shorthand property, transition, capable of supporting all of these
different properties and values. Using the transition value alone, you
can set every transition value in the order
of transition-property, transition-duration, transition-timing-function,
and lastly transition-delay. Do not use commas with these values unless
you are identifying numerous transitions.

To set numerous transitions at once, set each individual group of
transition values, then use a comma to separate each additional group of
transition values.

+---+----------------------------------------------------------------------+
| 1 | .box {                                                               |
|   |                                                                      |
| 2 | background: #2db34a;                                                 |
|   |                                                                      |
| 3 | border-radius: 6px;                                                  |
|   |                                                                      |
| 4 | transition: background .2s linear, border-radius 1s ease-in 1s;      |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | .box:hover {                                                         |
|   |                                                                      |
| 7 | color: #ff7b29;                                                      |
|   |                                                                      |
| 8 | border-radius: 50%;                                                  |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Shorthand Transitions Demo

### Transitional Button

<b>HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;button&gt;Awesome Button&lt;/button&gt;                                |
|   |                                                                    |
| 2 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

<b>CSS**

+---+--------------------------------------------------------------------+
| 1 | button {                                                           |
|   |                                                                    |
| 2 | border: 0;                                                         |
|   |                                                                    |
| 3 | background: #0087cc;                                               |
|   |                                                                    |
| 4 | border-radius: 4px;                                                |
|   |                                                                    |
| 5 | box-shadow: 0 5px 0 #006599;                                       |
|   |                                                                    |
| 6 | color: #fff;                                                       |
|   |                                                                    |
| 7 | cursor: pointer;                                                   |
|   |                                                                    |
| 8 | font: inherit;                                                     |
|   |                                                                    |
| 9 | margin: 0;                                                         |
|   |                                                                    |
| 1 | outline: 0;                                                        |
| 0 |                                                                    |
|   | padding: 12px 20px;                                                |
| 1 |                                                                    |
| 1 | transition: all .1s linear;                                        |
|   |                                                                    |
| 1 | }                                                                  |
| 2 |                                                                    |
|   | button:active {                                                    |
| 1 |                                                                    |
| 3 | box-shadow: 0 2px 0 #006599;                                       |
|   |                                                                    |
| 1 | transform: translateY(3px);                                        |
| 4 |                                                                    |
|   | }                                                                  |
| 1 |                                                                    |
| 5 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 6 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 7 |                                                                    |
|   |                                                                    |
| 1 |                                                                    |
| 8 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Demo

### Card Flip

<b>HTML**

+---+--------------------------------------------------------------------+
| 1 | &lt;div class=&quot;card-container&quot;&gt;                                   |
|   |                                                                    |
| 2 | &lt;div class=&quot;card&quot;&gt;                                             |
|   |                                                                    |
| 3 | &lt;div class=&quot;side&quot;&gt;&#8230;&lt;/div&gt;                                 |
|   |                                                                    |
| 4 | &lt;div class=&quot;side back&quot;&gt;&#8230;&lt;/div&gt;                            |
|   |                                                                    |
| 5 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 6 | &lt;/div&gt;                                                           |
|   |                                                                    |
| 7 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

<b>CSS**

+---+--------------------------------------------------------------------+
| 1 | .card-container {                                                  |
|   |                                                                    |
| 2 | height: 150px;                                                     |
|   |                                                                    |
| 3 | perspective: 600;                                                  |
|   |                                                                    |
| 4 | position: relative;                                                |
|   |                                                                    |
| 5 | width: 150px;                                                      |
|   |                                                                    |
| 6 | }                                                                  |
|   |                                                                    |
| 7 | .card {                                                            |
|   |                                                                    |
| 8 | height: 100%;                                                      |
|   |                                                                    |
| 9 | position: absolute;                                                |
|   |                                                                    |
| 1 | transform-style: preserve-3d;                                      |
| 0 |                                                                    |
|   | transition: all 1s ease-in-out;                                    |
| 1 |                                                                    |
| 1 | width: 100%;                                                       |
|   |                                                                    |
| 1 | }                                                                  |
| 2 |                                                                    |
|   | .card:hover {                                                      |
| 1 |                                                                    |
| 3 | transform: rotateY(180deg);                                        |
|   |                                                                    |
| 1 | }                                                                  |
| 4 |                                                                    |
|   | .card .side {                                                      |
| 1 |                                                                    |
| 5 | backface-visibility: hidden;                                       |
|   |                                                                    |
| 1 | height: 100%;                                                      |
| 6 |                                                                    |
|   | position: absolute;                                                |
| 1 |                                                                    |
| 7 | width: 100%;                                                       |
|   |                                                                    |
| 1 | }                                                                  |
| 8 |                                                                    |
|   | .card .back {                                                      |
| 1 |                                                                    |
| 9 | transform: rotateY(180deg);                                        |
|   |                                                                    |
| 2 | }                                                                  |
| 0 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 1 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 2 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 3 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 4 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 5 |                                                                    |
|   |                                                                    |
| 2 |                                                                    |
| 6 |                                                                    |
+===+====================================================================+
+---+--------------------------------------------------------------------+

### Demo

### Animations

Transitions do a great job of building out visual interactions from one
state to another, and are perfect for these kinds of single state
changes. However, when more control is required, transitions need to
have multiple states. In return, this is
where [[animations]{.underline}](http://coding.smashingmagazine.com/2011/09/14/the-guide-to-css-animation-principles-and-examples/) pick
up where transitions leave off.

### Animations Keyframes

To set multiple points at which an element should undergo a transition,
use the @keyframes rule. The @keyframes rule includes the animation
name, any animation breakpoints, and the properties intended to be
animated.

+---+----------------------------------------------------------------------+
| 1 | &#0064;keyframes slide {                                                  |
|   |                                                                      |
| 2 | 0% {                                                                 |
|   |                                                                      |
| 3 | left: 0;                                                             |
|   |                                                                      |
| 4 | top: 0;                                                              |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | 50% {                                                                |
|   |                                                                      |
| 7 | left: 244px;                                                         |
|   |                                                                      |
| 8 | top: 100px;                                                          |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | 100% {                                                               |
| 0 |                                                                      |
|   | left: 488px;                                                         |
| 1 |                                                                      |
| 1 | top: 0;                                                              |
|   |                                                                      |
| 1 | }                                                                    |
| 2 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Vendor Prefixing the Keyframe Rule

The @keyframes rule must be vendor prefixed, just like all of the
other transition and animation properties. The vendor prefixes for
the @keyframes rule look like the following:

-   @-moz-keyframes

-   @-o-keyframes

-   @-webkit-keyframes

The animation above is named slide, stated directly after the
opening @keyframes rule. The different keyframe breakpoints are set
using percentages, starting at 0% and working to 100% with an
intermediate breakpoint at 50%. The keywords from and to could be used
in place of 0% and 100% if wished. Additional breakpoints, besides 50%,
may also be stated. The element properties to be animated are listed
inside each of the breakpoints, left and top in the example above.

It is important to note, as with transitions only individual properties
may be animated. Consider how you might move an element from top to
bottom for example. Trying to animate from top: 0; to bottom: 0; will
not work, because animations can only apply a transition within a single
property, not from one property to another. In this case, the element
will need to be animated from top: 0; to top: 100%;.

### Animations Keyframes Demo

Hover over the ball below to see the animation in action.

### Animation Name

Once the keyframes for an animation have been declared they need to be
assigned to an element. To do so, the animation-name property is used
with the animation name, identified from the @keyframes rule, as the
property value. The animation-name declaration is applied to the element
in which the animation is to be applied to.

+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Using the animation-name property alone isn't enough though. You also
need to declare an animation-duration property and value so that the
browser knows how long an animation should take to complete.

### Animation Duration, Timing Function, & Delay

Once you have declared the animation-name property on an element,
animations behave similarly to transitions. They include a duration,
timing function, and delay if desired. To start, animations need a
duration declared using the animation-duration property. As with
transitions, the duration may be set in seconds or milliseconds.

+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | animation-duration: 2s;                                              |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

A timing function and delay can be declared using
the animation-timing-function and animation-delay properties
respectively. The values for these properties mimic and behave just as
they do with transitions.

+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | animation-duration: 2s;                                              |
|   |                                                                      |
| 4 | animation-timing-function: ease-in-out;                              |
|   |                                                                      |
| 5 | animation-delay: .5s;                                                |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

The animation below should cause the ball to bounce once while moving to
the left, however only when hovering over the stage.

<b>HTML**

+---+----------------------------------------------------------------------+
| 1 | &lt;div class=&quot;stage&quot;&gt;                                              |
|   |                                                                      |
| 2 | &lt;figure class=&quot;ball&quot;&gt;&lt;/figure&gt;                                 |
|   |                                                                      |
| 3 | &lt;/div&gt;                                                             |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<b>CSS**

+---+----------------------------------------------------------------------+
| 1 | &#0064;keyframes slide {                                                  |
|   |                                                                      |
| 2 | 0% {                                                                 |
|   |                                                                      |
| 3 | left: 0;                                                             |
|   |                                                                      |
| 4 | top: 0;                                                              |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 | 50% {                                                                |
|   |                                                                      |
| 7 | left: 244px;                                                         |
|   |                                                                      |
| 8 | top: 100px;                                                          |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | 100% {                                                               |
| 0 |                                                                      |
|   | left: 488px;                                                         |
| 1 |                                                                      |
| 1 | top: 0;                                                              |
|   |                                                                      |
| 1 | }                                                                    |
| 2 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 3 | .stage {                                                             |
|   |                                                                      |
| 1 | height: 150px;                                                       |
| 4 |                                                                      |
|   | position: relative;                                                  |
| 1 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 1 | .ball {                                                              |
| 6 |                                                                      |
|   | height: 50px;                                                        |
| 1 |                                                                      |
| 7 | position: absolute;                                                  |
|   |                                                                      |
| 1 | width: 50px;                                                         |
| 8 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 9 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
| 0 |                                                                      |
|   | animation-duration: 2s;                                              |
| 2 |                                                                      |
| 1 | animation-timing-function: ease-in-out;                              |
|   |                                                                      |
| 2 | animation-delay: .5s;                                                |
| 2 |                                                                      |
|   | }                                                                    |
| 2 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Animation Demo

Hover over the ball below to see the animation in action.

### Customizing Animations

Animations also provide the ability to further customize an element's
behavior, including the ability to declare the number of times an
animation runs, as well as the direction in which an animation
completes.

### Animation Iteration

By default, animations run their cycle once from beginning to end and
then stop. To have an animation repeat itself numerous times
the animation-iteration-count property may be used. Values for
the animation-iteration-count property include either an integer or
the infinite keyword. Using an integer will repeat the animation as many
times as specified, while the infinite keyword will repeat the animation
indefinitely in a never ending fashion.

+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | animation-duration: 2s;                                              |
|   |                                                                      |
| 4 | animation-timing-function: ease-in-out;                              |
|   |                                                                      |
| 5 | animation-delay: .5s;                                                |
|   |                                                                      |
| 6 | animation-iteration-count: infinite;                                 |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Animation Iteration Demo

Hover over the ball below to see the animation in action.

### Animation Direction

On top of being able to set the number of times an animation repeats,
you may also declare the direction an animation completes using
the animation-direction property. Values for
the animation-direction property include normal, reverse, alternate,
and alternate-reverse.

The normal value plays an animation as intended from beginning to end.
The reverse value will play the animation exactly opposite as identified
within the @keyframes rule, thus starting at 100% and working backwards
to 0%.

The alternate value will play an animation forwards then backwards.
Within the keyframes that includes running forward from 0% to 100% and
then backwards from 100% to 0%. Using
the animation-iteration-count property may limit the number of times an
animation runs both forwards and backwards. The count starts
at 1 running an animation forwards from 0% to 100%, then adds 1 running
an animation backwards from 100% to 0%. Combining for a total
of 2 iterations. The alternate value also inverses any timing functions
when playing in reverse. If an animation uses the ease-in value going
from 0% to 100%, it then uses the ease-out value going from 100% to 0%.

Lastly, the alternate-reverse value combines both
the alternate and reverse values, running an animation backwards then
forwards. The alternate-reverse value starts at 100% running to 0% and
then back to 100% again.

+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | animation-duration: 2s;                                              |
|   |                                                                      |
| 4 | animation-timing-function: ease-in-out;                              |
|   |                                                                      |
| 5 | animation-delay: .5s;                                                |
|   |                                                                      |
| 6 | animation-iteration-count: infinite;                                 |
|   |                                                                      |
| 7 | animation-direction: alternate;                                      |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Animation Direction Demo

Hover over the ball below to see the animation in action.

### Animation Play State

The animation-play-state property allows an animation to be played or
paused using the running and paused keyword values respectively. When
you play a paused animation, it will resume running from its current
state rather than starting from the very beginning again.

In the example below the animation-play-state property is set
to paused when making the stage active by clicking on it. Notice how the
animation will temporarily pause until you let up on the mouse.

```
+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | animation-duration: 2s;                                              |
|   |                                                                      |
| 4 | animation-timing-function: ease-in-out;                              |
|   |                                                                      |
| 5 | animation-delay: .5s;                                                |
|   |                                                                      |
| 6 | animation-iteration-count: infinite;                                 |
|   |                                                                      |
| 7 | animation-direction: alternate;                                      |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | .stage:active .ball {                                                |
|   |                                                                      |
| 1 | animation-play-state: paused;                                        |
| 0 |                                                                      |
|   | }                                                                    |
| 1 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

### Animation Play State Demo

Hover over the ball below to see the animation in action. Click to pause
the animation.

### Animation Fill Mode

The animation-fill-mode property identifies how an element should be
styled either before, after, or before and after an animation is run.
The animation-fill-mode property accepts four keyword values,
including none, forwards, backwards, and both.

The none value will not apply any styles to an element before or after
an animation has been run.

The forwards value will keep the styles declared within the last
specified keyframe. These styles may, however, be affected by
the animation-direction and animation-iteration-count property values,
changing exactly where an animation ends.

The backwards value will apply the styles within the first specified
keyframe as soon as being identified, before the animation has been run.
This does include applying those styles during any time that may be set
within an animation delay. The backwards value may also be affected by
the animation-direction property value.

Lastly, the both value will apply the behaviors from both
the forwards and backwards values.

```
+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation-name: slide;                                               |
|   |                                                                      |
| 3 | animation-duration: 2s;                                              |
|   |                                                                      |
| 4 | animation-timing-function: ease-in-out;                              |
|   |                                                                      |
| 5 | animation-delay: .5s;                                                |
|   |                                                                      |
| 6 | animation-fill-mode: forwards;                                       |
|   |                                                                      |
| 7 | }                                                                    |
|   |                                                                      |
| 8 | .stage:active .ball {                                                |
|   |                                                                      |
| 9 | animation-play-state: paused;                                        |
|   |                                                                      |
| 1 | }                                                                    |
| 0 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 1 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

### Animation Fill Mode Demo

Hover over the ball below to see the animation in action. Click to pause
the animation.

### Shorthand Animations

Fortunately [animations](https://developer.mozilla.org/en-US/docs/CSS/Using_CSS_animations),
just like transitions, can be written out in a shorthand format. This is
accomplished with one animation property, rather than multiple
declarations. The order of values within the animation property should
be animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction, animation-fill-mode, and lastly animation-play-state.

```
+---+----------------------------------------------------------------------+
| 1 | .stage:hover .ball {                                                 |
|   |                                                                      |
| 2 | animation: slide 2s ease-in-out .5s infinite alternate;              |
|   |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 4 | .stage:active .ball {                                                |
|   |                                                                      |
| 5 | animation-play-state: paused;                                        |
|   |                                                                      |
| 6 | }                                                                    |
|   |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

### Shorthand Animations Demo

Hover over the ball below to see the animation in action. Click to pause
the animation.

### Resources & Links

-   [Understanding CSS3 Transitions](http://www.alistapart.com/articles/understanding-css3-transitions/) 
  via A List Apart

-   [CSS Cubic-Bezier Builder](http://www.roblaplaca.com/examples/bezierBuilder/) 
  via Rob LaPlaca

-   [The Guide To CSS Animation: Principles and
    Examples](http://coding.smashingmagazine.com/2011/09/14/the-guide-to-css-animation-principles-and-examples/) via
    Smashing Magazine

-   [Using CSS
    Animations](https://developer.mozilla.org/en-US/docs/CSS/Using_CSS_animations) via
    Mozilla Developer Network

[<b>Lesson 7</b>] [Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/)
[<b>Lesson 9</b>] [Feature Support & Polyfills](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/)

[Lesson 9] Feature Support & Polyfills

In this Lesson 9

<b>HTML**

-   [HTML5
    Shiv](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#html5-shiv)

-   [Cross Browser
    Testing](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#cross-browser-testing)

<b>CSS**

-   [Detecting Browser
    Features](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#detecting-browser-features)

<b>JAVASCRIPT**

-   [Conditionally Loading
    Files](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#conditionally-loading-files)

Building a website can be both extremely rewarding and frustrating.
Common frustrations arise from trying to get a website to look and
perform the same in every browser. All front end developers have shared
this frustration at one point or another.

Truth be told, websites <b>do not** need to look or perform the same in
every browser. Exactly how close a website works in each browser is up
to you and your level of comfort for a given website. If a website
receives under half a percent of traffic from Internet Explorer 6 it
might make sense to drop support for it. If that half a percent is still
contributing to thousands of dollars in sales, support may be mandatory.
Determine what is acceptable for a given website and work from there.

There are a handful of common practices to get websites to perform
adequately in all browsers, some of which have already been covered
within this guide. When incorporating CSS3 properties, fallbacks are
recommend to support older browsers. Other techniques include shivs and
polyfills. Generally speaking, shivs and polyfills are small JavaScript
plugins that add support for a requested set of features not natively
supported by a specific browser.

### HTML5 Shiv

Perhaps the most popular shiv, and one you may have likely used already,
is the HTML5 Shiv. The HTML5 Shiv was [created by Remy
Sharp](http://paulirish.com/2011/the-history-of-the-html5-shiv/) to
provide the ability to use HTML5 elements within versions of Internet
Explorer 8 and below. The HTML5 Shiv not only creates support for HTML5
elements but also allows them to be properly styled with CSS.

The [shiv](https://code.google.com/p/html5shiv/) should be
downloaded from Google, where Remy maintains the latest version, then
hosted on your server. For the best performance, reference the shiv
JavaScript file within the head of the document, after any stylesheet
references. Additionally, you want to reference the shiv inside of
a [conditional
comment](https://css-tricks.com/how-to-create-an-ie-only-stylesheet/),
making sure that the file is only loaded within versions of Internet
Explorer 8 and below.

In this case the conditional comment looks like &lt;!&#45;&#45;&lbrack;if lt IE
9&rbrack;&gt;&#8230;&lt;&#0033;[endif&rbrack;&#45;&#45;&gt;.

```
+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45;&lbrack;if lt IE 9&rbrack;&gt;                                               |
|   |                                                                      |
| 2 | &lt;script src=&quot;html5shiv.js&quot;&gt;&lt;/script&gt;                           |
|   |                                                                      |
| 3 | &lt;&#0033;[endif&rbrack;&#45;&#45;&gt;                                                    |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

### The Difference Between a Shiv & a Shim

Chances are you may have heard of both the HTML5 *Shiv* and
HTML5 *Shim*, and wondered what the difference, if any, may be. Oddly
enough, there is <b>no** difference between the HTML5 Shiv and HTML5
Shim. The two words are often used interchangeably and are commonly
transposed.

Additionally, once the new HTML5 elements are created using the shiv,
any block level elements need to be identified and updated using
the display: block; declaration.

```
+---+----------------------------------------------------------------------+
| 1 | article,                                                             |
|   |                                                                      |
| 2 | aside,                                                               |
|   |                                                                      |
| 3 | details,                                                             |
|   |                                                                      |
| 4 | figcaption,                                                          |
|   |                                                                      |
| 5 | figure,                                                              |
|   |                                                                      |
| 6 | footer,                                                              |
|   |                                                                      |
| 7 | header,                                                              |
|   |                                                                      |
| 8 | hgroup,                                                              |
|   |                                                                      |
| 9 | nav,                                                                 |
|   |                                                                      |
| 1 | section,                                                             |
| 0 |                                                                      |
|   | summary {                                                            |
| 1 |                                                                      |
| 1 | display: block;                                                      |
|   |                                                                      |
| 1 | }                                                                    |
| 2 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

Lastly, Internet Explorer 8 and 9 do not correctly define styles for a
few HTML5 inline-block level elements. As before, these styles will need
to be explicitly stated. After which, all versions of Internet Explorer
should be good to go using any new HTML5 elements.

```
+---+----------------------------------------------------------------------+
| 1 | audio,                                                               |
|   |                                                                      |
| 2 | canvas,                                                              |
|   |                                                                      |
| 3 | video {                                                              |
|   |                                                                      |
| 4 | display: inline-block;                                               |
|   |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

### Detecting Browser Features

Referencing the HTML5 Shiv works well with a conditional comment because
the intention is to specifically target browsers that don't support new
HTML5 features and elements. Additionally, there is a way to to provide
support for specific HTML5 and CSS3 features, regardless of which
browser is being used.

Feature detection, as provided
by [Modernizr](http://modernizr.com/), provides a way to
write conditional CSS and JavaScript based on whether or not a browser
supports a specific feature. For example, if a browser supports rounded
corners Modernizr will add the class of borderradius to
the html element. If the browser doesn't support rounded corners,
Modernizr will add the class of no-borderradius to the html element.

### Loading Modernizr

To get feature detection with Modernizr up and running, visit
their [download](http://modernizr.com/download/) page and
customize what features you are looking to detect. Once downloaded,
upload the JavaScript file on your server and reference it within
the head of your HTML document, below any referenced style sheets.

It is worth noting that Modernizr may be configured to include the HTML5
Shiv, in which case the shiv doesn't need to be referenced on top of
Modernizr.

```
+---+----------------------------------------------------------------------+
| 1 | <script src="modernizr.js"></script>                                 |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+
```

### Conditionally Applying CSS Styles

Once Modernizr is up and running CSS styles may be conditionally applied
based on the features a given browser supports. Modernizr has detection
for the majority of the CSS3 properties and values, all of which can be
found in the Modernizr <a href="https://modernizr.com/docs">documentation</a>.

One item to weigh out is if feature detection is necessary for certain
styles. For example, using an RGBa color value may easily be supported
with a fallback hexadecimal value without the use of feature detection.
When deciding to use feature detection, it is important to keep styles
organized and performance in mind. Avoid duplicating any code or making
additional HTTP requests when possible.

+---+----------------------------------------------------------------------+
| 1 | button {                                                             |
|   |                                                                      |
| 2 | border: 0;                                                           |
|   |                                                                      |
| 3 | color: #fff;                                                         |
|   |                                                                      |
| 4 | cursor: pointer;                                                     |
|   |                                                                      |
| 5 | font-size: 14px;                                                     |
|   |                                                                      |
| 6 | font-weight: 600;                                                    |
|   |                                                                      |
| 7 | margin: 0;                                                           |
|   |                                                                      |
| 8 | outline: 0;                                                          |
|   |                                                                      |
| 9 | }                                                                    |
|   |                                                                      |
| 1 | /&ast; With CSS Gradient Styles &ast;/                                     |
| 0 |                                                                      |
|   | .cssgradients button {                                               |
| 1 |                                                                      |
| 1 | border: 1px solid #0080c2;                                           |
|   |                                                                      |
| 1 | background: linear-gradient(#00a2f5, #0087cc);                       |
| 2 |                                                                      |
|   | border-radius: 6px;                                                  |
| 1 |                                                                      |
| 3 | padding: 15px 30px;                                                  |
|   |                                                                      |
| 1 | }                                                                    |
| 4 |                                                                      |
|   | .cssgradients button:hover {                                         |
| 1 |                                                                      |
| 5 | background: linear-gradient(#1ab1ff, #009beb);                       |
|   |                                                                      |
| 1 | }                                                                    |
| 6 |                                                                      |
|   | .cssgradients button:active {                                        |
| 1 |                                                                      |
| 7 | box-shadow: inset 0 1px 10px rgba(255, 255, 255, .5);                |
|   |                                                                      |
| 1 | }                                                                    |
| 8 |                                                                      |
|   | /&ast; Without CSS Gradient Styles &ast;/                                  |
| 1 |                                                                      |
| 9 | .no-cssgradients button {                                            |
|   |                                                                      |
| 2 | background: transparent url(&quot;button.png&quot;) 0 0 no-repeat;           |
| 0 |                                                                      |
|   | padding: 16px 31px;                                                  |
| 2 |                                                                      |
| 1 | }                                                                    |
|   |                                                                      |
| 2 | .no-cssgradients button:hover {                                      |
| 2 |                                                                      |
|   | background-position: 0 -49px;                                        |
| 2 |                                                                      |
| 3 | }                                                                    |
|   |                                                                      |
| 2 | .no-cssgradients button:active {                                     |
| 4 |                                                                      |
|   | background-position: 0 -98px;                                        |
| 2 |                                                                      |
| 5 | }                                                                    |
|   |                                                                      |
| 2 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 2 |                                                                      |
| 9 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 0 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 1 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 2 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 3 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 4 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 3 |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Feature Detection Demo

In the demonstration above, the button inherits some default styles.
However, specific styles are only applied based on whether or not CSS3
gradient background are supported. In this case, rounded corners and box
shadows are also included within the conditional styles. Those browsers
that support gradients get a gradient background, rounded corners, and a
box shadow. Those browsers that do not receive an image with all of
these styles included within the image. With this code none of the
styles are being over written and an HTTP request is only made when
necessary.

When working with CSS3 feature detection it is hard to know what the
styles look like in browsers that do not support specific CSS3 features.
Fortunately, there is a bookmarklet
called <a href="https://github.com/davatron5000/deCSS3">deCSS3</a> which
disables any CSS3 features. Doing so allows you to see what a website
would look like without CSS3, and if your conditional styles are
working.

### Conditionally Loading Files

On top of conditionally loading styles, Modernizr also provides a way to
use <a href="https://modernizr.com/docs#using-modernizr-with-javascript">
feature detection in JavaScript</a>. With this, JavaScript polyfills and 
conditional files may be loaded based on the detection of a given feature 
with the help of jQuery and the jQuery getScript method.

Using Modernizr to set the condition of an if statement in Javascript
allows different scripts to be executed based on whether or not the
given condition is true or false. Below Modernizr is checking for local
storage support. If local storage is supported 
<a href="https://davidwalsh.name/loading-scripts-jquery">jQuery is used to load</a>
the storage.js file using the getScript method, and if local storage is not supported jQuery
is used the storage-polyfill.js file using the getScript method.

+---+----------------------------------------------------------------------+
| 1 | &#36;(document).ready(function() {                                      |
|   |                                                                      |
| 2 | if (Modernizr.localstorage) {                                        |
|   |                                                                      |
| 3 | // Local storage is available                                        |
|   |                                                                      |
| 4 | jQuery.getScript(&#39;storage.js&#39;);                                    |
|   |                                                                      |
| 5 | } else {                                                             |
|   |                                                                      |
| 6 | // Local storage is not available                                    |
|   |                                                                      |
| 7 | jQuery.getScript(&#39;storage-polyfill.js&#39;);                           |
|   |                                                                      |
| 8 | }                                                                    |
|   |                                                                      |
| 9 | });                                                                  |
|   |                                                                      |
| 1 |                                                                      |
| 0 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Conditionally Loading Based on Media Queries

One interesting condition Modernizr can test against is media queries.
Doing so provides the ability to only load files based on different
media query conditions. Not loading unnecessary files can be extremely
beneficial for performance.

+---+----------------------------------------------------------------------+
| 1 | &#36;(document).ready(function() {                                      |
|   |                                                                      |
| 2 | if (Modernizr.mq(&#39;screen and (min-width: 640px)&#39;)) {               |
|   |                                                                      |
| 3 | jQuery.getScript(&#39;tabs.js&#39;);                                       |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | });                                                                  |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Above, Modernizr looks to detect screens above 640 pixels wide,
primarily desktops, and then loads the tabs.js file based off of this
condition. It is important to note that this condition is tested only
once, when the page loads, and that is it. Should a user resize the
page, this condition will not be retested. Should this condition need to
be retested, additional JavaScript would need to be included.

### Conditionally Running Scripts

Using Modernizr, all of the HTML5 and CSS3 features they detect may be
tested within JavaScript. For example, it may be worth disabling
tooltips on mobile devices due to not having hover capabilities, and
instead showing the tooltip in plain text on the screen. The script for
calling these tooltips could be wrapped in a Modernizr condition,
preventing the script from loading on smaller screens.

+---+----------------------------------------------------------------------+
| 1 | &#36;(document).ready(function() {                                      |
|   |                                                                      |
| 2 | if (Modernizr.mq(&#39;screen and (max-width: 400px)&#39;)) {               |
|   |                                                                      |
| 3 | &#36;(&#39;.size&#39;).text(&#39;small&#39;);                                       |
|   |                                                                      |
| 4 | }                                                                    |
|   |                                                                      |
| 5 | });                                                                  |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Conditionally Running Scripts Demo

Above is a basic example of how JavaScript can be executed based on a
condition established by Modernizr. Upon loading the page, if the screen
is above 800 pixels wide nothing happens. However, if the screen is
below 800 pixels wide, upon being loaded, the word 'small' will be
swapped for 'large' based off of the executed JavaScript.

### HTML5 & CSS3 Polyfills

Currently there are polyfills for nearly all of the different HTML5 and
CSS3 features. The team over at Modernizr has put together quite an
exhaustive [list of polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills).
These polyfills can be dropped in as needed.

The same people behind Modernizr have also put together
a [list](http://html5please.com/) of all of the new HTML5
and CSS3 features, including instructions on how to use them
responsibly. Understand, not all of these features need polyfills. Quite
a few of them can be used outright or with the use of a fallback.

### Cross Browser Testing

Perhaps the most dreaded part of web design and development is cross
browser testing, making sure a website works well in all browsers.
Generally speaking the more modern browsers, Chrome, Firefox, and
Safari, all perform pretty well. The largest pitfalls live within
Internet Explorer, and testing different versions of Internet Explorer
can be difficult.

There are a [handful](http://www.smashingmagazine.com/2011/08/07/a-dozen-cross-browser-testing-tools/) of
services out there that do help with cross browser testing, some are
interactive while others are not. Being able to interact with a browser,
rather than seeing a rendered screenshot, is far more helpful for
debugging code. One of the best ways to boot up multiple versions of
Internet Explorer is by using multiple virtual machines, each with a
different version of Internet Explorer.

![VirtualBox](./images/image014.png)

<b>Fig. 9.**VirtualBox running on Mac OS X with Internet Explorer
versions 6 through 9.

Microsoft provides a handful of VirtualPCs that can be used solely for
testing. Setting all of these up can be a herculean task. Fortunately,
Greg Thornton has built an [automated installer](https://github.com/xdissent/ievms) for all of
these virtual machines. The installation takes a while to download all
of the different virtual machines, and requires a decent amount of disk
space. Prepare adequately by only installing the necessary virtual
machines and by clearing up the necessary disk space ahead of time.
Depending on how often the virtual machines are used, it may be worth
installing them on an external hard drive.

Internet Explorer versions 8 and above have built-in development tools,
unfortunately versions 7 and below do not. The web inspector and all of
the other debugging tools we've grown to love are not readily available
within Internet Explorer 7 and below.

![VirtualBox](./images/image015.png)

<b>Fig. 9</b> Internet Explorer 7 running inside of a virtual machine with the Firebug Lite

### bookmarklet open for debugging.

### Resources & Links

-   [HTML5 Shiv](https://code.google.com/p/html5shiv/) via Remy Sharp

-   [How To Create an IE-Only
    Stylesheet](https://css-tricks.com/how-to-create-an-ie-only-stylesheet/) via
    CSS-Tricks

-   [Modernizr](http://modernizr.com/)

-   [Loading Scripts with
    jQuery](https://davidwalsh.name/loading-scripts-jquery) via David Walsh

-   [deCSS3](https://github.com/davatron5000/deCSS3) via Dave Rupert

-   [HTML5 Cross Browser Polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills)

-   [HTML5 Please](http://html5please.com/)

-   [Microsoft IE Virtual Machines](https://github.com/xdissent/ievms) via Greg Thornton

<b>[Lesson 8]</b> [Transitions &
Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/)
<b>[Lesson 10]</b> [Extending Semantics &
Accessibility](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/)

<h2>[Lesson 10] Extending Semantics & Accessibility</h2>

<h3>In this Lesson 10</h3>

<h5>HTML</h5>

-   [Semantic Motivation](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#semantic-motivation)

-   [Structural Semantics](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#structural-semantics)

-   [Text Level Semantics](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#text-level-semantics)

-   [Microdata](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#microdata)

-   [WAI-ARIA](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#wai-aria)

<b>SHARE</b>

Semantics and accessibility are naturally part of HTML by design,
however they are not fully leveraged unless used accordingly. Knowing
how to write semantic and accessible code properly takes an
understanding of how semantics and accessibility work, and how users and
machines interpret them. Writing semantic and accessible code isn't
incredibly difficult, but it can be time consuming. In the long run,
however, the benefits win out.

One of the more important parts to remember when writing semantic and
accessible code is to do your best to leverage the standard markup
language. Do your best to write the cleanest code possible, and take
pride in your work. Generally speaking, don't use a meaningless element
where another element might make more semantic sense, using a div where
a h1 would be better fitted for example. Use semantic elements and
attributes, as well as microdata and WAI-ARIA to extend the value of
your code.

Additionally, <b>be an advocate for semantics and accessibility</b>. Tell
others why you've written certain code, and provide reasoning why
certain modules of content are marked up in a specific way. Outline
goals and objectives within your code, and explain how those goals and
objectives are being accomplished. The practice of writing semantic and
accessible code is growing, however adoption at large has not yet been
achieved. Be an advocate for the code you write.

### Semantic Motivation

Occasionally, one may ask if semantics really make a difference. You may
hear they slow down development, are poorly supported, or that they are
even opinionated. While this may have some validity, you still need to
retain integrity and continue to write the best code possible, for
semantics provide a larger meaning in writing code.

The fact of the matter is, [[semantics largely benefit
everyone]{.underline}](http://www.vanseodesign.com/web-design/semantic-html/).
For starters, semantics provide a shared and unambiguous meaning to
content. Semantics give content solid structure and value, while also
favoring accessibility, providing better user interfaces and more
defined information to assistive technologies. Search and globalization
is more permanent with semantics, making it easier to serve content
internationally and making it more search engine friendly. Should that
not be enough, semantics also promote interoperability, allowing the
exchange and use of information across different platforms and devices.

It's safe to say semantics are important, and here to stay. To briefly
recap, semantics provide:

-   Unambiguous, shared meaning within content

-   Accessibility

-   Search and globalization

-   Interoperability

### Structural Semantics

Within the beginner's guide we discuss the use of [[structural
semantics]{.underline}](https://learn.shayhowe.com/html-css/getting-to-know-html/),
specifically using the header, nav, article, section, aside,
and footer elements. These elements are used to provide additional
background context to the content within them, communicating their core
meaning to web browsers and other devices. This is important, as it
provides a better way to outline and structure pages, not to mention a
more meaningful solution than divisions.

### Hiding Content

Every now and then you may want to hide a block of content on the page,
perhaps showing or hiding an element depending on a user's state. For
example, having a success message hidden from a user until they complete
a desired action. Most commonly, this is accomplished with the display:
none; CSS declaration. While this does work, it is semantically
incorrect.

A better option is to use the hidden Boolean attribute, which is a
global attribute available to all elements for use. Functionally it
performs the same way as the CSS declaration, but semantically it
represents an element that should be hidden, or ignored, for the time
being. Screen readers and other devices will recognize this, temporarily
skipping it, where they may not done so with the CSS declaration.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Good &#45;&#45;&gt;                                                    |
|   |                                                                      |
| 2 | &lt;div hidden&gt;&#8230;&lt;/div&gt;                                           |
|   |                                                                      |
| 3 | &lt;!&#45;&#45; Not good &#45;&#45;&gt;                                                |
|   |                                                                      |
| 4 | &lt;div style=&quot;display: none;&quot;&gt;&#8230;&lt;/div&gt;                         |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Imagine a blind user attempting to fill out a form and the first piece
of content, before even filling out the form, is a success message. This
is a poor user experience, and one that can easily be fixed using proper
semantics.

### Text Level Semantics

The majority of content on the web lives within text, and we primarily
browse the Internet looking for this content. Using the
proper [[semantic
markup]{.underline}](https://developers.whatwg.org/text-level-semantics.html) for
text makes it easier for users to find what they need.

### Bolding Text

There are a few different ways to make text bold, including multiple
elements and the [[font
weight]{.underline}](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
property. The two main elements used in this case include strong and b.
While these two elements have the same presentation they have completely
different semantic meanings.

The strong element outlines text that has a <b>strong importance</b>. On
the contrasting side, the b element identifies text that is to
be <b>stylistically offset</b>, without importance. Generally speaking,
the b element should be used solely as a styling hook to change the
presentation of an element, where the strong element should be used to
identify significantly important text.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Strong importance &#45;&#45;&gt;                                       |
|   |                                                                      |
| 2 | &lt;strong&gt;Caution:&lt;/strong&gt; Falling rocks.                         |
|   |                                                                      |
| 3 | &lt;!&#45;&#45; Stylistically offset &#45;&#45;&gt;                                    |
|   |                                                                      |
| 4 | This recipe calls for &lt;b&gt;bacon&lt;/b&gt; and &lt;b&gt;baconnaise&lt;/b&gt;.    |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Bolding Text Demo

### Italicizing Text

Italicizing text falls in line with that of bolding text, where we can
use multiple elements or the [[font
style]{.underline}](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
property to achieve a desired presentation. When italicizing text, the
two elements most commonly used are em and i. Again, these share the
same presentation, yet have completely different semantic meanings.

The em element places a <b>stressed emphasis</b> on text, while
the i element identifies text to be expressed in an <b>alternate voice or
tone</b>. Using the em element really drives prominence with an added
importance. On the other hand, the i element is primarily used within
dialog or prose, offsetting text without any added emphasis or
importance.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Stressed emphasis &#45;&#45;&gt;                                       |
|   |                                                                      |
| 2 | I &lt;em&gt;love&lt;/em&gt; Chicago!                                         |
|   |                                                                      |
| 3 | &lt;!&#45;&#45; Alternative voice or tone &#45;&#45;&gt;                               |
|   |                                                                      |
| 4 | The name &lt;i&gt;Shay&lt;/i&gt; means a gift.                               |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Italicizing Text Demo

### Using i for Icons

Recently there has been a small movement of front end programmers using
the i element for including icons on a page, specifically as seen
within [[Bootstrap]{.underline}](https://getbootstrap.com/).
The i element is used as a hook, to which a class then determines which
icon background image to apply to the element. Depending on how closely
you wish to follow semantics this may or may not be an acceptable
practices.

### Underlining Text

Continuing the pattern of having multiple elements with the same
presentation, underlining text is no different. There are a couple of
different elements we can use as well as the [[text
decoration]{.underline}](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
property. In this case, the two primary elements used to underline text
are ins and u.

The ins element is used to identify text that has been recently <b>added
to the document</b>, and the u element simply refers to an <b>unarticulated
annotation</b>.

For more semantic code, the ins element may be used with
the cite and datetime attributes. The datetime attribute identifies when
the content was added to the document, and the cite attribute provides a
machine readable source providing reference for the addition, perhaps
documentation or a request ticket.

The u element is typically used to label text as a proper name, often in
another language, or to point out a misspelling.

Underlining text does require a bit of additional care, as it may be
confused with a hyperlink. By default hyperlinks are underlined, and
thus have become a standard design practice. Underlining text that is
not a hyperlink can confuse users and cause quite a bit of frustration.
Use underlines with caution.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Added to the document &#45;&#45;&gt;                                   |
|   |                                                                      |
| 2 | &lt;ins cite=&quot;http://learn.shayhowe.com&quot; datetime=&quot;2012-07-01&quot;&gt;   |
|   |                                                                      |
| 3 | Updated: This website now contains an advanced guide.                |
|   |                                                                      |
| 4 | &lt;/ins&gt;                                                             |
|   |                                                                      |
| 5 | &lt;!&#45;&#45; Unarticulated annotation &#45;&#45;&gt;                                |
|   |                                                                      |
| 6 | &lt;u&gt;Urushihara Yuuji&lt;/u&gt; won &lt;u&gt;Sasuke 27&lt;/u&gt;.                |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Underlining Text Demo

### Striking Text

Striking text follows the same pattern as before where different
elements may be used, as may the [[text
decoration]{.underline}](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
property. The two properties most commonly used include del and s.

The del element is used to identify text <b>deleted or removed from the
document</b>. As with the ins element, it may be used with
the cite and datetime attributes. Each of which hold the identical
semantic values as before, cite specifying a resource that explains the
change and datetime identifying when the content was removed from the
document.

The s element identifies text that is no longer accurate or relevant.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Deleted from the document &#45;&#45;&gt;                               |
|   |                                                                      |
| 2 | I am an avid cyclist, &lt;del cite=&quot;http://shayhowe.com&quot;             |
|   | datetime=&quot;2012-07-01&quot;&gt;                                            |
| 3 |                                                                      |
|   | skateboarder&lt;/del&gt; and designer.                                   |
| 4 |                                                                      |
|   | &lt;!&#45;&#45; No longer accurate or relevant &#45;&#45;&gt;                          |
| 5 |                                                                      |
|   | &lt;s&gt;&#36;24.99&lt;/s&gt; &#36;19.99                                           |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Striking Text Demo

### Highlighting Text

To highlight text for reference purposes the mark element should be
used. Added in HTML5, the mark element provides a clean, semantic way to
identify text, specifically for reference purposes without having to use
an un-semantic text level element.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Highlighted for reference purposes &#45;&#45;&gt;                      |
|   |                                                                      |
| 2 | Search results for &lt;mark&gt;&#39;chicago&#39;&lt;/mark&gt;.                     |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Highlighting Text Demo

### Abbreviations

Abbreviations, the shortened form of a phrase, can be semantically
marked up in HTML using the abbr element. The abbr element should be
used along with the title attribute, of which includes the full value of
the phrase being abbreviated. The acronym element was originally used to
distinguish acronyms from abbreviations but has since been deprecated,
and shouldn't be used.

+---+----------------------------------------------------------------------+
| 1 | &lt;abbr title=&quot;HyperText Markup Language&quot;&gt;HTML&lt;/abbr&gt;            |
|   |                                                                      |
| 2 | &lt;abbr title=&quot;Cascading Style Sheets&quot;&gt;CSS&lt;/abbr&gt;                |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Abbreviations Demo

### Sub & Superscripts

Subscripts and superscripts may be marked up accordingly using
the sub and sup elements respectively. It is important to note that
these elements should be reserved for typographical conventions, not for
presentational purposes.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Subscript &#45;&#45;&gt;                                               |
|   |                                                                      |
| 2 | H&lt;sub&gt;2&lt;/sub&gt;O                                                   |
|   |                                                                      |
| 3 | &lt;!&#45;&#45; Superscripts &#45;&#45;&gt;                                            |
|   |                                                                      |
| 4 | 1&lt;sup&gt;st&lt;/sup&gt; Place                                             |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Sub & Superscripts Demo

### Meter & Progress

To gauge scale or indicate progress the meter and progress elements
should be used. The meter element is used to measure a fixed value, one
that does not change over time, while the progress element measures the
progress of a increasing measurement.

The meter element may be used with the min, max, low, high, optimum,
and value attributes. The min and max attributes set the lower and upper
bounds of the range, where the value attribute sets the exact measured
value. The low and high attributes identify what is to be considered the
lower and higher parts of the range, while the optimum value identifies
the most favorable part of the range, of which may be in the lower or
higher parts.

The progress element indicates progress rather than a fixed measurement.
It specifically represents the completion of a task, either by what is
left to be completed or what has been completed thus far. There are two
attributes that may be applied to the progress element, value and max.
The value attributes indicates where the progress currently stands and
the max attribute indicates what progress needs to be reached.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Meter &#45;&#45;&gt;                                                   |
|   |                                                                      |
| 2 | &lt;meter value=&quot;7&quot; max=&quot;10&quot;&gt;7 stars&lt;/meter&gt;                    |
|   |                                                                      |
| 3 | &lt;meter value=&quot;47&quot; min=&quot;0&quot; max=&quot;105&quot; low=&quot;5&quot; high=&quot;65&quot;     |
|   | optimum=&quot;45&quot;&gt;The car                                              |
| 4 |                                                                      |
|   | is moving at a decent average mile per hour.&lt;/meter&gt;               |
| 5 |                                                                      |
|   | &lt;!&#45;&#45; Progress &#45;&#45;&gt;                                                |
| 6 |                                                                      |
|   | You are &lt;progress value=&quot;50&quot; max=&quot;100&quot;&gt;50%&lt;/progress&gt;        |
| 7 | complete.                                                            |
|   |                                                                      |
| 8 | &lt;progress value=&quot;50&quot; min=&quot;0&quot; max=&quot;100&quot;&gt;Hold tight,           |
|   | you&#8217;re getting                                                 |
|   |                                                                      |
|   | there.&lt;/progress&gt;                                                  |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Meter & Progress Demo

### Time & Address

Representing time and addresses in HTML can be accomplished using
the time and address elements respectively. The time element may be used
with, or without, the datetime attribute, depending on how the text
within the element is formatted. If the content is formatted with the
correct time stamp then the datetime attribute may be omitted.
Furthermore, if the time is representing the date or time of a
publication the pubdate Boolean attribute should be used.

The address element may be used to hold any contact information,
including a physical address as well as a website or email address. It
should not include any further information than the contact information,
and other content needs to be placed outside of the address element.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Time &#45;&#45;&gt;                                                    |
|   |                                                                      |
| 2 | &lt;time&gt;2011-08-24&lt;/time&gt;                                          |
|   |                                                                      |
| 3 | &lt;time datetime=&quot;2011-08-24&quot; pubdate&gt;August 24th, 2011&lt;/time&gt;   |
|   |                                                                      |
| 4 | &lt;time datetime=&quot;15:00&quot;&gt;3pm&lt;/time&gt;                              |
|   |                                                                      |
| 5 | &lt;time datetime=&quot;2011-08-24T15:00&quot;&gt;August 24th, 2011 at           |
|   | 3pm&lt;/time&gt;                                                         |
| 6 |                                                                      |
|   | &lt;!&#45;&#45; Address &#45;&#45;&gt;                                                 |
| 7 |                                                                      |
|   | &lt;address&gt;                                                          |
| 8 |                                                                      |
|   | &lt;strong&gt;Shay Howe&lt;/strong&gt;&lt;br&gt;                                 |
| 9 |                                                                      |
|   | &lt;a                                                                  |
| 1 | href=                                                                |
| 0 | &quot;http://learn.shayhowe.com&quot;&gt;http://learn.shayhowe.com&lt;/a&gt;&lt;br&gt; |
|   |                                                                      |
| 1 | &lt;a href=&quot;mailto:hello@awesome.com&quot;&gt;hello@awesome.com&lt;/a&gt;&lt;br&gt; |
| 1 |                                                                      |
|   | 600 W. Chicago Ave.&lt;br&gt;                                            |
| 1 |                                                                      |
| 2 | Suite 620&lt;br&gt;                                                      |
|   |                                                                      |
| 1 | Chicago, IL 60654&lt;br&gt;                                              |
| 3 |                                                                      |
|   | USA                                                                  |
| 1 |                                                                      |
| 4 | &lt;/address&gt;                                                         |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 7 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Time & Address Demo

### Presenting Code

Presenting code snippets, or samples, within a page can be accomplished
using either the code or pre elements, or a combination of the two.
The code element is commonly used to represent a fragment of code and is
displayed in the default monospace font. The code element is an inline
level element and may be used within paragraphs of text, or other block
and inline level elements.

For large blocks of code, the pre element can be used in conjunction
with the code element. The pre element represent preformatted text and
will display text exactly as it is typed, whitespace included. Nesting
the code element within the pre element semantically identifies larger
samples of code, which include whitepsace, displayed in a block level
manner.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Inline code samples &#45;&#45;&gt;                                     |
|   |                                                                      |
| 2 | Use the &lt;code&gt;article&lt;/code&gt; element.                            |
|   |                                                                      |
| 3 | &lt;!&#45;&#45; Larger, block level code snippets &#45;&#45;&gt;                       |
|   |                                                                      |
| 4 | &lt;pre&gt;&lt;code&gt;body {                                                |
|   |                                                                      |
| 5 | color: #666;                                                         |
|   |                                                                      |
| 6 | font: 14px/20px Arial, sans-serif;                                   |
|   |                                                                      |
| 7 | }&lt;/code&gt;&lt;/pre&gt;                                                   |
|   |                                                                      |
| 8 |                                                                      |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Presenting Code Demo

### Line & Word Breaks

Occasionally you may want to include a line break within a line of text,
in which case the br element may be used. The br element does not have a
closing tag, simply a beginning. In XHTML the br element is self
closing, including a trailing forward slash, &lt;br /&gt;.

Line breaks are not to be used for thematic grouping of content.
Paragraphs or other elements are better suited for thematic grouping.
Line breaks are specifically to be used where line breaks exist as part
of the content, for example as within addresses and poems.

In addition to line breaks, you may also specify word breaking
opportunities with the wbr element. Using the wbr element in the middle
of a word ensures that, should the word need to wrap two lines, it does
in a legible fashion.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Line break &#45;&#45;&gt;                                              |
|   |                                                                      |
| 2 | 600 W. Chicago Ave.&lt;br&gt;                                            |
|   |                                                                      |
| 3 | Chicago, IL 60654&lt;br&gt;                                              |
|   |                                                                      |
| 4 | USA                                                                  |
|   |                                                                      |
| 5 | &lt;!&#45;&#45; Word break &#45;&#45;&gt;                                              |
|   |                                                                      |
| 6 | http://shay&lt;wbr&gt;howe.com                                           |
|   |                                                                      |
| 7 |                                                                      |
|   |                                                                      |
| 8 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Line & Word Breaks Demo

### Side Comments

Originally the small element was used to render text as one font size
smaller than the default, purely for presentational purposes. As we are
aware, presentation and style should only live within CSS, not HTML.
Within HTML5, the small element preserves the presentation of being
displayed at a smaller font size, however it semantically means to be
rendered as a side comments or small print. This often includes
copyright information or legal print.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Side comments or small print &#45;&#45;&gt;                            |
|   |                                                                      |
| 2 | &lt;small&gt;&copy; 2012 Shay Howe&lt;/small&gt;                             |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Side Comments Demo

### Citations & Quotes

The beginner's guide discusses [[citations and
quotes]{.underline}](https://learn.shayhowe.com/html-css/working-with-typography/),
and when to use the cite, q, and blockquote elements accordingly. As a
quick reminder, the cite element refers to a title of work,
the q element identifies dialog or prose, and the blockquote element is
used to code longer formed quotes, commonly from external sources.

### Hyperlink Attributes

The beginner's guide also
outlines [[hyperlinks]{.underline}](https://learn.shayhowe.com/html-css/getting-to-know-html/),
and some of their different behaviors. What is not covered, however, is
some of the semantic benefits to hyperlinks, specifically with the use
of the download and rel attributes.

### Download Attribute

The download attribute tells the browser to prompt a download for a
file, rather than the default behavior of navigation to the file. As an
example, if the hyperlink reference attribute, href, is pointing to an
image, the browser will prompt a user to download the image instead of
opening the image within the browser.

The download attribute can serve as a Boolean attribute, downloading the
file as is, or it may contain a value, of which becomes the file name
once downloaded. Using a specific value here lets you name the file as
you wish on your server while still providing users with a meaningful
name.

+---+----------------------------------------------------------------------+
| 1 | &lt;!&#45;&#45; Boolean &#45;&#45;&gt;                                                 |
|   |                                                                      |
| 2 | &lt;a href=&quot;twitter-logo.png&quot; download&gt;Twitter Logo&lt;/a&gt;           |
|   |                                                                      |
| 3 | &lt;!&#45;&#45; With a value &#45;&#45;&gt;                                            |
|   |                                                                      |
| 4 | &lt;a href=&quot;twitter-logo.png&quot; download=&quot;Logo&quot;&gt;Twitter Logo&lt;/a&gt;  |
|   |                                                                      |
| 5 |                                                                      |
|   |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Download Attribute Demo

### Relationship Attribute

For any hyperlinks including a reference attribute, href, you may also
include the relationship attribute, rel. The rel attribute identifies
the relationship between the current document and the document being
referenced. For example, when linking to a copyright statement
the rel attribute value of copyright should be used.

+---+----------------------------------------------------------------------+
| 1 | &lt;a href=&quot;legal.html&quot; rel=&quot;copyright&quot;&gt;Terms of Use&lt;/a&gt;        |
|   |                                                                      |
| 2 | &lt;a href=&quot;toc.html&quot; rel=&quot;contents&quot;&gt;Table of Contents&lt;/a&gt;      |
|   |                                                                      |
| 3 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

A
few [[popular]{.underline}](http://microformats.org/wiki/existing-rel-values) rel attribute
values include:

-   alternate

-   author

-   bookmark

-   help

-   license

-   next

-   nofollow

-   noreferrer

-   prefetch

-   prev

-   search

-   tag

### Microdata

[[Microdata]{.underline}](http://www.w3.org/TR/microdata/) is HTML
extended with nested groups of name-value pairs that allow machines,
including browsers and search engines, to pick up additional semantics
and information for rich content. Adding microdata to your website is
accomplished by using predetermined attributes and values. These
attributes and values will then be interpreted, and extended, as
intended. Currently, the more popular uses of microdata reside within
coding contact information and calendar events, however there
are [[encoding
models]{.underline}](http://schema.org/docs/schemas.html) for products,
reviews, and more.

One example of microdata at work is within Google, where microdata is
interpreted and used within search results to display more relevant
data. Often performing a search for a business location yields the
address and sub sequential contact information within the results.
Chances are this information is being pulled from microdata written on
an existing website.

![Google
Microdata](./3-25-24/media/image016.jpeg){width="4.235416666666667in"
height="9.0in"}

Fig. 10

Google uses microdata to identify business locations, contact
information, hours, pricing, ratings, and more.

### Microdata vs. Microformats vs. RDFa

There are actually a handful of rich, structured data standards,
including [[microdata]{.underline}](http://www.w3.org/TR/microdata/), [[microformats]{.underline}](http://microformats.org/wiki/Main_Page),
and [[RDFa]{.underline}](http://www.w3.org/TR/xhtml-rdfa-primer/). All
of these have their pros and cons, and all of which are still viable to
practice.

Microdata is the recommended format
from [[Google]{.underline}](https://support.google.com/webmasters/bin/answer.py?hl=en&answer=99170),
and other search engines, as well as part of the HTML5 specification. It
uses findings from both microformats and RDFa to base it's design
around, thus looking to be a solid choice, and the one covered here. It
is, however, recommended you do your research, take the pulse of the
community, find what works best for your situation, and use that. Using
one of these standards is substantially better than not using any. Find
what will provide the best benefit for your users.

### Outlining Microdata

Microdata is identified using three main
attributes, itemscope, itemtype, and itemprop.

The itemscope Boolean attribute declares the scope of each microdata
item. Place this attribute on the parent element where all of the
microdata information pertaining to this item should reside.

Once you have determined the scope, use the itemtype attribute to
identify what microdata vocabulary should be used. Generally speaking,
some of the more popular microdata item types have been outlined
at [[Schema.org]{.underline}](http://schema.org/docs/schemas.html).
There are, however, other websites which outline additional, and
different, item types. You may also write your own item types should you
find the need.

+---+----------------------------------------------------------------------+
| 1 | &lt;section itemscope itemtype=&quot;http://schema.org/Person&quot;&gt;          |
|   |                                                                      |
| 2 | &#8230;                                                                 |
|   |                                                                      |
| 3 | &lt;/section&gt;                                                         |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Once the scope and type of the item have been determined, properties may
then be set. These properties are identified by different elements which
include the itemprop attribute. The value of this attribute determines
what property is being referenced, and the content within the element
itself most commonly determines the value of the property.

+---+----------------------------------------------------------------------+
| 1 | &lt;section itemscope itemtype=&quot;http://schema.org/Person&quot;&gt;          |
|   |                                                                      |
| 2 | &lt;h1 itemprop=&quot;name&quot;&gt;Shay Howe&lt;/h1&gt;                             |
|   |                                                                      |
| 3 | &lt;/section&gt;                                                         |
|   |                                                                      |
| 4 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

Some elements, however, do not get their itemprop value from the content
within the element. Instead, their value is determined from the value of
another attribute on the element. The table below outlines these one-off
elements and what attribute is used for their property value.

  ---------------------------------------------------------------------------------------
  <b>[Element]{.mark}</b>                                               <b>[Value]{.mark}</b>
  ------------------------------------------------------------------ --------------------
  &lt;meta&gt;                                                           content attribute

  &lt;audio&gt;, &lt;embed&gt;, &lt;iframe&gt;, &lt;img&gt;, &lt;source&gt;, &lt;video&gt;   src attribute

  &lt;a&gt;, &lt;area&gt;, &lt;link&gt;                                          href attribute

  &lt;object&gt;                                                         data attribute

  &lt;time&gt;                                                           datetime attribute
  ---------------------------------------------------------------------------------------

### Person Microdata

When referring to a person
the [[person]{.underline}](http://schema.org/Person) microdata library
should be used. Below is an example of what a person microdata item
might look like. Please notice, the person item type is used, as is the
postal address item type within it. Also, please notice the different
item properties and their corresponding values.

+---+----------------------------------------------------------------------+
| 1 | &lt;section itemscope itemtype=&quot;http://schema.org/Person&quot;&gt;          |
|   |                                                                      |
| 2 | &lt;strong itemprop=&quot;name&quot;&gt;Shay Howe&lt;/strong&gt;                     |
|   |                                                                      |
| 3 | &lt;img src=&quot;shay.jpg&quot; itemprop=&quot;image&quot; alt=&quot;Shay Howe&quot;&gt;        |
|   |                                                                      |
| 4 | &lt;div itemprop=&quot;jobTitle&quot;&gt;Designer and Front-end                  |
|   | Developer&lt;/div&gt;                                                    |
| 5 |                                                                      |
|   | &lt;a href=&quot;http://www.shayhowe.com&quot;                                 |
| 6 | itemprop=&quot;url&quot;&gt;shayhowe.com&lt;/a&gt;                                 |
|   |                                                                      |
| 7 | &lt;div itemprop=&quot;telephone&quot;&gt;(555) 123-4567&lt;/div&gt;                 |
|   |                                                                      |
| 8 | &lt;a href=&quot;mailto:shay@awesome.com&quot;                                 |
|   | itemprop=&quot;email&quot;&gt;shay@awesome.com&lt;/a&gt;                           |
| 9 |                                                                      |
|   | &lt;address itemprop=&quot;address&quot; itemscope                             |
| 1 | itemtype=&quot;http://schema.org/PostalAddress&quot;&gt;                       |
| 0 |                                                                      |
|   | &lt;span itemprop=&quot;streetAddress&quot;&gt;600 W. Chicago Ave.&lt;/span&gt;      |
| 1 |                                                                      |
| 1 | &lt;span itemprop=&quot;addressLocality&quot;&gt;Chicago&lt;/span&gt;,               |
|   |                                                                      |
| 1 | &lt;abbr itemprop=&quot;addressRegion&quot; title=&quot;Illinois&quot;&gt;IL&lt;/abbr&gt;    |
| 2 |                                                                      |
|   | &lt;span itemprop=&quot;postalCode&quot;&gt;60654&lt;/span&gt;                       |
| 1 |                                                                      |
| 3 | &lt;/address&gt;                                                         |
|   |                                                                      |
| 1 | &lt;/section&gt;                                                         |
| 4 |                                                                      |
|   |                                                                      |
| 1 |                                                                      |
| 5 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Person Microdata Demo

Please keep in mind, this code is for an individual person. Should you
wish to refer to an organization, a more
specific [[organization]{.underline}](http://schema.org/Organization) microdata
library should be followed.

### Event Microdata

The event microdata is very similar to that of the person microdata,
however it uses
the [[event]{.underline}](http://schema.org/Event) microdata library
instead. Common property similarities between the two can be identified,
as can some of the nested item types.

+---+----------------------------------------------------------------------+
| 1 | &lt;section itemscope itemtype=&quot;http://schema.org/Event&quot;&gt;           |
|   |                                                                      |
| 2 | &lt;a itemprop=&quot;url&quot; href=&quot;#&quot;&gt;                                    |
|   |                                                                      |
| 3 | &lt;span itemprop=&quot;name&quot;&gt;Styles Conference&lt;/span&gt;                 |
|   |                                                                      |
| 4 | &lt;/a&gt;                                                               |
|   |                                                                      |
| 5 | &lt;time itemprop=&quot;startDate&quot; datetime=&quot;2014-08-2409:00&quot;&gt;Sunday,  |
|   | August 24,                                                           |
| 6 |                                                                      |
|   | 2014 at 9:00 a.m.&lt;/time&gt;                                           |
| 7 |                                                                      |
|   | &lt;div itemprop=&quot;location&quot; itemscope                                |
| 8 | itemtype=&quot;http://schema.org/Place&quot;&gt;                               |
|   |                                                                      |
| 9 | &lt;a itemprop=&quot;url&quot;                                                 |
|   | href=&quot;http://www.thechicagotheatre.com/&quot;&gt;Chicago Theatre&lt;/a&gt;    |
| 1 |                                                                      |
| 0 | &lt;address itemprop=&quot;address&quot; itemscope                             |
|   | itemtype=&quot;http://schema.org/PostalAddress&quot;&gt;                       |
| 1 |                                                                      |
| 1 | &lt;div itemprop=&quot;streetAddress&quot;&gt;175 N. State St.&lt;/div&gt;           |
|   |                                                                      |
| 1 | &lt;span itemprop=&quot;addressLocality&quot;&gt;Chicago&lt;/span&gt;,               |
| 2 |                                                                      |
|   | &lt;abbr itemprop=&quot;addressRegion&quot; title=&quot;Illinois&quot;&gt;IL&lt;/abbr&gt;    |
| 1 |                                                                      |
| 3 | &lt;span itemprop=&quot;postalCode&quot;&gt;60601&lt;/span&gt;                       |
|   |                                                                      |
| 1 | &lt;/address&gt;                                                         |
| 4 |                                                                      |
|   | &lt;/div&gt;                                                             |
| 1 |                                                                      |
| 5 | &lt;/section&gt;                                                         |
|   |                                                                      |
| 1 |                                                                      |
| 6 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

### Event Microdata Demo

Microdata provides a lot of ways to further extend the content of a
page. We have only touched the surface here. Further information on
microdata may be found at [[Dive Into HTML5
Microdata]{.underline}](http://diveintohtml5.info/extensibility.html) and [[WHATWG
Microdata]{.underline}](https://developers.whatwg.org/links.html#microdata).

### WAI-ARIA

[[WAI-ARIA]{.underline}](http://www.w3.org/WAI/intro/aria), also know as
Web Accessibility Initiative --- Accessible Rich Internet Applications,
is a specification that helps make web pages and applications more
accessible to those with disabilities. Specifically, WAI-ARIA helps
define roles (for what blocks of content do), states (for how blocks of
content are configured), and additional properties to support assistive
technologies.

### Roles

Setting [[WAI-ARIA
roles]{.underline}](https://www.w3.org/TR/wai-aria/#roles) is
accomplished using the role attribute. These roles then specify what
certain elements and blocks of content do on a page.

+---+----------------------------------------------------------------------+
| 1 | &lt;header role=&quot;banner&quot;&gt;&#8230;&lt;/header&gt;                            |
|   |                                                                      |
| 2 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

WAI-ARIA roles break down into four different categories, including
abstract, widget, document structure, and landmark roles. For this
lesson we will focus primarily on the document structure and landmark
roles. <b>Document structure roles</b> define the organizational structure
of content on a page, while <b>landmark roles</b> define the regions of a
page. Specific role values for each of these categories are broken out
below.

### Document Structure Roles

-   article

-   columnheader

-   definition

-   directory

-   document

-   group

-   heading

-   img

-   list

-   listitem

-   math

-   note

-   presentation

-   region

-   row

-   rowheader

-   separator

-   toolbar

### Landmark Roles

-   application

-   banner

-   complementary

-   contentinfo

-   form

-   main

-   navigation

-   search

HTML5 introduced a handful of new structural elements which commonly
match up against the document structure and landmark roles. Exactly how
these roles match up against specific elements may be seen below. Please
notice, the header and footer elements do not have an implied role, and
the acceptable roles for these elements may only be used <b>once</b> per
page. That said, if you have multiple header and footer elements on a
page the banner and contentinfo roles should be applied on the elements
directly tied to the document from a top level perspective, not elements
nested within other regions of the document structure.

+------+-----------+---------------------------------------------------+
|      | *         | <b>[Acceptable Roles]{.mark}</b>                  |
|      |           |                                                   |
|      |           |                                                   |
|      |           |                                                   |
|      |           |                                                   |
+======+===========+===================================================+
| art  | article   | application, article, document, or main           |
| icle |           |                                                   |
+------+-----------+---------------------------------------------------+
| a    | comp      | complementary, note, or search                    |
| side | lementary |                                                   |
+------+-----------+---------------------------------------------------+
| fo   | ---       | contentinfo (Only once per page)                  |
| oter |           |                                                   |
+------+-----------+---------------------------------------------------+
| he   | ---       | banner (Only once per page)                       |
| ader |           |                                                   |
+------+-----------+---------------------------------------------------+
| nav  | n         | navigation                                        |
|      | avigation |                                                   |
+------+-----------+---------------------------------------------------+
| sec  | region    | alert, alertdialog,                               |
| tion |           | application, contentinfo, dialog, document, log,  |
|      |           |                                                   |
|      |           | main, marquee, region, search, or status          |
+------+-----------+---------------------------------------------------+

Combining the elements with their matched roles in HTML5 would look like
the following code snippet.

+---+----------------------------------------------------------------------+
| 1 | &lt;header role=&quot;banner&quot;&gt;                                           |
|   |                                                                      |
| 2 | &lt;nav role=&quot;navigation&quot;&gt;&#8230;&lt;/nav&gt;                              |
|   |                                                                      |
| 3 | &lt;/header&gt;                                                          |
|   |                                                                      |
| 4 | &lt;article role=&quot;article&quot;&gt;                                         |
|   |                                                                      |
| 5 | &lt;section role=&quot;region&quot;&gt;&#8230;&lt;/section&gt;                          |
|   |                                                                      |
| 6 | &lt;/article&gt;                                                         |
|   |                                                                      |
| 7 | &lt;aside role=&quot;complementary&quot;&gt;&#8230;&lt;/aside&gt;                       |
|   |                                                                      |
| 8 | &lt;footer role=&quot;contentinfo&quot;&gt;&#8230;&lt;/footer&gt;                       |
|   |                                                                      |
| 9 |                                                                      |
+===+======================================================================+
+---+----------------------------------------------------------------------+

<h3>States & Properties</h3>

In combination with WAI-ARIA roles there are also 
<a href="https://www.w3.org/TR/wai-aria/#states_and_properties" rel="noopener noreferrer" target="_blank">
states and properties</a> which help inform assistive technologies how content 
is configured. Like roles, the states and properties are broken into four 
categories, including <b>widget attributes</b>, <b>live region attributes</b>, 
<b>drag-and-drop attributes</b>, and <b>relationship attributes</b>.

The <b>widget attributes</b> support widget roles and are specific to the
user interface and where users take actions. The <b>live region
attributes</b> may be applied to any element and are used to indicate
content changes for assistive technologies, on page alerts and
notifications for example. <b>Drag-and-drop attributes</b> supply
information about drag-and-drop interface elements and provide alternate
behaviors to assistive technologies. Lastly, <b>relationship
attributes</b> outline the relationship between elements when the document
structure cannot be determined.

<details>
  <summary>Resources</summary>

  <h3>Resources & Links</h3>

  <ul>
    <li><a href="https://developers.whatwg.org/text-level-semantics.html" rel="noopener noreferrer" target="_blank">
      Text-Level Semantics</a> via WHATWG</li>
    <li><a href="http://microformats.org/wiki/existing-rel-values" rel="noopener noreferrer" target="_blank">
      Existing rel Values</a> via Microformats.org</li>
    <li><a href="http://schema.org/docs/schemas.html" rel="noopener noreferrer" target="_blank">
      Organization of Schemas</a> via Schema.org</li>
    <li><a href="http://diveintohtml5.info/extensibility.html" rel="noopener noreferrer" target="_blank">
      Microdata</a> via Dive Into HTML5</li>
    <li><a href="http://www.w3.org/WAI/intro/aria" rel="noopener noreferrer" target="_blank">
      WAI-ARIA Overview</a>) via W3.org</li>
    <li><a href="https://www.w3.org/TR/wai-aria/#roles" rel="noopener noreferrer" target="_blank">
      The Roles Model</a> via W3.org</li>
  </ul>

</details>

[<b>Lesson 9</b>] <a href="https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/" rel="noopener noreferrer" target="_blank">
  Feature Support &amp; Polyfills</a>

...the end.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 0x/0x.  (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image00x.png"
    style="width:40%"
    alt="." />
  <img src="./images/image00x.png"
    style="width:40%"
    alt="." />
</p>
