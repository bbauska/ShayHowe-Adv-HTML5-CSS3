<!--
---
title: "Shay & Howe's Advanced HTML and CSS"
author: "Brian Bauska (bbauska)"
date last editted: "3/27/2024 5+pm"
output:
  markdown:
  with some style
---
-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h1 align="center" width="100%">Advanced HTML &amp; CSS</h1>
<h6 align="center">by Shay-Howe</h6>

<h2 align="center">Lesson 1: Performance &amp; Organization</h2>

<h3>In this Lesson 1</h3>

<h4>HTML</h4>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#minify-compress-files"
    rel="noopener noreferrer" target="_blank">
	Minify & Compress Files</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#cache-common-files"
    rel="noopener noreferrer" target="_blank">
    Cache Common Files</a></li>
</ul>

<h4>CSS</h4>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#strategy-structure" 
    rel="noopener noreferrer" target="_blank">
    Strategy &amp; Structure</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#performance-driven-selectors" 
    rel="noopener noreferrer" target="_blank">
	Performance Driven Selectors</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#reusable-code" 
    rel="noopener noreferrer" target="_blank">
	Reusable Code</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/#reduce-http-requests" 
    rel="noopener noreferrer" target="_blank">
	Reduce HTTP Requests</a></li>
</ul>

Having the ability to <a href="https://learn.shayhowe.com/html-css/writing-your-best-code/" 
rel="noopener noreferrer" target="_blank">write HTML and CSS</a> with a solid 
understanding is a great expertise to have. As a website's code base and traffic 
grows, a new skill set comes into play, one that is extremely important to both 
development time and user experience. Knowing the fundamentals of website 
<a href="http://developer.yahoo.com/performance/rules.html" 
rel="noopener noreferrer" target="_blank">performance</a> 
and organization can go a long way.

The organization and architecture of a code base can greatly affect not
only the speed of development, but also the speed at which pages render.
Both of which can be sizeable concerns not only for developers but also
users. Taking the time to design the right structure for a code base,
and identify how all of the different components will work together, can
speed up production and make for a better experience all around.

Additionally, taking a few small steps to improve the performance of a
website can pay off in dividends. <a href="https://www.stevesouders.com/blog/2012/02/10/the-performance-golden-rule/" 
rel="noopener noreferrer" target="_blank">Website performance</a> 
greatly resembles the 80/20 rule, where 20% of the optimizations will speed up
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
 1  # Base
 2    -- normalize.css
 3    -- layout.css
 4    -- typography.css
 5  
 6  # Components
 7    -- alerts.css
 8    -- buttons.css
 9    -- forms.css
 10   -- list.css
 11   -- nav.css
 12   -- tables.css
 13  
 14 # Modules
 15   -- aside.css
 16   -- footer.css
 17   -- header.css
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

<h4>Object Oriented CSS</h4>

The <a href="http://oocss.org/" rel="noopener noreferrer" target="_blank">
Object Oriented CSS</a> methodology was pioneered by Nicole Sullivan in her 
work with writing styles for larger websites. Object Oriented CSS identifies 
two principles that will help build scalable websites with a strong architecture 
and a reasonable amount of code. These two principles include:

<ul>
  <li>Separate structure from skin</li>
  <li>Separate content from container</li>
</ul>

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

<h4>Scalable & Modular Architecture for CSS</h4>

Along the same line of Object Oriented CSS is the <a href="http://smacss.com/" 
rel="noopener noreferrer" target="_blank">Scalable and Modular Architecture for 
CSS</a> methodology developed by Jonathan Snook. The Scalable and Modular 
Architecture for CSS promotes breaking up styles into <b>five</b> core categories, 
including:

<ul>
  <li>Base</li>
  <li>Layout</li>
  <li>Module</li>
  <li>State</li>
  <li>Theme</li>
</ul>

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

<h4>HTML</h4>

```
 1  <div class="alert is-error">
 2    <p>...</p>
 3  </div>
 4  
```

<h4>CSS</h4>

```
 1  .alert {...}
 2  .alert.is-error {...}
 3  .alert p {...}
 4  .alert.is-error p {...}
 5  
```

In the example above the alert class falls into the module category
while the is-error class falls into the state category. Styles from each
of these categories are then inherited as necessary.

<h4>Choosing a Methodology</h4>

Choosing which methodology to use, if any, is completely 
<a href="http://viget.com/inspire/css-squareoff" rel="noopener noreferrer" 
target="_blank">up to you</a> and what you feel is best for a given website. 
Generally speaking, a solid mix of both OOCSS and SMACSS works well, borrowing 
principles from each methodology as you prefer.

<h4>Performance Driven Selectors</h4>

One functionality of CSS often abused without awareness
are <a href="http://csswizardry.com/2011/09/writing-efficient-css-selectors/" 
rel="noopener noreferrer" target="_blank">selectors</a>. Much of the attention 
within CSS is given to properties and values. So long as these styles are applied 
to the correct element, everything looks to be fine. This is a very poor assumption. 
How elements are selected within CSS affects performance, including how fast a page
renders as well as how practical and modular the styles are in the overall site 
architecture.

<h4>Keep Selectors Short</h4>

There are a handful of benefits to keeping CSS selectors as short as
possible. These include minimizing specificity, allowing for better
inheritance and portability, and improving efficiency. Long, over
qualified selectors reduce performance because they force the browser to
render each individual selector type from right to left. They also put a
burden on all other selectors to be more specific.

```
 1  /* Bad */
 2  header nav ul li a {...}
 3  
 4  /* Good */
 5  .primary-link {...}
 6  
 7  /* Bad */
 8  button strong span {...}
 9  button strong span .callout {...}
 10 
 11 /* Good */
 12 button span {...}
 13 button .callout {...}
 14 
```

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

<h4>Favor Classes</h4>

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

```
 1  /* Bad */
 2  #container header nav {...}
 3 
 4  /* Good */
 5  .primary-nav {...}
 6 
 7  /* Bad */
 8  article.feat-post {...}
 9 
 10 /* Good */
 11 .feat-post {...}
 12
```

It is also worth noting, stay away from ID selectors where possible as
they are overly specific and do not allow for any repetition. At the end
of the day using an ID isn't a whole lot different than
using !important.

<h4>Reusable Code</h4>

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

<details>
  <summary>CSS Examples</summary>
  
```
 1  /* Bad */
 2  .news { 
 3    background: #eee;  
 4    border-radius: 5px;
 5    box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25); 
 6  }
 7  .social {
 8    background: #eee;
 9    border-radius: 5px;
 10   box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
 11 }
 12
 13 /* Good */
 14 .news,
 15 .social {
 16   background: #eee;
 17   border-radius: 5px;
 18   box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
 19 }
 20 
 21 /* Even Better */
 22 .modal {
 23   background: #eee;
 24   border-radius: 5px;
 25   box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
 26 }
 27 
```

</details>

Which approach you take doesn't make a huge difference, so long as code
is being shared and reused, and the overall file size is reduced.

<h4>Minify & Compress Files</h4>

Simply removing duplicate and unnecessary code is the best way to cut
down on file size, however there are additional ways. One way includes 
<a href="http://www.hanselman.com/blog/TheImportanceAndEaseOfMinifyingYourCSSAndJavaScriptAndOptimizingPNGsForYourBlogOrWebsite.aspx" 
rel="noopener noreferrer" target="_blank">minifying</a> and compressing 
files, such as HTML, CSS, and JavaScript files. Additionally, images may be 
compressed, removing any unnecessary comments and color profiles.

<h4>gzip Compression</h4>

One of the more popular types of file compression is called gzip. gzip
compression takes common files, including HTML, CSS, JavaScript, and so
forth, and identifies similar strings to compress down. The more
matching strings identified, the smaller the file can be compressed,
thus sending a smaller file from the server to the browser.

Setting up gzip is fairly painless, and the <a href="http://html5boilerplate.com/" 
rel="noopener noreferrer" target="_blank">HTML5 Boilerplate</a> team has done a 
great job of getting this going. To gzip files an .htaccess file needs to be added 
to the root directory of the web server, labeling the specific files to be gzipped. 
The dot at the beginning of the file name is correct, as the .htaccess file is a 
hidden file.

Within the HTML5 Boilerplate Apache Server Configs, they instruct which
files gzip compression should be applied to. Keep in mind, the code for
this compression should live within a .htaccess file in the root
directory of the web server. Additionally, it is worth noting
that .htaccess files only work on Apache web servers, which need to have
the following modules enabled.

<ul>
  <li>mod_setenvif.c</li>
  <li>mod_headers.c</li>
  <li>mod_deflate.c</li>
  <li>mod_filter.c</li>
  <li>mod_expires.c</li>
  <li>mod_rewrite.c</li>
</ul>

Generally speaking this isn't an issue, and some web servers may even
set up compression for you. After all, it is in the web server's best
interest to compress files too.

<h4>Measuring Compression</h4>

Within the Google Chrome web browser the web inspector gives a plethora
of data around performance, particularly within the Network tab.
Additionally, there are a few websites that help identify if gzip
compression is enabled.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 01. gzip overview screenshot (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image001.png"
  style="width:40%"
  alt="gzip Overview Screenshot." />
</p>

<h6>Fig. 1</h6>

The Network tab identifies each file loaded within the browser and displays the 
file size and load time. Notice how gzipping has reduced the file sizes by around 60%.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 02. gzip detail screenshot (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image002.png"
  style="width:40%"
  alt="gzip Detail Screenshot." />
</p>

<h6>Fig. 1</h6>

Looking at a file specifically identifies what type of compression encoding the 
browser supports. In this case gzip, deflate, and sdch are all supported as noted 
within the request headers.

Looking at the response headers identifies that the file was sent using the gzip 
compression encoding.

<h4>Image Compression</h4>

Cutting down the size of a text file helps, but you get even better results by 
compressing the file size of images. The total file size of all the images across 
a website can quickly add up, and compressing images will greatly help keep the 
file size under control.

Many people steer away from compressing images in fear that compression involves 
reducing the quality of the image itself. For the most part this is incorrect, 
and images can be compressed in a lossless fashion, allowing unnecessary color 
profiles and comments to be removed from the image without changing the quality 
of the image at all.

There are a handful of tools to help compress images, two of the best
are <a href="http://imageoptim.com/" rel="noopener noreferrer" target="_blank">
ImageOptim</a> for Mac and <a href="http://pnggauntlet.com/" 
rel="noopener noreferrer" target="_blank">PNGGauntlet</a> for Windows. Both of 
these services compress the most commonly used image formats, specifically JPG 
and PNG files.

<h4>Image Compression Demo</h4>

<h4>Uncompressed, 455kb</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 03. uncompressed ocean picture (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image003.jpeg"
  style="width:40%"
  alt="Uncompressed Ocean Picture." />
</p>

<h4>Compressed, 401kb</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 04. compressed ocean picture (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image004.jpeg"
  style="width:40%"
  alt="Compressed Ocean Picture." />
</p>

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 05. imageoptim screenshot (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image005.png"
  style="width:40%"
  alt="ImageOptim Screenshot." />
</p>

<h6>Fig. 1</h6>

Using ImageOptim the above image was reduced over 14% without any
reduction or loss in quality.

It should also be noted, setting an image's dimensions in HTML by way of
the height and width attributes <b>does help</b> render the page quicker,
setting aside the appropriate space for the image. Understand, these
attributes are to only be used to identify the exact image dimensions
and not to shrink an image. Using a larger image, then scaling it down
with the height and width attributes is bad practice as it loads more
data than necessary.

```
 1  <img src="ocean.jpg" height="440" width="660" alt="Oceanview">
 2  
```

<h4>Reduce HTTP Requests</h4>

Next to file size, the number of HTTP requests a website makes is one of
the largest performance pitfalls. Each time a request is made to the
server the page load time increases. Some request have to finish before
others can start, and too many request can bloat the server.

<h4>Combine Like Files</h4>

One way, and perhaps the easiest way, to reduce the number of HTTP
requests is to combine like files. Specifically, combine all of the CSS
files into one and all of the JavaScript files into one. Combining these
files then compressing them creates one, hopefully small, HTTP request.

```
 1  <!-- Bad -->
 2  <link href="css/reset.css" rel="stylesheet">
 3  <link href="css/base.css" rel="stylesheet">
 4  <link href="css/site.css" rel="stylesheet">
 5  
 6  <!-- Good -->
 7  <link href="css/styles.css" rel="stylesheet">
 8  
```

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

<h4>Image Sprites</h4>

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
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 06. menu sprite (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image006.png"
  style="width:40%"
  alt="Menu Sprite." />
</p>

<h6>Fig. 1</h6>

Here is a sprite for a text editor menu, outlined with guides for
reference of how the images background position will change.

Using the image sprite above, a menu can be created by using the image
sprite as a background on the span element. Then, using classes to
change the background position of the image sprite, different icons can
be shown accordingly.

<h5>HTML</h5>

```
 1  <ul>
 2    <li><a href="#"><span class="bold">Bold Text</span></a></li>
 3    <li><a href="#"><span class="italic">Italicize 4 Text</span></a></li>
 4    <li><a href="#"><span class="underline">Underline Text</span></a></li>
 5    <li><a href="#"><span class="size">Size 7  Text</span></a></li>
 6    <li><a href="#"><span class="bullet">Bullet Text</span></a></li>
 7    <li><a href="#"><span class="number">Number 1  Text</span></a></li>
 8    <li><a href="#"><span class="quote">Quote 1  Text</span></a></li>
 9    <li><a href="#"><span class="left">Left Align 1  Text</span></a></li>
 10   <li><a href="#"><span class="center">Center Align 1  Text</span></a></li>
 11   <li><a href="#"><span class="right">Right Align Text</span></a></li>
 12 </ul>
 13 
```

<h4>CSS</h4>

```
 1  ul {
 2    margin: 0;
 3    padding: 0;
 4  }
 5  li {
 6    float: left;
 7    list-style: none;
 8    margin: 2px;
 9  }
 10 li a {
 11   background: linear-gradient(#fff, #eee);
 12   border: 1px solid #ccc;
 13   border-radius: 3px;
 14   display: block;
 15   padding: 3px;
 16 }
 17 li a:hover {
 18   border-color: #999;
 19 }
 20 li span {
 21   background: url("sprite.png") 0 0 no-repeat;
 22   color: transparent;
 23   display: block;
 24   font: 0/0 a;
 25   height: 16px;
 26   width: 16px;
 27 }
 28 .italic {
 29   background-position: -16px 0;
 30 }
 31 .underline { 
 32   background-position: -32px 0;
 33 }
 34 .size { 
 35   background-position: -48px 0;
 36 }
 37 .bullet {
 38   background-position: -64px 0;
 39 }
 40 .number {
 41   background-position: -80px 0;
 42 }
 43 .quote {
 44   background-position: -96px 0;
 45 }
 46 .left {
 47   background-position: -112px 0;
 48 }
 49 .center {
 50   background-position: -128px 0;
 51 }
 52 .right {
 53   background-position: -144px 0;
 54 }
 55 
```

<h4>Image Sprites Demo</h4>

<h4>Image Data URI</h4>

Additionally, instead of spriting images, the encoded data for an image
can be included within HTML and CSS directly by way of the 
<a href="https://css-tricks.com/data-uris/" rel="noopener noreferrer" target="_blank">
data URI</a>, removing the need for a HTTP request all together. Using the image 
data URI works great for small images, likely to never change, and where the HTML 
and CSS can be heavily cached. There are, however, a couple of problems with data
URIs. They can be difficult to change and maintain, leading to having to generate 
another encoding. And, they don't work in older browsers, specifically Internet 
Explorer 7 and below.

If using data URIs helps cut down a few HTTP requests, and the HTML or CSS can 
be heavily cached, the benefits tend to outweigh the risk. A few tools to help 
generate data URIs include 
<a href="http://websemantics.co.uk/online_tools/image_to_data_uri_convertor/" 
rel="noopener noreferrer" target="_blank">converters</a> and 
<a href="http://www.patternify.com/" rel="noopener noreferrer" target="_blank">
pattern generators</a>. Be careful though, and always double check to see that 
the actual data URI is less weight than the actual image.

<h5>HTML</h5>

```
 1  <img height="100" width="660" alt="Rigged Pattern" src="data:image/png;base64,
 2  iVBORw0KGgoAAAANSUhEUgAAAAoAAAAICAYAAADA+m62AAAAPUlEQVQYV2NkQAO6m73+X/bdxoguji 
 3  IAU4RNMVwhuiQ6H6wQl3XI4oy4FMHcCJPHcDS6J2A2EqUQpJ
 4  hohQAyIyYy0nBAGgAAAABJRU5ErkJggg==">
 5  
```

<h5>CSS</h5>

```
 1  div {
 2  background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAICAYAA 
 3  ADA+m62AAAAPUlEQVQYV2NkQAO6m73+X/bdxogujiIAU4RNMVwhuiQ6H6wQl3XI4oy4F
 4  MHcCJPHcDS6J2A2EqUQpJhohQAyIyYy0nBAGgAAAABJRU5ErkJggg==") repeat;
 5 }
```

<h4>Image Data URI Demo</h4>

<h4>Cache Common Files</h4>

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

```
 1  ExpiresByType text/css "access plus 1 year"
 2  ExpiresByType application/javascript "access plus 1 year"
 3  
```

Changing the "access plus 1 year" value to "access plus 1 week" is
better suited for CSS and JavaScript files that are changing weekly but
are not version controlled with separate file names. For accepted
expires header values reference the mod_expires 
<a href="http://httpd.apache.org/docs/current/mod/mod_expires.html" 
rel="noopener noreferrer" target="_blank">syntax</a>.

<h4>Resources & Links</h4>

<ul>
  <li><a href="http://developer.yahoo.com/performance/rules.html" 
    rel="noopener noreferrer" target="_blank">
	Best Practices for Speeding Up Your Web Site</a> via Yahoo! Developer Network</li>
  <li><a href="https://www.stevesouders.com/blog/2012/02/10/the-performance-golden-rule/">
    Rules for Faster-Loading Web  Sites</a> via Steve Sounders</li>
  <li><a href="http://viget.com/inspire/css-squareoff">
    CSS Strategy Square-off</a> via Viget Labs</li>
  <li><a href="http://csswizardry.com/2011/09/writing-efficient-css-selectors/">
    Writing Efficient CSS Selectors</a> via Harry Roberts</li>
  <li><a href="http://www.hanselman.com/blog/TheImportanceAndEaseOfMinifyingYourCSSAndJavaScriptAndOptimizingPNGsForYourBlogOrWebsite.aspx">
    Minifying and Optimizing Files</a> via Scott Hanselman</li>
  <li><a href="http://html5boilerplate.com/">HTML5 Boilerplate</a></li>
  <li><a href="https://css-tricks.com/data-uris/">
    Data URIs</a> via CSS-Tricks</li>
</ul>

<b>Lesson 1</b> <a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/" 
rel="noopener noreferrer" target="_blank">Performance &amp; Organization</a>
<b>Lesson 3</b> <a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/" 
rel="noopener noreferrer" target="_blank">Complex Selectors</a>



<h2 align="center">[Lesson 2] Detailed Positioning</h2>

<h3>In this Lesson 2</h3>

<h4>CSS</h4>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/#containing-floats" 
    rel="noopener noreferrer" target="_blank">
    Containing Floats</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/#position-property" 
    rel="noopener noreferrer" target="_blank">
    Position Property</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/#z-index-property" 
    rel="noopener noreferrer" target="_blank">
    Z-Index Property</a></li>
</ul>

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

<h4>Containing Floats</h4>

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

<h4>What is the DOM?</h4>

The DOM, or Document Object Model, is an API for HTML and XML documents
which provides their structural representation. In our case, we are
speaking specifically to HTML documents, thus the DOM represents all of
the different elements and their relationship to each other.

The representation can be considered a tree of sorts, with each element
having a different relationship with those around it. Elements nested
inside others have a parent and child relationship while elements that
share the same parent have a sibling relationship.

While <a href="https://css-tricks.com/all-about-floats/" 
rel="noopener noreferrer" target="_blank">floats</a> do provide quite a bit of 
fire power, they do come with a few of their own problems. The most popular 
problem involves a parent element that contains numerous floated elements. 
Content on the page will respect the size and placement of the floated children 
element, but these floated elements no longer impact the outer edges of the 
parent container. In this event the parent element loses context of exactly what 
it contains and collapses, thus giving the parent element a height of 0 and 
ignoring various other properties. A lot of times this may go unnoticed, 
specifically when the parent element doesn't have any styles tied to it and the 
nested elements look to have aligned correctly.

Should the nested elements not line up correctly, styling errors may
appear. Taking a look at the demo below, the .box-set division should
have a light gray background, however the background is not seen as all
of the elements nested within it are floated. Upon inspecting
the .box-set division you will see it has a height of 0.

<h4>HTML</h4>

```
 1  <div class="box-set">
 2    <figure class="box">Box 1</figure>
 3    <figure class="box">Box 2</figure>
 4    <figure class="box">Box 3</figure>
 5  </div>
 6  
```

<h4>CSS</h4>

```
 1  .box-set {
 2    background: #eaeaed;
 3  }
 4  .box {
 5    background: #2db34a;
 6    float: left;
 7    margin: 1.858736059%;
 8    width: 29.615861214%;
 9  }
 10 
```

<h4>Containing Floats Demo</h4>

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

<h4>The Overflow Technique</h4>

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

```
 1  .box-set {
 2    overflow: auto;
 3  }
 4  
```

<h4>Overflow Technique Demo</h4>

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

<h4>Overflow Pitfall Demo</h4>

<h4>The Clearfix Technique</h4>

Depending on the context of the floated elements a better technique to
contain floats may be
the [clearfix](http://nicolasgallagher.com/micro-clearfix-hack/) technique.
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

Adding the *zoom property to the parent element triggers
the hasLayout mechanism specifically within Internet Explorer 6 and 7,
which determines how elements should draw and bound their content, as
well as how elements should interact with and relate to other elements.

Taking the same example from above you can see how the floats are
contained and the elements are able to live outside of the parent
element.

```
 1  .box-set:before,
 2  .box-set:after {
 3    content: "";
 4    display: table;
 5  }
 6  .box-set:after {
 7    clear: both;
 8  }
 9  .box-set {
 10   *zoom: 1;
 11 }
 12  
```

<h4>Clearfix Technique Demo</h4>

<h4>Effectively Containing Floats</h4>

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

```
 1  .group:before,
 2  .group:after {
 3    content: "";
 4    display: table;
 5  }
 6  .group:after {
 7    clear: both;
 8  }
 9  .group {
 10   *zoom: 1;
 11  }
 12 
```

<h4>Single Pseudo-Elements</h4>

It is worth noting only one :before and one :after pseudo-element are
allowed per element, for the time being. When trying to use the clearfix
technique with other :before and :after pseudo-element content you may
not achieve the desired outcome.

In the examples above, the clearfix styles would not live under
the box-set class. Instead, the class of group would need to be added to
the parent element containing the floats.

<h4>Position Property</h4>

Occasionally you need more control over the position of an element, more
than a float can provide, in which case the position property comes into
play. The position property accepts five different values, each of which
provide different ways to [uniquely
position](http://www.alistapart.com/articles/css-positioning-101/) an
element.

<h4>Position Static</h4>

Elements by default have the position value of static, meaning they
don't have, nor will they accept, any specific [box offset
properties](https://learn.shayhowe.com/html-css/opening-the-box-model/).
Furthermore, elements will be positioned as intended, with their default
behaviors.

In the demonstration below, all the boxes are stacked one on top of the
other as they are block level elements and are not floated in any
specific direction.

<h4>HTML</h4>

```
 1  <div class="box-set">
 2    <figure class="box box-1">Box 1</figure>
 3    <figure class="box box-2">Box 2</figure>
 4    <figure class="box box-3">Box 3</figure>
 5    <figure class="box box-4">Box 4</figure>
 6  </div>
 7  
```

<h4>CSS</h4>

```
 1  .box-set {
 2    background: #eaeaed;
 3  }
 4  .box {
 5    background: #2db34a;
 6    height: 80px;
 7    width: 80px;
 8  }
 9  
```

<h4>Position Static Demo</h4>

<h4>Position Relative</h4>

The relative value for the position property is very similar to that of
the static value. The primary difference is that the relative value
accepts the box offset properties top, right, bottom, and left. These
box offset properties allow the element to be precisely positioned,
shifting the element from its default position in any direction.

<h4>How Box Offset Properties Work</h4>

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

<h4>HTML</h4>

```
 1  <div class="box-set">
 2    <figure class="box box-1">Box 1</figure>
 3    <figure class="box box-2">Box 2</figure>
 4    <figure class="box box-3">Box 3</figure>
 5    <figure class="box box-4">Box 4</figure>
 6  </div>
 7  
```

<h4>CSS</h4>

```
 1  .box-set {
 2    background: #eaeaed;
 3  }
 4  .box {
 5    background: #2db34a;
 6    height: 80px;
 7    position: relative;
 8    width: 80px;
 9  }
 10 .box-1 {
 11   top: 20px;
 12 }
 13 .box-2 {
 14   left: 40px;
 15 }
 16 .box-3 {
 17   bottom: -10px;
 18   right: 20px;
 19 }
 20 
```

<h4>Position Relative Demo</h4>

In the event that the top and bottom box offset properties are both
declared on a relatively positioned element, the top properties will
take priority. Additionally, if both the left and right box offset
properties are declared on a relatively positioned element, priority is
given in the direction in which the language of the page is written. For
example, in English pages the left offset property is given priority,
and for Arabic pages the right offset property is given priority.

<h4>Position Absolute</h4>

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

<h4>HTML</h4>

```
 1  <div class="box-set">
 2    <figure class="box box-1">Box 1</figure>
 3    <figure class="box box-2">Box 2</figure>
 4    <figure class="box box-3">Box 3</figure>
 5    <figure class="box box-4">Box 4</figure>
 6  </div>
 7  
```

<h4>CSS</h4>

```
 1  .box-set {
 2    background: #eaeaed;
 3    height: 200px;
 4    position: relative;
 5  }
 6  .box {
 7    background: #2db34a;
 8    height: 80px;
 9    position: absolute;
 10   width: 80px;
 11 }
 12 .box-1 {
 13   top: 6%;
 14   left: 2%;
 15  }
 16 .box-2 {
 17   top: 0;
 18   right: -40px;
 19 }
 20 .box-3 {
 21   bottom: -10px;
 22   right: 20px;
 23 }
 24 .box-4 {
 25   bottom: 0;
 26 }
 27  
```

<h4>Position Absolute Demo</h4>

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

<h4>Position Fixed</h4>

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

<h4>HTML</h4>

```
 1  <div class="box-set">
 2    <figure class="box box-1">Box 1</figure>
 3    <figure class="box box-2">Box 2</figure>
 4    <figure class="box box-3">Box 3</figure>
 5    <figure class="box box-4">Box 4</figure>
 6  </div>
 7 
```

<h4>CSS</h4>

```
 1  .box {
 2    background: #2db34a;
 3    height: 80px;
 4    position: fixed;
 5    width: 80px;
 6  }
 7  .box-1 {
 8    top: 6%;
 9    left: 2%;
 10 }
 11 .box-2 {
 12   top: 0;
 13   right: -40px;
 14 }
 15 .box-3 {
 16   bottom: -10px;
 17   right: 20px; 
 18 } 
 19 .box-4 {
 20   bottom: 0;
 21 }
 22  
```

<h4>Position Fixed Demo</h4>

<h4>Fixed Header or Footer</h4>

One of the most common uses of fixed positioning is to build a fixed
header, or footer, anchored to one side of a page. As a user scrolls the
element stays prevalent, always within the viewport for users to
interact with.

The code and demonstration below outline how this may be achieved.
Notice how both left and right box offset properties are declared. This
allows the footer to span the entire width of the bottom of the page,
and it does so without disrupting the box model, allowing margins,
borders, and padding to be applied freely.

<h4>HTML</h4>

```
 1  <footer>Fixed Footer</footer>
 2  
```

<h4>CSS</h4>

```
 1  body {
 2    background: #eaeaed;
 3  }
 4  footer {
 5    background: #2db34a;
 6    bottom: 0;
 7    left: 0;
 8    position: fixed;
 9    right: 0;
 10 }
 11 
```

<h4>Fixed Footer Demo</h4>

<h4>Z-Index Property</h4>

By nature web pages are often considered to be two dimensional,
displaying elements upon a x and y axis. However when you begin to
position elements they are occasionally placed on top of one another. To
change the order of 
<a href="http://www.impressivewebs.com/a-detailed-look-at-the-z-index-css-property/" 
rel="noopener noreferrer" target="_blank">how these elements are stacked</a>, 
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

<h4>HTML</h4>

```
 1  <div class="box-set">
 2  <figure class="box box-1">Box 1</figure>  
 3  <figure class="box box-2">Box 2</figure>  
 4  <figure class="box box-3">Box 3</figure>  
 5  <figure class="box box-4">Box 4</figure>  
 6  </div>
 7 
```

<h4>CSS</h4>

```
 1  .box-set {
 2    background: #eaeaed;
 3    height: 160px;
 4    position: relative;
 5  }
 6  .box {
 7    background: #2db34a;
 8    border: 2px solid #ff7b29;
 9    position: absolute;
 10  }
 11 .box-1 {
 12   left: 10px;
 13   top: 10px;
 14 }
 15 .box-2 {
 16   bottom: 10px;
 17   left: 70px;
 18   z-index: 3;
 19 }
 20 .box-3 {
 21   left: 130px;
 22   top: 10px;
 23   z-index: 2;
 24 }
 25 .box-4 {
 26   bottom: 10px;
 27   left: 190px;
 28   z-index: 1;
 29 }
 30  
```

<h4>Z-Index Demo</h4>

<h4>Resources & Links</h4>

<ul>
  <li><a href="https://css-tricks.com/all-about-floats/" 
    rel="noopener noreferrer" target="_blank">
	All About Floats</a> via CSS-Tricks</li>
  <li><a href="http://nicolasgallagher.com/micro-clearfix-hack/" 
    rel="noopener noreferrer" target="_blank">
	A New Micro Clearfix Hack</a> via Nicolas Gallagher</li>
  <li><a href="http://www.alistapart.com/articles/css-positioning-101/" 
    rel="noopener noreferrer" target="_blank">
	CSS Positioning 101</a> via A List Apart</li>
  <li><a href="http://www.impressivewebs.com/a-detailed-look-at-the-z-index-css-property/"
    rel="noopener noreferrer" target="_blank">
	A Detailed Look at the z-index CSS Property</a> via Impressive Webs</li>
</ul>

<b>Lesson 1</b> <a href="https://learn.shayhowe.com/advanced-html-css/performance-organization/"
  rel="noopener noreferrer" target="_blank">
  Performance & Organization</a>
<b>Lesson 3</b> <a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/" 
  rel="noopener noreferrer" target="_blank">
  Complex Selectors</a>

<h2 align="center">[Lesson 3] Complex Selectors</h2>

<h3>In this Lesson 3</h3>

<h4>CSS</h4>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/#common-selectors"
    rel="noopener noreferrer" target="_blank">
    Common Selectors</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/#child-selectors"
    rel="noopener noreferrer" target="_blank">
    Child Selectors</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/#sibling-selectors"
    rel="noopener noreferrer" target="_blank">
    Sibling Selectors</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/#attribute-selectors"
    rel="noopener noreferrer" target="_blank">
    Attribute Selectors</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/#pseudo-classes"
    rel="noopener noreferrer" target="_blank">
    Pseudo-classes</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/#pseudo-elements"
    rel="noopener noreferrer" target="_blank">
    Pseudo-elements</a></li>
</ul>

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
discuss [selectors](http://net.tutsplus.com/tutorials/html-css-techniques/the-30-css-selectors-you-must-memorize/),
old and new, and how to best put them to use.

<h4>Common Selectors</h4>

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

<h4>CSS</h4>

```
 1  h1 {...}
 2  .tagline {...}
 3  #intro {...}
 4  
```

<h4>HTML</h4>

```
 1  <section id="intro">
 2    <h1>...</h1>
 3    <h2 class="tagline">...</h2>
 4  </section>
 5  
```

<h4>Common Selectors Overview</h4>

  | <b>Example</b>|<b>Classification</b> | <b>Explanation</b> |
  -----------|-----------------------------|-----------------------------------------------------|
  | h1       | Type Selector | Selects an element by its type.  |
  | .tagline | Class         | Selects an element by the class attribute value, which may be reused |
  |          | Selector      | multiple times per page. |
  | #intro   | ID Selector   | Selects an element by the ID attribute value, which is unique and to |
  |          |               | only be used once per page. |

<h4>Child Selectors</h4>

Child selectors provide a way to select elements that fall within one
another, thus making them children of their parent element. These
selections can be made two different ways, using either descendant or
direct child selectors.

<h4>Descendant Selector</h4>

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

<h4>CSS</h4>

```
 1  article h2 {...}  
 2 
```

<h4>HTML</h4>

```
 1  <h2>...</h2>  
 2  <article>
 3    <h2>This heading will be selected</h2>
 4    <div> 
 5      <h2>This heading will be selected</h2>
 6    </div>
 7  </article> 
 8 
```

<h4>Direct Child Selector</h4>

Sometimes descendant selectors go a bit overboard, selecting more than
hoped. At times only the direct children of a parent element need to be
selected, not every instance of the element nested deeply inside of an
ancestor. In this event the direct child selector may be used by placing
a greater than sign, >, between the parent element and child element
within the selector.

For example, article > p is a direct child selector only
identifying p elements that fall directly within an article element.
Any p element placed outside of an article element, or nested inside of
another element other than the article element, will not be selected.

Below, the paragraph on line 3 is the only direct child of its parent
article, thus selected.

<h4>CSS</h4>

```
 1  article > p {...}
 2 
```

<h4>HTML</h4>

```
 1  <p>...</p> 
 2  <article>
 3    <p>This paragraph will be selected</p>
 4    <div> 
 5      <p>...</p> 
 6    </div>
 7  </article> 
 8 
```

<h4>Child Selectors Overview</h4>

  | <b>Example</b>|<b>Classification</b> | <b>Explanation</b> |
  --------------|-----------------------------|-----------------------------------------------------|
  | article h2  | Descendant   | Selects an element that resides anywhere within an    |
  |             | Selector     | identified ancestor element.                          |
  | article > p | Direct Child | Selects an element that resides immediately inside an |
  |             | Selector     | identified parent element.                            |

<h4>Sibling Selectors</h4>

Knowing how to [select
children](https://css-tricks.com/child-and-sibling-selectors/) of
an element is largely beneficial, and quite commonly seen. However
sibling elements, those elements that share a common parent, may also
need to be selected. These sibling selections can be made by way of the
general sibling and adjacent sibling selectors.

<h4>General Sibling Selector</h4>

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

<h4>CSS</h4>

```
 1  h2 ~ p {...}  
 2 
```

<h4>HTML</h4>

```
 1  <p>...</p> 
 2  <section>
 3    <p>...</p> 
 4    <h2>...</h2>  
 5    <p>This paragraph will be selected</p>
 6    <div> 
 7      <p>...</p> 
 8    </div>
 9    <p>This paragraph will be selected</p>
 10 </section> 
 11 
```

<h4>Adjacent Sibling Selector</h4>

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

<h4>CSS</h4>

```
 1  h2 + p {...}
 2 
```

<h4>HTML</h4>

```
 1  <p>...</p>
 2  <section>
 3  <p>...</p> 
 4  <h2>...</h2>  
 5  <p>This paragraph will be selected</p>
 6  <div> 
 7  <p>...</p> 
 8  </div>
 9  <p>...</p> 
 10 </section> 
 11 
```

<h4>Sibling Selectors Example</h4>

<h4>HTML</h4>

```
 1  <input type="checkbox" id="toggle"> 
 2  <label for="toggle">&#9776;</label> 
 3  <nav> 
 4  <ul>  
 5    <li><a href="#">Home</a></li>
 6    <li><a href="#">About</a></li>  
 7    <li><a href="#">Services</a></li>  
 8    <li><a href="#">Contact</a></li>
 9  </ul> 
 10 </nav>
 11 
```

<details>
  <summary>CSS</summary>

```
 1   input { 
 2     display: none;  
 3   } 
 4   label,  
 5   ul { 
 6     border: 1px solid #cecfd5;  
 7     border-radius: 6px;
 8   } 
 9   label { 
 10    color: #0087cc; 
 11    cursor: pointer;
 12    display: inline-block;
 13    font-size: 18px; 
 14    padding: 5px 9px;  
 15    transition: all .15s ease;  
 16  } 
 17  label:hover {
 18    color: #ff7b29; 
 19  } 
 20  input:checked + label {  
 21    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.15);
 22    color: #9799a7; 
 23  }
 24  nav {
 25    max-height: 0;  
 26    overflow: hidden;  
 27    transition: all .15s ease;  
 28  } 
 19    input:checked &tilde; nav {
 30    max-height: 500px; 
 31  } 
 32  ul { 
 33    list-style: none;  
 34    margin: 8px 0 0 0; 
 35    padding: 0;  
 36    width: 100px;
 37  } 
 38  li { 
 39    border-bottom: 1px solid #cecfd5; 
 40  } 
 41  li:last-child { 
 42    border-bottom: 0;  
 43  } 
 44  a {  
 45    color: #0087cc; 
 46    display: block; 
 47    padding: 6px 12px; 
 48    text-decoration: none;
 49  } 
 50  a:hover { 
 51    color: #ff7b29; 
 52  } 
 53 
```

</details>

<h4>Demo</h4>

<h4>Sibling Selectors Overview</h4>

  | <b>Example</b>|<b>Classification</b> | <b>Explanation</b> |
  --------------|-----------------------------|-----------------------------------------------------|
  | h2 ~ p | General Sibling  | Selects an element that follows anywhere after the prior          |
  |        | Selector         | element, in which both elements share the same parent.            |
  | h2 + p | Adjacent Sibling | Selects an element that follows directly after the prior element, |
  |        | Selector         | in which both elements share the same parent.                     |


<h4>Attribute Selectors</h4>

Some of the common selectors looked at early may also be defined as
attribute selectors, in which an element is selected based upon its
class or ID value. These class and ID attribute selectors are widely
used and extremely powerful but only the beginning. Other [attribute
selectors](http://www.css3.info/preview/attribute-selectors/) have
emerged over the years, specifically taking a large leap forward with
CSS3. Now elements can be selected based on whether an attribute is
present and what its value may contain.

<h4>Attribute Present Selector</h4>

The first attribute selector identifies an element based on whether it
includes an attribute or not, regardless of any actual value. To select
an element based on if an attribute is present or not, include the
attribute name in square brackets, &lbrack;&rbrack;, within a selector. 
The square brackets may or may not follow any qualifier such as an element 
type or class, all depending on the level of specificity desired.

<h4>CSS</h4>

```
 1  a[target] {...} 
 2 
```

<h4>HTML</h4>

```
 1  <a href="#" target="_blank">...</a>
 2 
```

<h4>Attribute Equals Selector</h4>

To identify an element with a specific, and exact matching, attribute
value the same selector from before may be used, however this time
inside of the square brackets following the attribute name, include the
desired matching value. Inside the square brackets should be the
attribute name followed by an equals sign, =, quotations, "", and
inside of the quotations should be the desired matching attribute value.

<h4>CSS</h4>

```
 1  a]href="http://google.com/"[ {...} 
 2 
```

<h4>HTML</h4>

```
 1  <a href="http://google.com/">...</a>  
 2 
```

<h4>Attribute Contains Selector</h4>

When looking to find an element based on part of an attribute value, but
not an exact match, the asterisk character, *, may be used within the
square brackets of a selector. The asterisk should fall just after the
attribute name, directly before the equals sign. Doing so denotes that
the value to follow only needs to appear, or be contained, within the
attribute value.

<h4>CSS</h4>

```
 1  a]href*="login"[ {...}
 2 
```

<h4>HTML</h4>

```
 1  <a href="/login.php">...</a>  
 2 
```

<h4>Attribute Begins With Selector</h4>

In addition to selecting an element based on if an attribute value
contains a stated value, it is also possible to select an element based
on what an attribute value begins with. Using a circumflex accent, &Hat;,
within the square brackets of a selector between the attribute name and
equals sign denotes that the attribute value should begin with the
stated value.

<h4>CSS</h4>

```
 1  a]href&Hat;="https://"[ {...}
 2 
```

<h4>HTML</h4>

```
 1  <a href="https://chase.com/">...</a>  
 2 
```

<h4>Attribute Ends With Selector</h4>

Opposite of the begins with selector, there is also an ends with
attribute selector. Instead of using the circumflex accent, the ends
with attribute selector uses the dollar sign, $, within the square
brackets of a selector between the attribute name and equals sign. Using
the dollar sign denotes that the attribute value needs to end with the
stated value.

<h4>CSS</h4>

```
 1  a]href$=".pdf"[ {...} 
 2 
```

<h4>HTML</h4>

```
 1  <a href="/docs/menu.pdf">...</a> 
 2 
```

<h4>Attribute Spaced Selector</h4>

At times attribute values may be spaced apart, in which only one of the
words needs to be matched in order to make a selection. In this event
using the tilde character, &tilde;, within the square brackets of a selector
between the attribute name and equals sign denotes an attribute value
that should be whitespace-separated, with one word matching the exact
stated value.

<h4>CSS</h4>

```
 1  a]rel&tilde;="tag"[ {...}
 2 
```

<h4>HTML</h4>

```
 1  <a href="#" rel="tag nofollow">...</a> 
 2 
```

<h4>Attribute Hyphenated Selector</h4>

When an attribute value is hyphen-separated, rather than
whitespace-separated, the vertical line character, &#0124;, may be used
within the square brackets of a selector between the attribute name and
equals sign. The vertical line denotes that the attribute value may be
hyphen-separated however the hyphen-separated words must begin with the
stated value.

<h4>CSS</h4>

```
 1  a]lang&#0124;="en"[ {...}
 2 
```

<h4>HTML</h4>

```
 1  <a href="#" lang="en-US">...</a> 
 2 
```

<h4>Attribute Selectors Example</h4>

<h4>HTML</h4>

```
 1  <ul>  
 2  <li><a href="#.pdf">PDF Document</a></li>
 3  <li><a href="#.doc">Word Document</a></li>  
 4  <li><a href="#.jpg">Image File</a></li>  
 5  <li><a href="#.mp3">Audio File</a></li>  
 6  <li><a href="#.mp4">Video File</a></li>  
 7  </ul>
 8 
```

<h4>CSS</h4>

```
 1  ul { 
 2  list-style: none;  
 3  margin: 0;
 4  padding: 0;  
 5  } 
 6  a {  
 7  background-position: 0 50%; 
 8  background-repeat: no-repeat;  
 9  color: #0087cc; 
 10  padding-left: 22px;
 11 text-decoration: none;
 12  } 
 13  a:hover { 
 14 color: #ff7b29; 
 15  } 
 16  a[href&$=".pdf"] {
 17 background-image: url("images/pdf.png");
 18  } 
 19  a[href$=".doc"] {
 20 background-image: url("images/doc.png");
 21  } 
 22  a[href$=".jpg"] {
 23  background-image: url("images/image.png"); 
 24  } 
 25  a[href$=".mp3"] {
 26 background-image: url("images/audio.png"); 
 27  } 
 28  a[href$=".mp4"] {
 29  background-image: url("images/video.png"); 
 30  } 
 31 
```

<h4>Demo</h4>

<h4>Attribute Selectors Overview</h4>

  | **Example** | **Classification** | **Explanation** |
  |---------------|----------------------|----------------------------------------------|
  | a[target]     | Attribute Present    | Selects an element if the given attribute is
  |               | Selector             | present. |
  | a[href="http://google.com/"] | Attribute Equals | Selects an element if the given attribute value |
  |                              | Selector         | exactly matches the value stated. |
  | a[href*="login"]             | Attribute Contains           | Selects an element if the given attribute value |
  |                              | Selector                     | contains at least one instance of the value stated |
  | a[href&Hat;="https://"] | Attribute Begins | Selects an element if the given attribute value |
  |                         | with Selector    | begins with the value stated.                   |
  | a[href$=".pdf"]         | Attribute Ends   | Selects an element if the given attribute value |
  |                         | With Selector    | ends with the value stated.                     |
  | a[rel&tilde;="tag"]     | Attribute Spaced | Selects an element if the given attribute value |
  |                         | Selector         | is whitespace-separated with one word being     |
  |                         |                  | exactly as stated.                              |
  | a[lang&#0124;="en"]     | Attribute        | Selects an element if the given attribute value |
  |                         | Hyphenated       | is hyphen-separated and begins with the word stated. |

<h4>Pseudo-classes</h4>

[Pseudo-classes](http://coding.smashingmagazine.com/2011/03/30/how-to-use-css3-pseudo-classes/) are
similar to regular classes in HTML however they are not directly stated
within the markup, instead they are dynamically populated as a result of
users' actions or the document structure. The most common pseudo-class,
and one you've likely seen before, is :hover. Notice how this
pseudo-class begins with the colon character, :, as will all other
pseudo-classes.

<h4>Link Pseudo-classes</h4>

Some of the more basic pseudo-classes include two revolving around links
specifically. The :link and :visited pseudo-classes define if a link has
or hasn't been visited. To style an anchor which has not been visited
the :link pseudo-class comes into play, where the :visited pseudo-class
styles links that a user has already visited based on their browsing
history.

```
 1  a:link {...}
 2  a:visited {...}
 3 
```

<h4>User Action Pseudo-classes</h4>

Based on a users' actions different pseudo-classes may be dynamically
applied to an element, of which include the :hover, :active,
and :focus pseudo-classes. The :hover pseudo-class is applied to an
element when a user moves their cursor over the element, most commonly
used with anchor elements. The :active pseudo-class is applied to an
element when a user engages an element, such as clicking on an element.
Lastly, the :focus pseudo-class is applied to an element when a user has
made an element the focus point of the page, often by using the keyboard
to tab from one element to another.

```
 1  a:hover {...}  
 2  a:active {...} 
 3  a:focus {...}  
 4 
```

<h4>User Interface State Pseudo-classes</h4>

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

```
 1  input:enabled {...}
 2  input:disabled {...}
 3  
```

The last two user interface element state pseudo-classes
of :checked and :indeterminate revolve around checkbox and radio button
input elements. The :checked pseudo-class selects checkboxes or radio
buttons that are, as you may expect, checked. When a checkbox or radio
button has neither been selected nor unselected it lives in an
indeterminate state, from which the :indeterminate pseudo-class can be
used to target these elements.

```
 1  input:checked {...}
 2  input:indeterminate {...}
 3  
```

<h4>Structural & Position Pseudo-classes</h4>

A handful of pseudo-classes are structural and position based, in which
they are determined based off where elements reside in the document
tree. These structural and position based pseudo-classes come in a few
different shapes and sizes, each of which provides their own unique
function. Some pseudo-classes have been around longer than others,
however CSS3 brought way of an entire new set of pseudo-classes to
supplement the existing ones.

<h3>:first-child, :last-child, &amp; :only-child</h3>


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

<h4>CSS</h4>

```
 1  li:first-child {...}
 2  li:last-child {...}
 3  div:only-child {...}
 4 
```

<h4>HTML</h4>

```
 1  <ul>
 2    <li>This list item will be selected</li>
 3    <li>
 4      <div>This div will be selected</div>
 5    </li>
 6    <li>
 7      <div>...</div>
 8      <div>...</div>
 9    </li>
 10   <li>This list item will be selected</li>
 11 </ul>
  
```

<h3>:first-of-type, :last-of-type, &amp; :only-of-type</h3>

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

<h4>CSS</h4>

```
 1  p:first-of-type {...}
 2  p:last-of-type {...}
 3  img:only-of-type {...}
 4 
```

<h4>HTML</h4>

```
 1  <article>
 2    <h1>...</h1>
 3    <p>This paragraph will be selected</p>
 4    <p>...</p>
 5    <img src="#"><!&#45;&#45; This image will be selected &#45;&#45;>
 6    <p>This paragraph will be selected</p>
 7    <h6>...</h6>
 8  </article>
 9 
```

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

<h4>Using Pseudo-class Numbers &amp; Expressions</h4>

As mentioned, using numbers outright within a pseudo-class will count
from the beginning, or end, of the document tree and select one element
accordingly. For example, the li:nth-child(4) selector will select the
fourth list item within a list. Counting begins with the first list item
and increases by one for each list item, until finally locating and
selecting the fourth item. When using a number outright it must be a
positive number.

[Expressions for
pseudo-classes](http://reference.sitepoint.com/css/understandingnthchildexpressions) fall
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

<h4>:nth-child(n) & :nth-last-child(n)</h4>

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

<h4>CSS</h4>

```
 1  li:nth-child(3n) {...}
```

<h4>HTML</h4>

```
 1  <ul>
 2    <li>...</li>
 3    <li>...</li>
 4    <li>This list item will be selected</li>
 5    <li>...</li>
 6    <li>...</li>
 7    <li>This list item will be selected</li>
 8  </ul>
```

Using a different expression within the :nth-child(n) pseudo-class will
yield a different selection. The li:nth-child(2n+3) selector, for
example, will identify every second list item starting with the third
and then onward. As a result, the list items lines 4 and 6 are selected.

<h4>CSS</h4>

```
 1  li:nth-child(2n+3) {...}
```

<h4>HTML</h4>

```
 1  <ul>
 2    <li>...</li>
 3    <li>...</li>
 4    <li>This list item will be selected</li>
 5    <li>...</li>
 6    <li>This list item will be selected</li>
 7    <li>...</li>
 8  </ul>
 9 
```

Changing the expression again, this time with a negative value, yields
new selection. Here the li:nth-child(-n+4) selector is identifying the
top four list items, leaving the rest of the list items unselected, thus
lines 2 through 5 are selected.

<h4>CSS</h4>

```
 1  li:nth-child(-n+4) {...}
 2 
```

<h4>HTML</h4>

```
 1  <ul>
 2  <li>This list item will be selected</li>
 3  <li>This list item will be selected</li>
 4  <li>This list item will be selected</li>
 5  <li>This list item will be selected</li>
 6  <li>...</li>
 7  <li>...</li>
 8  </ul>
 9 
```

Adding a negative integer before the n argument changes the selection
again. Here the li:nth-child(-2n+5) selector identifies every second
list item within the first five list items starting with the first list
item, thus the list items on lines 2, 4, and 6 are selected.

<h4>CSS</h4>

```
 1  li:nth-child(-2n+5) {...}
```

<h4>HTML</h4>

```
 1  <ul>
 2  <li>This list item will be selected</li>
 3  <li>...</li>
 4  <li>This list item will be selected</li>
 5  <li>...</li>
 6  <li>This list item will be selected</li>
 7  <li>...</li>
 8  </ul>
```

Changing from the :nth-child(n) pseudo-class to
the :nth-last-child(n) pseudo-class switches the direction of counting,
with counting starting from the end of the document tree using
the :nth-last-child(n) pseudo-class.
The li:nth-last-child(3n+2) selector, for example, will identify every
third list item starting from the second to last item in a list, moving
towards the beginning of the list. Here the list items on lines 3 and 6
are selected.

<h4>CSS</h4>

```
 1  li:nth-last-child(3n+2) {...}

```

<h4>HTML</h4>

```
 1  <ul>
 2  <li>...</li>
 3  <li>This list item will be selected</li>
 4  <li>...</li>
 5  <li>...</li>
 6  <li>This list item will be selected</li>
 7  <li>...</li>
 8  </ul>
```

<h4>:nth-of-type(n) & :nth-last-of-type(n)

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

<h4>CSS</h4>

```
 1  p:nth-of-type(3n) {...}
```

<h4>HTML</h4>

```
 1  <article>
 2    <h1>...</h1>
 3    <p>...</p>
 4    <p>...</p>
 5    <p>This paragraph will be selected</p>
 6    <h2>...</h2>
 7    <p>...</p>
 8    <p>...</p>
 9    <p>This paragraph will be selected</p>
 10 </article>
 11 
```

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

<h4>CSS</h4>

```
 1  p:nth-last-of-type(2n+1) {...}
 2  
```

<h4>HTML</h4>

```
 1  <article>
 2    <h1>...</h1>
 3    <p>...</p>
 4    <p>This paragraph will be selected</p>
 5    <p>...</p>
 6    <h2>...</h2>
 7    <p>This paragraph will be selected</p>
 8    <p>...</p>
 9    <p>This paragraph will be selected</p>
 10 </article>
 11 
```

<h4>Target Pseudo-class</h4>

The :target pseudo-class is used to style elements when an element's ID
attribute value matches that of the URI fragment identifier. The
fragment identifier within a URI can be recognized by the hash
character, #, and what directly follows it. The
URL http://example.com/index.html#hello includes the fragment identifier
of hello. When this identifier matches the ID attribute value of an
element on the page, <section id="hello"> for example, that element
may be identified and stylized using the :target pseudo-class. Fragment
identifiers are most commonly seen when using [on page
links](https://learn.shayhowe.com/html-css/getting-to-know-html/#hyperlinks),
or linking to another part of the same page.

Looking at the code below, if a user would visit a page with the URI
fragment identifier of #hello, the section with that same ID attribute
value would be stylized accordingly using the :target pseudo-class. If
the URI fragment identifier changes, and matches the ID attribute value
of another section, that new section may be stylized using the same
selector and pseudo-class from before.

<h4>CSS</h4>

```
 1  section:target {...}
 2  
```

<h4>HTML</h4>

```
 1  <section id="hello">...</section>
 2  
```

<h4>Empty Pseudo-class</h4>

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

<h4>CSS</h4>

```
 1  div:empty {...}
 2 
```

<h4>HTML</h4>

```
 1  <div>Hello</div>
 2  <div><!&#45;&#45; Coming soon &#45;&#45;></div><!&#45;&#45; This div will be 
 3  selected &#45;&#45;>
 4  <div></div><!&#45;&#45; This div will be selected &#45;&#45;>
 5  <div> </div>
 6  <div><strong></strong></div>
 7  
```

<h4>Negation Pseudo-class</h4>

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

<h4>CSS</h4>

```
 1  div:not(.awesome) {...}
 2  :not(div) {...}
 3  
```

<h4>HTML</h4>

```
 1  <div>This div will be selected</div>
 2  <div class="awesome">...</div>
 3  <section>This section will be selected</section>
 4  <section class="awesome">This section will be selected</section>
 5 
```

<h4>Pseudo-classes Example</h4>

<h4>HTML</h4>

```
 1  <table>
 2    <thead>
 3      <tr>
 4        <th>Number</th>
 5        <th>Player</th>
 6        <th>Position</th>
 7        <th>Height</th>
 8        <th>Weight</th>
 9      </tr>
 10   </thead>
 11   <tbody>
 12     <tr>
 13       <td>8</td>
 14       <td>Marco Belinelli</td>
 15       <td>G</td>
 16       <td>6-5</td>
 17       <td>195</td>
 18     </tr>
 19     <tr>
 20       <td>5</td>
 21       <td>Carlos Boozer</td>
 22       <td>F</td>
 23       <td>6-9</td>
 24       <td>266</td>
 25     </tr>
 26     ...
 27   </tbody>
 28 </table>
 29  
```


<h4>CSS</h4>

```
 1   table {
 2     border-collapse: separate;
 3     border-spacing: 0;
 4     width: 100%;
 5   }
 6   th,
 7   td {
 8     padding: 6px 15px;
 9   }
 10  th {
 11    background: #42444e;
 12    color: #fff;
 13    text-align: left;
 14  }
 15  tr:first-child th:first-child {
 16    border-top-left-radius: 6px;
 17  }
 18  tr:first-child th:last-child {
 19    border-top-right-radius: 6px;
 20  }
 21  td {
 22    border-right: 1px solid #c6c9cc;
 23    border-bottom: 1px solid #c6c9cc;
 24  }
 25  td:first-child {
 26    border-left: 1px solid #c6c9cc;
 27  }
 28  tr:nth-child(even) td {
 29    background: #eaeaed;
 30  }
 31  tr:last-child td:first-child {
 32    border-bottom-left-radius: 6px;
 33  }
 34  tr:last-child td:last-child {
 35    border-bottom-right-radius: 6px;
 36  }
 37  
```

<h4>Demo</h4>

<h4>Pseudo-classes Overview</h4>

  | **Example** | **Classification** | **Explanation**                            |
  |---------------|----------------------|---------------------------------------------------|
  | a:link        | Link Pseudo-    | Selects a link that has not been visited by a user.    |
  |               | class           |                                                        |
  | a:visited     | Link Pseudo-    | Selects a link that has been visited by a user.        |
  |               | class           |                                                        |
  | a:hover       | Action Pseudo-  | Selects an element when a user has hovered their       |
  |               | class           | cursor over it.                                        |
  | a:active      | Action Pseudo-  | Selects an element when a user has engaged it.         |
  |               | class           |                                                        |
  | a:focus       | Action Pseudo-  | Selects an element when a user has made it their focus |
  |               | class           | point.                                                 |
  | input:enabled | State Pseudo-   | Selects an element in the default enabled state.       |
  |               | class           |                                                        |
  | input:disabled | State Pseudo-   | Selects an element in the disabled state, by way of the |
  |               | class           | disabled attribute.                                    |
  | input:checked | State Pseudo-   | Selects a checkbox or radio button that has been       |
  |               | class           | checked.                                               |
  | input:indeterminate | State Pseudo-  | Selects a checkbox or radio button thats neither been |
  |                     | class          | checked or unchecked, leaving it in an indeterminate  |
  |                     |                | state.                                                |
  | li:first-child | Structural   | Selects an element that is the first within a parent. |
  |                | Pseudo-class |                                                        |
  | li:last-child  | Structural   | Selects an element that is the last within a parent. |
  |                | Pseudo-class |                                                        |
  | div:only-child  | Structural   | Selects an element that is the only element within a |
  |                | Pseudo-class  | parent.                                                   |
  | p:first-of-type | Structural   | Selects an element that is the first of its type within a |
  |                | Pseudo-class  | parent.                                                   |
  | p:last-of-type | Structural   | Selects an element that is the last of its type within a |
  |                | Pseudo-class  | parent.                                                   |
  | img:only-of-type | Structural   | Selects an element that is the only one of its type within a |
  |                | Pseudo-class  | parent.                                                   |
  | li:nth-child(2n+3) | Structural    | Selects an element that matches the given number or |
  |                   | Pseudo-class  | expression, counting all elements from the beginning of |
  |                   |               | the document tree.                                       |
  | li:nth-last-   | Structural  | Selects an element that matches the given number or      |
  | type(3n+2)     | Pseudo-class | expression, counting all elements from the end of the |
  |                |              | document tree.                         |
  | p:nth-of-type(3n) | Structural   | Selects an element that matches the given number or      |
  |                   | Pseudo-class | expression, counting all elements of its type from the |
  |                   |              | beginning of the document tree.                        |
  | p:nth-last-of- | Structural  | Selects an element that matches the given number or      |
  | type(2n+1)     | Pseudo-class | expression, counting all elements of its type from the |
  |                |              | end of the document tree.                              |
  | section:target  | Target Pseudo- | Selects an element whose ID attribute value matches    |
  |                 | class          | that of the URI fragment identifier. |
  | div:empty       | Empty Pseudo- | Selects an element that does not contain any children  |
  |                 | class          | or text nodes. |
  | div:not(.awesome) | Negation     | Selects an element not represented by the stated  |
  |                   | Pseudo-class | argument. |
  
Pseudo-elements

Pseudo-elements are dynamic elements that don't exist in the document
tree, and when used within selectors
these [pseudo-elements](http://coding.smashingmagazine.com/2009/08/17/taming-advanced-css-selectors/) allow
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

<h4>CSS</h4>

```
 1  .alpha:first-letter,
 2  .bravo:first-line {
 3  color: #ff7b29;
 4  font-size: 18px;
 5  }
 6 
```

<h4>HTML</h4>

```
 1  <p class="alpha">Lorem ipsum dolor...</p>
 2  <p class="bravo">Integer eget enim...</p>
 3 
```

<h4>Textual Pseudo-elements Demo</h4>

<h4>Generated Content Pseudo-elements</h4>

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

<h4>CSS</h4>

```
 1  a:after {
 2  color: #9799a7;
 3  content: " (" attr(href) ")";
 4  font-size: 11px;
 5  }
 6 
```

<h4>HTML</h4>

```
 1  <a href="http://google.com/">Search the Web</a>
 2  <a href="http://learn.shayhowe.com/">Learn How to Build Websites</a>
 3 
```

<h4>Generated Content Pseudo-elements Demo</h4>

<h4>Fragment Pseudo-element</h4>

The ::selection fragment pseudo-element identifies part of the document
that has been selected, or highlighted, by a user's actions. The
selection may then be stylized, however only using
the color, background, background-color, and text-shadow properties. It
is worth noting, the background-image property is ignore. While the
shorthand background property may be used to add a color, any images
will be ignored.

<h4>Single Colon (:) versus Double Colons (::)</h4>

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

```
 1  ::-moz-selection {
 2  background: #ff7b29;
 3  }
 4  ::selection {
 5  background: #ff7b29;
 6  }
 7 
```

<h4>Fragment Pseudo-element Demo</h4>

<h4>Pseudo-elements Example</h4>

<h4>HTML</h4>

```
 1  <a class="arrow" href="#">Continue Reading</a>
 2  
```

<h4>CSS</h4>

```
 1  .arrow {
 2  background: #2db34a;
 3  color: #fff;
 4  display: inline-block;
 5  height: 30px;
 6  line-height: 30px;
 7  padding: 0 12px;
 8  position: relative;
 9  text-decoration: none;
 10  }
 11  .arrow:before,  
 12  .arrow:after {
 13  content: "";
 14  height: 0;
 15  position: absolute;
 16  width: 0;
 17  }
 18  .arrow:before {
 19  border-bottom: 15px solid #2db34a;
 20  border-left: 15px solid transparent;
 21  border-top: 15px solid #2db34a;
 22  left: -15px;
 23  }
 24  .arrow:after {
 25  border-bottom: 15px solid transparent;
 26  border-left: 15px solid #2db34a;
 27  border-top: 15px solid transparent;
 28  right: -15px;
 29  }
 30  .arrow:hover {
 31  background: #ff7b29;
 32  }
 33  .arrow:hover:before {
 34  border-bottom: 15px solid #ff7b29;
 35  border-top: 15px solid #ff7b29;
 36  }
 37  .arrow:hover:after {
 39  border-left: 15px solid #ff7b29;
 40  }
 41 
```

<h4>Demo</h4>

<h4>Pseudo-elements Overview</h4>

  | <b>Example</b> | <b>Classification</b> | <b>Explanation</b> |
  |------------------------------------------------------|--------------------|
  | .alpha:first-  | Textual Pseudo-   | Selects the first letter of text within an element. |
  | letter         | elements          |
  | .bravo:first-  | Textual Pseudo-   | Selects the first line of text within an element. |
  | line           | elements          |
  | div:before     | Generated Content | Creates a pseudo-element inside the selected element at |
  |                |                   | the beginning. |
  | a:after        | Generated Content | Creates a pseudo-element inside the selected element at |
  |                |                   | the end. |
  | ::selection    | Fragment Pseudo-  | Selects the part of a document which has been selected, |
  |                | element           | or highlighted, by a users' action. |
  

<h4>Selector Browser Support</h4>

While these selectors provide a variety of opportunity and the ability
to do some truly amazing things with CSS, they are at times plagued by
poor browser support. Before doing anything too critical check the
selectors you are wishing to use across your visitor's most common
browsers, and then make the judgment call as to whether they are
appropriate or not.

CSS3.info provides a [CSS3 Selectors Test](https://www.css3.info/selectors-test/) 
tool which will inform you as to which selectors are supported by the browser in
use. It's also never a bad idea to check browser support directly from the vendor.

Additionally, [Selectivizr](http://selectivizr.com/), a
JavaScript utility, provides great support for these selectors in
Internet Explorer 6-8. More support, should it be necessary, can also be
provided by [jQuery selectors](http://api.jquery.com/category/selectors/).

<h4>Selector Speed & Performance</h4>

It is important to pay attention the speed and performance of selectors,
as using too many intricate selectors can slow down the rendering of a
page. Be attentive and when a selector begins to look a bit foreign
think about revisiting it, and seeing if a better solution can be found.

<h4>Resources & Links</h4>

-[The 30 CSS Selectors you Must Memorize](http://net.tutsplus.com/tutorials/html-css-techniques/the-30-css-selectors-you-must-memorize/) via
 Nettuts+

-[Child and Sibling Selectors](https://css-tricks.com/child-and-sibling-selectors/) 
via CSS-Tricks

-[CSS3 Substring Matching Attribute
 Selectors](http://www.css3.info/preview/attribute-selectors/) via
 CSS3.info

-[How To Use CSS3
 Pseudo-Classes](http://coding.smashingmagazine.com/2011/03/30/how-to-use-css3-pseudo-classes/) via
 Smashing Magazine

-[Understanding :nth-child Pseudo-class
 Expressions](http://reference.sitepoint.com/css/understandingnthchildexpressions) via
 SitePoint

-[Taming Advanced CSS
 Selectors](http://coding.smashingmagazine.com/2009/08/17/taming-advanced-css-selectors/) via
 Smashing Magazine

 

[**Lesson 2**] Detailed
Positioning](https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/)
[**Lesson 4**] Responsive Web Design](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)

<h2 align="center">[Lesson 4] Responsive Web Design</h2>

<h3>In this Lesson 4</h3>

<h4>HTML</h4>

-[Responsive
 Overview](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#responsive-web-design)

-[Viewport](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#viewport)

<h4>CSS</h4>

-[Flexible
 Layouts](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#flexible-layouts)

-[Media
 Queries](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#media-queries)

-[Mobile
 First](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#mobile-first)

-[Flexible
 Media](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/#flexible-media)

**SHARE**

The Internet took off quicker than anyone would have predicted, growing
like crazy. Now, for the past few years, mobile growth has exploded onto
the scene. The growth of mobile Internet usage is also far out pacing
that of general Internet usage growth.

These days it is hard to find someone who doesn't own a mobile device,
or multiple, connected to the Internet. In the UK there are more mobile
phones than people, and should [trends
continue](http://www.digitalbuzzblog.com/2011-mobile-statistics-stats-facts-marketing-infographic/) mobile
Internet usage will surpass that of desktop Internet usage within the
year.

With the growth in mobile Internet usage comes the question of how to
build websites suitable for all users. The industry response to this
question has become responsive web design, also known as RWD.

<h4>Responsive Overview</h4>

Responsive web design is the practice of building a website suitable to
work on every device and every screen size, no matter how large or
small, mobile or desktop. Responsive web design is focused around
providing an intuitive and gratifying experience for everyone. Desktop
computer and cell phone users alike all benefit from responsive
websites.

The [responsive web design](http://www.alistapart.com/articles/responsive-web-design/) term
itself was coined, and largely developed, by Ethan Marcotte. A lot of
what is covered in this lesson was first talked about by Ethan online
and in his book <i><a href="http://www.abookapart.com/products/responsive-web-design/"></i>
Responsive Web Design</a>, which is worth a read.

![Food Sense Responsive Layout](./images/image007.png)

Fig. 4

<a href="http://foodsense.is/">Food Sense</a> has a beautiful
website, responsive to all different viewport sizes. No matter how large
or small the viewport may be the Food Sense website adjust, creating a
natural user experience.

<h4>Responsive vs. Adaptive vs. Mobile</h4>

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

<h4>Flexible Layouts</h4>

Responsive web design is broken down into three main components,
including flexible layouts, media queries, and flexible media. The first
part, flexible layouts, is the practice of building the layout of a
website with a flexible grid, capable of dynamically resizing to any
width. Flexible grids are built using relative length units, most
commonly percentages or em units. These relative lengths are then used
to declare common grid property values such as width, margin,
or padding.

<h4>Relative Viewport Lengths</h4>

CSS3 [introduced](http://dev.w3.org/csswg/css3-values/#viewport-relative-lengths) some
new relative length units, specifically related to the viewport size of
the browser or device. These new units include vw, vh, vmin, and vmax.
Overall support for these new units isn't great, but it is growing. In
time they look to play a large roll in building responsive websites.

-vw\
 Viewports width

-vh\
 Viewports height

-vmin\
 Minimum of the viewport's height and width

-vmax\
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

```
 1  target ÷ context = result
 2  
```

<h4>Flexible Grid</h4>

Let's see how this formula works inside of a two column layout. Below we
have a parent division with the class of container wrapping both
the section and aside elements. The goal is to have the section on the
left and the aside on the right, with equal margins between the two.
Normally the markup and styles for this layout would look a bit like the
following.

<h4>HTML</h4>

```
 1  <div class="container"> 
 2  <section>...</section> 
 3  <aside>...</aside>  
 4  </div>
 5 
```

<h4>CSS</h4>

```
 1  .container { 
 2    width: 538px;
 3  }
 4  section,
 5  aside {
 6    margin: 10px;
 7  }
 8  section {
 9    float: left;
 10   width: 340px;
 11 }
 12 aside {
 13   float: right;
 14   width: 158px;
 15 }
 16 
```

<h4>Fixed Grid Demo</h4>

Using the flexible grid formula we can take all of the fixed units of
length and turn them into relative units. In this example we'll use
percentages but em units would work equally as well. Notice, no matter
how wide the parent container becomes, the section and aside margins and
widths scale proportionally.

```
 1  section,
 2  aside {
 3    margin: 1.858736059%; /* 10px ÷ 538px = .018587361 */
 4  }
 5  section {
 6    float: left;
 7    width: 63.197026%; /* 340px ÷ 538px = .63197026 */
 8  }
 9  aside {
 10   float: right;
 11   width: 29.3680297%; /* 158px ÷ 538px = .293680297 */
 12 }
 13 
```

<h4>Flexible Grid Demo</h4>

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

<h4>Media Queries</h4>

Media queries were built as an extension to media types commonly found
when targeting and including styles. Media queries provide the ability
to specify different styles for individual browser and device
circumstances, the width of the viewport or device orientation for
example. Being able to apply uniquely [targeted
styles](https://css-tricks.com/css-media-queries/) opens up
a world of opportunity and leverage to responsive web design.

<h4>Initializing Media Queries</h4>

There are a couple different ways to use media queries, using
the @media rule inside of an existing style sheet, importing a new style
sheet using the @import rule, or by linking to a separate style sheet
from within the HTML document. Generally speaking it is recommend to use
the @media rule inside of an existing style sheet to avoid any
additional HTTP requests.

<h4>HTML</h4>

```
 1  <!&#45;&#45; Separate CSS File &#45;&#45;>
 2  <link href="styles.css" rel="stylesheet" media="all and (max-width: 1024px)">
 3 
```

<h4>CSS</h4>

```
 1  /* &#0064;media Rule */  
 2  &#0064;media all and (max-width: 1024px) {...}
 3  /* &#0064;import Rule */ 
 4  &#0064;import url(styles.css) all and (max-width: 1024px) {...} 
 5 
```

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

<h4>Logical Operators in Media Queries</h4>

Logical operators in media queries help build powerful expressions.
There are three different logical operators available for use within
media queries, including and, not, and only.

Using the and logical operator within a media query allows an extra
condition to be added, making sure that a browser or devices does
both a, b, c, and so forth. Multiple individual media queries can be
comma separated, acting as an unspoken or operator. The example below
selects all media types between 800 and 1024 pixels wide.

```
 1  &#0064;media all and (min-width: 800px) and (max-width: 1024px) {...} 
 2 
```

The not logical operator negates the query, specifying any query but the
one identified. In the example below the expression applies to any
device that does not have a color screen. Black and white or monochrome
screens would apply here for example.

```
 1  &#0064;media not screen and (color) {...}
 2 
```

The only logical operator is a new operator and is not recognized by
user agents using the HTML4 algorithm, thus hiding the styles from
devices or browsers that don't support media queries. Below, the
expression selects only screens in a portrait orientation that have a
user agent capable of rending media queries.

```
 1  &#0064;media only screen and (orientation: portrait) {...}
 2 
```

<h4>Omitting a Media Type</h4>

When using the not and only logical operators the media type may be left
off. In this case the media type is defaulted to all.

<h4>Media Features in Media Queries</h4>

Knowing the media query syntax and how logical operators work is a great
introduction to media queries but the true work comes with media
features. Media features identify what attributes or properties will be
targeted within the media query expression.

<h4>Height & Width Media Features</h4>

One of the most common media features revolves around determining a
height or width for a device or browser viewport. The height and width
may be found by using the height and width media features. Each of these
media features may then also be prefixed with the min or max qualifiers,
building a feature such as min-width or max-width.

The height and width features are based off the height and width of the
viewport rendering area, the browser window for example. Values for
these height and width media features may be any length unit, relative
or absolute.

```
 1  &#0064;media all and (min-width: 320px) and (max-width: 780px) {...}  
 2 
```

Within responsive design the most commonly used features
include min-width and max-width. These help build responsive websites on
desktops and mobile devices equally, avoiding any confusion with device
features.

<h4>Using Minimum & Maximum Prefixes</h4>

The min and max prefixes can be used on quite a few media features.
The min prefix indicates a values of *greater than or equal to* while
the max prefix indicates a value of *less than or equal to*.
Using min and max prefixes avoid any conflict with the general HTML
syntax, specifically not using the < and > symbols.

<h4>Orientation Media Feature</h4>

The orientation media feature determines if a device is in
the landscape or portrait orientation. The landscape mode is triggered
when the display is wider than taller, and the portrait mode is
triggered when the display is taller than wider. This media feature
plays a large part with mobile devices.

```
 1  &#0064;media all and (orientation: landscape) {...} 
 2 
```

<h4>Aspect Ratio Media Features</h4>

The aspect-ratio and device-aspect-ratio features specifies
the width/height pixel ratio of the targeted rendering area or output
device. The min and max prefixes are available to use with the different
aspect ratio features, identifying a ratio above or below that of which
is stated.

The value for the aspect ratio feature consist of two positive integers
separated by a forward slash. The first integer identifies the width in
pixels while the second integer identifies the height in pixels.

```
 1  &#0064;media all and (min-device-aspect-ratio: 16/9) {...}
 2 
```

<h4>Pixel Ratio Media Features</h4>

In addition to the aspect ratio media features there are
also pixel-ratio media features. These features do include
the device-pixel-ratio feature as well as min and max prefixes.
Specifically, the pixel ratio feature is great for identifying high
definition devices, including retina displays. Media queries for doing
so look like the following.

```
 1  &#0064;media only screen and (-webkit-min-device-pixel-ratio: 1.3), 
    only screen and (min-device-pixel-ratio: 1.3) {...}
 2 
```

<h4>Resolution Media Feature</h4>

The resolution media feature specifies the resolution of the output
device in pixel density, also known as dots per inch or DPI.
The resolution media feature does accept the min and max prefixes.
Additionally, the resolution media feature will accept dots per pixel
(1.3dppx), dots per centimeter (118dpcm), and other length based
resolution values.

```
 1  &#0064;media print and (min-resolution: 300dpi) {...}  
 2 
```

<h4>Other Media Features</h4>

Other media features include identifying available output colors with
use of the color, color-index, and monochrome features, identifying
bitmap devices with the grid feature, and identifying the scanning
process of a television with the scan feature. These features are less
common but equally as helpful when needed.

<h4>Media Query Browser Support</h4>

Unfortunately media queries do not work within Internet Explorer 8 and
below, as well as other legacy browsers. There are, however, a couple
suitable polyfills written in Javascript.

[Respond.js](https://github.com/scottjehl/Respond/) is a
lightweight polyfill that only looks for min/max-width media types,
which is perfect should those be the only media query types
used. [CSS3-MediaQueries.js](https://code.google.com/p/css3-mediaqueries-js/) is
a more developed, and heavier, polyfill offering support for a larger
array of more complex media queries. Additionally, keep in mind any
polyfill can have performance concerns, and potentially slow down
websites. Make sure that any given polyfill is worth the performance
trade off.

<h4>Media Queries Demo</h4>

Using media queries we will now rewrite the flexible layout we built
previously. One of the current problems within the demo appears when the
aside width becomes uselessly small within smaller viewports. Adding a
media query for viewports under 420 pixels wide we can change the layout
by turning off the floats and changing the widths of
the section and aside.

```
 1  &#0064;media all and (max-width: 420px) { 
 2  section, aside {
 3  float: none; 
 4  width: auto; 
 5  } 
 6  } 
 7 
```

![Demo without Media Queries](./images/image008.png)

**Fig. 4.**Without any media queries the section and aside become quite
small. Perhaps too small to even contain any real content.

![Demo with Media Queries](./3-25-24/media/image009.png)  <-- 3.4 width -->

**Fig. 4.**Using media queries to remove the floats and change their
widths, the section and aside are now able to span the full width of the
viewport, allowing breathing room for any existing content.

<h4>Identifying Breakpoints</h4>

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

<h4>Mobile First</h4>

One popular technique with using media queries is called *mobile first*.
The [mobile first](https://abookapart.com/products/mobile-first) approach
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

```
 1  /* Default styles first then media queries */ 
 2  &#0064;media screen and (min-width: 400px) {...} 
 3  &#0064;media screen and (min-width: 600px) {...} 
 4  &#0064;media screen and (min-width: 1000px) {...}
 5  &#0064;media screen and (min-width: 1400px) {...}
 6 
```

Additionally, downloading unnecessary media assets can be stopped by
using media queries. Generally speaking, avoiding CSS3 shadows,
gradients, transforms, and animations within mobile styles isn't a bad
idea either. When used excessively, they cause heavy loading and can
even reduce a device's battery life.

```
 1  /* Default media */
 2  body {  
 3  background: #ddd;  
 4  } 
 5  /* Media for larger devices */  
 6  &#0064;media screen and (min-width: 800px) { 
 7  body {  
 8  background-image: url("bg.png") 50% 50% no-repeat;  
 9  } 
 1  } 
 1 
```

<h4>Mobile First Demo</h4>

Adding media queries to our previous example, we overwrote a handful of
styles in order to have a better layout on viewports under 420 pixels
wide. Rewriting this code to use the mobile styles first by default then
adding media queries to adjust for viewports over 420 pixels wide we
build the following:

```
 1  section,
 2  aside { 
 3  margin: 1.858736059%; 
 4  } 
 5  &#0064;media all and (min-width: 420px) { 
 6  .container { 
 7  max-width: 538px;  
 8  } 
 9  section {  
 10  float: left; 
 11  width: 63.197026%; 
 12  } 
 13  aside { 
 14 float: right;
 15  width: 29.3680297%;
 16  } 
 17 } 
 18 
```

<h4>Mobile First Demo</h4>

Notice, this is the same amount of code as before. The only exception
here is that mobile devices only have to render only **one** CSS
declaration. All of the other styles are deferred, only loading on
larger viewports and done so without overwriting any initial styles.

<h4>Viewport</h4>

Mobile devices generally do a pretty decent job of displaying websites
these days. Sometimes they could use a little assistance though,
particularly around identifying
the [viewport](http://dev.opera.com/articles/view/an-introduction-to-meta-viewport-and-viewport/) size,
scale, and resolution of a website. To remedy this, Apple invented
the viewport meta tag.

![Website without Viewport Meta Tag](./images/image010.png)

**Fig. 4.** Although this demo has media queries, many mobile devices
still do not know the initial width or scale of the website. Therefore,
they may not interrupt media queries.

<h4>Viewport Height & Width</h4>

Using the viewport meta tag with either the height or width values will
define the height or width of the viewport respectively. Each value
accepts either a positive integer or keyword. For the height property
the keyword device-height value is accepted, and for the width property
the keyword device-width is accepted. Using these keywords will inherit
the device's default height and width value.

For the best results, and the best looking website, it is recommend that
you use the device defaults by applying
the device-height and device-width values.

```
 1  <meta name="viewport" content="width=device-width">
 2 
```

![Website with Viewport Meta Tag](./images/image011.png)

**Fig. 4.** Letting devices know the intended width of the
website, device-width in this case, allows the website to be sized
properly and to pick up any qualifying media queries.

<h4>Viewport Scale</h4>

To control how a website is scaled on a mobile device, and how users can
continue to scale a website, use
the minimum-scale, maximum-scale, initial-scale,
and user-scalable properties.

The initial-scale of a website should be set to 1 as this defines the
ratio between the device height, while in a portrait orientation, and
the viewport size. Should a device be in landscape mode this would be
the ratio between the device width and the viewport size. Values
for initial-scale should always be a positive integer between 0 and 10.

```
 1  <meta name="viewport" content="initial-scale=2">
 2 
```

![Viewport Scale Meta Tag](./images/image012.png)

**Fig. 4.** Using an integer above 1 will zoom the website to be larger
than the default scale. Generally speaking, this value will most
commonly be set to 1.

The minimum-scale and maximum-scale values determine how small and how
large a viewport may be scaled. When using minimum-scale the value
should be a positive integer lower than or equal to the initial-scale.
Using the same reasoning, the maximum-scale value should be a positive
integer greater than or equal to the initial-scale. Values for both of
these must also be between 0 and 10.

```
 1  <meta name="viewport" content="minimum-scale=0">
 2 
```

Generally speaking, these values should not be set to the same value as
the initial-scale. This would disable any zooming, which can be
accomplished instead by using the user-scalable value. Setting
the user-scalable value to no will disable any zooming. Alternatively,
setting the user-scalable value to yes will turn on zooming.

Turning off the ability to scale a website is a **bad idea**. It harms
accessibility and usability, preventing those with disabilities from
viewing a website as desired.

```
 1  <meta name="viewport" content="user-scalable=yes"> 
 2 
```

<h4>Viewport Resolution</h4>

Letting the browser decide how to scale a website based off any viewport
scale values usually does the trick. When more control is needed,
specifically over the resolution of a device,
the target-densitydpi value may be used. The target-densitydpi viewport
accepts a handful of values
including device-dpi, high-dpi, medium-dpi, low-dpi, or an actual DPI
number.

Using the target-densitydpi viewport value is rare, but extremely
helpful when pixel by pixel control is needed.

```
 1  <meta name="viewport" content="target-densitydpi=device-dpi">  
 2 
```

<h4>Combining Viewport Values</h4>

The viewport meta tag will accept individual values as well as multiple
values, allowing multiple viewport properties to be set at once. Setting
multiple values requires comma separating them within
the content attribute value. One of the recommended viewport values is
outlined below, using both the width and initial-scale properties.

```
 1  <meta name="viewport" content="width=device-width, initial-scale=1">
 2 
```

![Website with Viewport Meta Tag](./images/image011.png)

**Fig. 4** A combination
of width=device-width and initial-scale=1 provide the initial size and
zoom commonly required.

<h4>CSS Viewport Rule</h4>

Since the viewport meta tag revolves so heavily around setting the
styles of how a website should be rendered it has been recommend to move
the viewport from a meta tag with HTML to an @ rule within CSS. This
helps keep the style separated from content, providing a more semantic
approach.

Currently some browsers have already implemented the @viewport rule,
however support isn't great across the board. The previously
recommended viewport meta tag would look like the
following @viewport rule in CSS.

```
 1  &#0064;viewport {  
 2  width: device-width;
 3  zoom: 1; 
 4  }  
 5  
```

<h4>Flexible Media</h4>

The final, equally important aspect to responsive web design involves
flexible media. As viewports begin to change size media doesn't always
follow suit. Images, videos, and other media types need to be scalable,
changing their size as the size of the viewport changes.

One quick way to make media scalable is by using the max-width property
with a value of 100%. Doing so ensures that as the viewport gets smaller
any media will scale down according to its containers width.

```
 1  img, video, canvas {  
 2  max-width: 100%;
 3  } 
 4 
```

<h4>Flexible Media Demo</h4>

<h4>Flexible Embedded Media</h4>

Unfortunately the max-width property doesn't work well for all instances
of media, specifically around iframes and embedded media. When it comes
to third party websites, such as YouTube, who use iframes for embedded
media this is a huge disappointment. Fortunately, there is a [work
around](http://www.alistapart.com/articles/creating-intrinsic-ratios-for-video/).

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

<h4>HTML</h4>

```
 1  <figure> 
 2    <iframe src="https://www.youtube.com/embed/Sv3xVOs7_No"></iframe> 
 3  </figure>
 4 
```

<h4>CSS</h4>

```
 1  figure {
 2  height: 0; 
 3  padding-bottom: 56.25%; /* 16:9 */ 
 4  position: relative;
 5  width: 100%; 
 6  } 
 7  iframe {
 8  height: 100%;
 9  left: 0;
 10  position: absolute;
 11  top: 0; 
 13  width: 100%; 
 14  } 
 15 
```

<h4>Flexible Embedded Media Demo</h4>

For security reasons CodePen doesn't allow iframes within embedded code
samples, however you may [review and edit this code](https://codepen.io/shayhowe/pen/cbmsI) 
on their website.

100% Wide Container

75% Wide Container

50% Wide Container

<h4>Resources & Links</h4>

<ul>
  <li><a href="http://www.alistapart.com/articles/responsive-web-design/">
    Responsive Web Design</a> via A List Apart</li>
  <li><a href="http://dev.w3.org/csswg/css3-values/#viewport-relative-lengths">
    Viewport Percentage Lengths</a> via W3C</li>
  <li><a href="https://css-tricks.com/css-media-queries/">
    CSS Media Queries</a> via CSS-Tricks</li>
  <li><a href="https://abookapart.com/products/mobile-first">
    Mobile First</a> via Luke Wroblewski></li>
  <li><a href="http://dev.opera.com/articles/view/an-introduction-to-meta-viewport-and-viewport/">
    An Introduction to Meta Viewport and  &#0064;viewport</a> via Dev. Opera</li>
</ul>

**Lesson 3** <a href="https://learn.shayhowe.com/advanced-html-css/complex-selectors/">Complex Selectors</a>
**Lesson 5** <a href="https://learn.shayhowe.com/advanced-html-css/preprocessors/">Preprocessors</a>

<h2 align="center">[Lesson 5] Preprocessors</h2>

<h3>In this Lesson 5</h3>

<h4>HTML</h4>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/preprocessors/#haml">
    Haml</a></li>
</ul>

<h4>CSS</h4>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/preprocessors/#scss-sass">
    SCSS & Sass</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/preprocessors/#other-preprocessors">
    Other Preprocessors</a></li>
</ul>

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
include [Haml](http://haml.info/) and [Sass](http://sass-lang.com/).
include [Haml](http://haml.info/) and [Sass](http://sass-lang.com/).
Haml is processed into HTML and Sass is processed into CSS.

Upon setting out to solve some of the more common problems, Haml and
Sass found many additional ways to empower HTML and CSS, not only by
removing the inefficiencies but also in creating ways to make building
websites easier and more logical. The popularity of preprocessors have
also brought along different frameworks to support them, one of the more
popular being Compass.

<h4>Haml</h4>

Haml, known as <a href="http://haml.info/docs/yardoc/file.REFERENCE.html">
HTML abstraction markup language</a>, is a markup language with the single 
goal of providing the ability to write beautiful markup. Serving as its own 
markup language, code written in Haml is later processed to HTML. Haml promotes 
DRY and well structured markup, providing a pleasing experience for anyone 
having to write or read it.

<h4>Installation</h4>

Haml requires Ruby to be compiled to HTML, so the first step to using it
is to ensure that Ruby is installed. Fortunately for those on Mac OS X
Ruby comes preinstalled, and those on a Windows machine may
visit <a href="http://rubyinstaller.org/">Windows Installer</a> for
directions. Upon confirming Ruby is installed the gem install
haml command needs to be run from the command line, using Terminal or
the alike command line program, to install Haml.

```
 1  gem install haml
 2 
```

Files written in the Haml markup should be saved with the file extension
of .haml. To then convert these files from Haml to HTML the haml command
below needs to be run to compile each individual file.

```
 1  haml index.haml index.html  
 2 
```

In the example above, the file index.haml is converted to HTML and saved
as index.html within the same directory. This command has to be run
within the same directory the files reside in. Should the command be run
outside this directory the path where the files reside need to be
included within the command. At any time the command haml &#45;&#45;help may be
run to see a list of different available options.

<h4>Watching a File or Directory</h4>

Unfortunately Haml doesn't provide a way to watch a file, or directory,
for changes without the use of another dependency.

Inside of a Rails application a Haml dependency may be added in the
Gemfile, thus automatically compiling Haml files to HTML upon any
changes. There are a few desktop applications available for those not
using Rails, one of the more popular
being [CodeKit](https://codekitapp.com/).

On top of Haml CodeKit also supports other preprocessors, which may also
come in handy.

<h4>Doctype</h4>

The first part to writing a document in Haml is knowing what type
of doctype is to be used. When working with HTML documents, the general
document type is going to be the HTML5 doctype. In Haml document types
are identified with three exclamation points, !!! followed by any
specifics if necessary.

The default doctype in Haml is the HTML 1.0 Transitional document type
so in order to make this the HTML5 doctype the number five has to be
passed in after the exclamation points, !!! 5.

**Haml**

```
 1  !!! 5
 2 
```

**Compiled HTML**

```
 1  <!DOCTYPE html>  
 2 
```

<h4>Declaring Elements</h4>

One of the defining features of Haml is its syntax, and how to [declare
and
nest](https://coderwall.com/p/aivizg/introduction-to-haml--2) elements.
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

```
 1  %body
 2  %header 
 3  %h1 Hello World 
 4  %section
 5  %p Lorem ipsum dolor sit amet. 
 6 
```

**Compiled HTML**

```
 1  <body>
 2  <header> 
 3  <h1>Hello World</h1> 
 4  </header>
 5  <section>
 6  <p>Lorem ipsum dolor sit amet.</p>  
 7  </section> 
 8  </body>  
 9 
```

<h4>Handling Text</h4>

Text within Haml can be placed on the same line as the declared element,
or indented below the element. Text cannot be both on the same line as
the declared element and nested below it, it has to be either or. The
example from above could be rewritten as the following:

```
 1  %body 
 2  %header  
 3  %h1
 4  Hello World
 5  %section 
 6  %p 
 7  Lorem ipsum dolor sit amet.  
 8  
```

<h4>Attributes</h4>

Attributes, as with elements, are declared a bit differently in Haml.
Attributes are declared directly after the element in either {} or (),
all depending if you wish to use Ruby or HTML syntax. Ruby style
attributes will use the standard hash syntax inside of {}, while HTML
style attributes will use standard HTML syntax inside of ().

**Haml**

```
 1  %img{:src => "shay.jpg", :alt => "Shay Howe"}
 2  %img{src: "shay.jpg", alt: "Shay Howe"}  
 3  %img(src="shay.jpg" alt="Shay Howe")
 4 
```

**Compiled HTML**

```
 1  <img src="shay.jpg" alt="Shay Howe">
 2 
```

<h4>Classes &amp; IDs</h4>

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

<h4>Haml</h4>

```
 1  %section.feature
 2  %section.feature.special 
 3  %section#hello  
 4  %section#hello.feature(role="region") 
 5 
```

**Compiled HTML**

```
 1  <section class="feature"></section> 
 2  <section class="feature special"></section>  
 3  <section id="hello"></section> 
 4  <section class="feature" id="hello" role="region"></section>  
 5 
```

<h4>Division Classes &amp; IDs</h4>

In the event a class or ID is used on a div the %div may be omitted, and
the class or ID value can be used outright. Again, classes are to be
identified with a . and IDs are to be identified with a #.

**Haml**

```
 1  .awesome
 2  .awesome.lesson 
 3  #getting-started.lesson  
 4 
```

**Compiled HTML**

```
 1  <div class="awesome"></div> 
 2  <div class="awesome lesson"></div>
 3  <div class="lesson" id="getting-started"></div>  
 4 
```

<h4>Boolean Attributes</h4>

Boolean attributes are handled just as they would be within Ruby or
HTML, all depending on the syntax being used.

**Haml**

```
 1  %input{:type => "checkbox", :checked => true}  
 2  %input(type="checkbox" checked=true)  
 3  %input(type="checkbox" checked) 
 4 
```

**Compiled HTML**

```
 1  <input type="checkbox" checked>  
 2 
```

<h4>Escaping Text</h4>

One of the benefits of Haml is the ability to evaluate and run Ruby,
however this isn't always the desired action. Text, and lines of code,
can be escaped by using a backslash, \&#0044; allowing the text to be
rendered explicitly without being executed.

In the example below, the first instance of = &#0064;author is executed Ruby,
pulling the authors name from the application. The second instance,
starting with the backslash, is escaped text, printing it as is, without
execution.

**Haml**

```
 1  .author 
 2  = &#0064;author 
 3  \\= &#0064;author 
 4 
```

**Compiled HTML**

```
 1  <div class="author"> 
 2  Shay Howe  
 3  = &#0064;author 
 4  </div>
 5 
```

<h4>Text Escaping Alternatives</h4>

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

```
 1  %p
 2  Shay is 
 3  = succeed "." do 
 4  %a{:href => "#"} awesome 
 5 
```

**Compiled HTML**

```
 1  <p>Shay is <a href="#">awesome</a>.</p>  
 2 
```

<h4>Comments</h4>

As with elements and attributes, comments are handled a bit differently
in Haml as well. Simply enough, code can be commented out with the use
of a single forward slash, /. Individual lines may be commented out with
the use of a forward slash at the beginning of the line, and blocks of
code can be commented out by being nested underneath a forward slash.

**Haml**

```
 1  %div 
 2  / Commented line
 3  Actual line
 4  / 
 5  %div 
 6  Commented block 
 7 
```

**Compiled HTML**

```
 1  <div> 
 2  <!&#45;&#45; Commented line &#45;&#45;> 
 3  Actual line
 4  </div>
 5  <!&#45;&#45;  
 6  <div> 
 7  Commented block 
 8  </div>
 9  &#45;&#45;>
 10 
```

<h4>Conditional Comments</h4>

Conditional comments are also handled differently in Haml. To create a
conditional comment use square brackets, [], around the condition.
These square brackets need to be placed directly after the forward
slash.

**Haml**

```
 1  /]if lt IE 9[ 
 2  %script{:src => "html5shiv.js"}
 3 
```

**Compiled HTML**

```
 1  <!&#45;&#45;]if lt IE 9[>
 2  <script src="html5shiv.js"></script>
 3  <&#0033;[endif[&#45;&#45;>  
 4 
```

<h4>Silent Comments</h4>

Haml also provides the ability to create Haml specific comments, or
silent comments. Silent comments differ from general HTML comments in
that upon being complied any content within a silent comment is
completely removed from the page, and is not displayed in the output.
Silent comments are initialized with a dash then the number sign, -#. As
with other comments, silent comments may be used to remove one line or
multiple lines with the use of nesting.

**Haml**

```
 1  %div 
 2  -# Removed line 
 3  Actual line
 4 
```

**Compiled HTML**

```
 1  <div> 
 2  Actual line
 3  </div>
 4 
```

<h4>Filters</h4>

Haml provides a handful of filters, allowing different types of input to
be used inside of Haml. Filters are identified with a colon followed by
the name of the filter, :markdown for example, with all of the content
to be filtered nested underneath.

<h4>Common Filters</h4>

Below are some of the more common filters, with the more popular ones of
the group being :css and :javascript.

-:cdata

-:coffee

-:css

-:erb

-:escaped

-:javascript

-:less

-:markdown

-:maruku

-:plain

-:preserve

-:ruby

-:sass

-:scss

-:textile

<h4>Javascript Filter</h4>

**Haml**

```
 1  :javascript
 2  $('button').on('click', function(event) {  
 3  $('p').hide('slow');
 4  });  
 5 
```

**Compiled HTML**

```
 1  <script> 
 2  $('button').on('click', function(event) {  
 3  $('p').hide('slow');
 4  });  
 5  </script>
 6 
```

<h4>CSS &amp; Sass Filters</h4>

**Haml**

```
 1  :css 
 2  .container { 
 3  margin: 0 auto; 
 4  width: 960px;
 5  } 
 6  :sass
 7  .container 
 8  margin: 0 auto  
 9  width: 960px 
 10  
```

**Compiled HTML**

```
 1  <style>  
 2  .container { 
 3  margin: 0 auto; 
 4  width: 960px;
 5  } 
 6  </style> 
 7 
```

<h4>Ruby Interpolation</h4>

As previously mentioned Haml can evaluate Ruby, and there may
occasionally be times where Ruby needs to be evaluated inside of plain
text. In this event Ruby needs to be interpolated, accomplished by
wrapping the necessary Ruby code inside .

Below is an example of Ruby being interpolated as part of a class name.

**Haml**

```
 1  %div{:class => "student-#{@student.name}"}
 2 
```

**Compiled HTML**

```
 1  <div class="student-shay"> 
 2 
```

<h4>SCSS &amp; Sass</h4>

SCSS and Sass are preprocessing languages which are compiled to CSS,
resembling Haml a bit in that they make writing code easier, and provide
quite a bit of leverage in doing so. Individually SCSS and Sass come
from the same origin however they are technical different syntaxes.

Sass, [Syntactically Awesome
Stylesheets](https://sass-lang.com/documentation/), came
first and is a strict indented syntax. SCSS, Sassy CSS, followed shortly
after providing the same firing power of Sass but with a more flexible
syntax, including the ability to write plain CSS.

<h4>Installation</h4>

As with Haml, SCSS and Sass
are [compiled](http://sassmeister.com/) using Ruby
therefore Ruby needs to be installed to produce CSS files. Please follow
the directions from before to install, or ensure Ruby is installed.

Once Ruby is installed the gem install sass command needs to be run from
the command line to install SCSS and Sass.

```
 1  gem install sass
 2 
```

Files written in SCSS or Sass need to have the .scss or .sass file
extensions respectively. To convert either of these file types
to .css the following sass command needs to be run.

```
 1  sass styles.sass styles.css 
```

The command above takes the styles.sass Sass file and compiles it to
the styles.css file. As with Haml, these file names are paths and need
to be executed respectively. The above command works when those files
reside within the directory from which the command is run, should the
files reside outside of the directory their path needs to be explicitly
stated within the command.

Should changes to a file be ongoing Sass can watch the file and
recompile the CSS every time a change takes place. To watch a Sass file
the following sass command may be run.

```
 1  sass &#45;&#45;watch styles.sass:styles.css 
 2 
```

Additionally, instead of compiling or watching individual files, Sass is
capable of compiling and watching entire directories of files. For
example, to watch an entire directory of Sass files and convert them to
CSS the sass command below may be run.

```
 1  sass &#45;&#45;watch assets/sass:public/css 
 2 
```

<h4>Converting Files from SCSS to Sass &amp; Vice Versa</h4>

On top of being able to convert SCSS and Sass files to CSS you can also
convert files from SCSS to Sass and vice versa. To do so
the sass commands below may be used to convert a SCSS file to Sass, and
then a Sass file to SCSS respectively.

```
 1  &#0035; Convert Sass to SCSS
 2  sass-convert styles.sass styles.scss  
 3  &#0035; Convert SCSS to Sass
 4  sass-convert styles.scss styles.sass  
 5  
```

<h4>Syntax</h4>

As previously mentioned the primary difference between SCSS and Sass is
their syntax, and their difference in severity. The syntax of SCSS isn't
much different than that of regular CSS. In fact, standard CSS will run
inside of SCSS. Sass on the other hand is fairly strict, and any
indenting or character errors will prohibit the styles from compiling.
Sass omits all curly brackets, {}, and semicolons, ;, relying on
indentation and clear line breaks for formatting.

**SCSS**

```
 1  .new {  
 2  color: #ff7b29; 
 3  font-weight: bold; 
 4  span {  
 5  text-transform: uppercase;  
 6  } 
 7  } 
 8 
```

**Sass**

```
 1  .new 
 2  color: #ff7b29  
 3  font-weight: bold  
 4  span 
 5  text-transform: uppercase
 6 
```

**Compiled CSS**

```
 1  .new {  
 2  color: #ff7b29; 
 3  font-weight: bold; 
 4  } 
 5  .new span {
 6  text-transform: uppercase;  
 7  } 
 8 
```

<h4>Using SCSS vs. Sass</h4>

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

<h4>Nesting</h4>

In the syntax example above you will notice how selectors may be nested
inside of one another to create compound selectors. The nesting quickly
outlines identifiable selectors, however it is important not to go
overboard. Do **not** nest selectors for unapparent reasons or go
overboard nesting one selector under the prior one. Using specific
selectors without raising specificity is important.

**Sass**

```
 1  .portfolio 
 2  border: 1px solid #9799a7
 3  ul
 4  list-style: none
 5  li
 6  float: left
 7 
```

**Compiled CSS**

```
 1  .portfolio { 
 2  border: 1px solid #9799a7;  
 3  } 
 4  .portfolio ul { 
 5  list-style: none;  
 6  } 
 7  .portfolio li { 
 8  float: left; 
 9  } 
 10 
```

<h4>Nesting Properties</h4>

On top of nesting selectors it is also possible to nest properties. Some
of the most popular uses of this may be seen with font, margin, padding,
and border properties. As with the decision of SCSS versus Sass, this is
very much a personal decision. Many feel that shorthand values are fine
and breaking out values in this longer format is unnecessary. Ultimately
your decision is up to personal preference.

**Sass**

```
 1  div  
 2  font:
 3  family: Baskerville, Palatino, serif 
 4  style: italic
 5  weight: normal  
 6 
```

**Compiled CSS**

```
 1  div {
 2  font-family: Baskerville, Palatino, serif;
 3  font-style: italic;
 4  font-weight: normal;  
 5  } 
 6 
```

<h4>Nested Media Queries</h4>

Individual media queries may also be nested inside of a selector,
changing property values based off a media condition.

**Sass**

```
 1  .container 
 2  width: 960px 
 3  &#0064;media screen and (max-width: 960px)
 4  width: 100%
 5 
```

**Compiled CSS**

```
 1  .container { 
 2  width: 960px;
 3  } 
 4  &#0064;media screen and (max-width: 960px) { 
 5  .container { 
 6  width: 100%; 
 7  } 
 8  } 
 9 
```

<h4>Parent Selector</h4>

Sass provides a way to add styles to a previous selector with the use of
the parent selector, implemented by using an ampersand, &. Most commonly
the parent selector is used in conjunction with a pseudo class, such
as :hover, however it doesn't have to be. Additionally the parent
selector could be used to bind additional selectors to its parent, such
as &.featured.

**Sass**

```
 1  a 
 2  color: #0087cc  
 3  &:hover 
 4  color: #ff7b29  
 5 
```

**Compiled CSS**

```
 1  a {  
 2  color: #0087cc; 
 3  } 
 4  a:hover {  
 5  color: #ff7b29; 
 6  } 
 7 
```

<h4>Parent Key Selector</h4>

The parent selector may also be used as the key selector, adding
qualifying selectors to make compound selectors. There are an abundance
of ways to use the parent selector as the key selector but perhaps one
of the most beneficial is inside of feature detection.

**Sass**

```
 1  .btn 
 2  background: linear-gradient(#fff, #9799a7)
 3  .no-cssgradients & 
 4  background: url("gradient.png") 0 0 repeat-x  
 5 
```

**Compiled CSS**

```
 1  .btn {  
 2  background: linear-gradient(#fff, #9799a7);  
 3  } 
 4  .no-cssgradients .btn {  
 5  background: url("gradient.png") 0 0 repeat-x; 
 6  } 
 7 
```

<h4>Comments</h4>

Sass handles comments very similar to that of Haml. The standard CSS
syntax, /* ... */, for comments works as intended within Sass however
there is also a syntax for silent comments to completely remove a
comment or lines of code from being compiled.

The syntax for silent comments is two forward slashes, //, and any
content on that line or nested below it will be omitted from
computation. Notice in the example below how the // Omitted comment line
is not rendered in the compiled CSS.

**Sass**

```
 1  /* Normal comment */
 2  div  
 3  background: #333
 4  // Omitted comment 
 5  strong  
 6  display: block  
 7 
```

**Compiled CSS**

```
 1  /* Normal comment */
 2  div {
 3  background: #333;  
 4  } 
 5  strong {
 6  display: block; 
 7  } 
 8 
```

<h4>Variables</h4>

Variables are one of the more sought after features of CSS that Sass
provides. With Sass you can define variables and then reuse them as
necessary.

Variables are defined with a dollar sign, $, followed by the variable
name. Between the variable name and value is a colon followed by an
empty space, such as $font-base: 1em. As for the value of the variable,
it may be a number, string, color, boolean, null, or a list of values
separated by spaces or commas.

<h4>Sass</h4>

```
 1  $font-base: 1em
 2  $serif: "Helvetica Neue", Arial, "Lucida Grande", sans-serif 
 3  p 
 4  font: $font-base $serif
 5 
```

**Compiled CSS**

```
 1  p {  
 2  font: 1em "Helvetica Neue", Arial, "Lucida Grande", sans-serif;  
 3  } 
 4 
```

<h4>Variable Interpolation</h4>

For the most part variables may be used anywhere inside of a Sass
document. However, they may occasionally need to be interpolated using
the syntax. A few instances of where variables need to be interpolated
include when being used in a class name, property name, or inside a
string of plain text.

<h4>Sass</h4>

```
 1  $location: chicago
 2  $offset: left  
 3  .#{$location}  
 4  #{$offset}: 20px  
 5 
```

**Compiled CSS**

```
 1  .chicago { 
 2  left: 20px;
 3  } 
 4 
```

<h4>Calculations</h4>

Sass also has the ability to do calculations in a variety of different
manners. Calculations can handle most problems, such as addition,
subtraction, division, multiplication, and rounding.

Addition can be done by using the plus sign, +, and may be completed
with or without units of measurement. When done with units, the unit
tied to the first number in the equation is the unit that will be used
in the computed value. For example, ten pixels plus one inch will equal
106 pixels. Subtraction is handled the same way as addition but with the
minus sign, -, instead.

Multiplication is completed with the asterisk sign, *, however only one
of the numbers, if any, may include a unit of measurement. Using the
percent sign, %, will return the remainder of the two numbers upon being
divided, and as with multiplication, only allows one number, if any, to
have a unit.

<h4>Sass</h4>

```
 1  width: 40px + 6 
 2  width: 40px - 6 
 3  width: 40px * 6
 4  width: 40px % 6 
 5 
```

**Compiled CSS**

```
 1  width: 46px; 
 2  width: 34px; 
 3  width: 240px;
 4  width: 4px;
 5 
```

<h4>Division</h4>

Division is a bit trickier in Sass as the forward slash, /, used to
perform division is already used in some CSS property values. Generally
speaking, division will take place when any part of the value uses a
variable, if the value is wrapped in parentheses, or if the value is
used as part of another equation.

When using one unit of measurement in division the value will reside in
that unit. When using two units of measurement, however, the resulting
value will be unitless.

**Sass**

```
 1  width: 100px / 10  
 2  width: (100px / 10)
 3  width: (100px / 10px) 
 4  $width: 100px  
 5  width: $width / 10
 6  width: 5px - 100px / 10  
 7 
```

**Compiled CSS**

```
 1  width: 100px/10;
 2  width: 10px; 
 3  width: 10; 
 4  width: 10px; 
 5  width: -5px; 
 6 
```

<h4>Detailed Math</h4>

As one may expect, Sass is also capable of combining multiple math
operations. Sass also recognizes which operations to execute first based
on the use of parentheses.

**Sass**

```
 1  $grid: 16 
 2  $column: 40px  
 3  $gutter: 20px  
 4  $container: ($column * $grid) + ($gutter * $grid) 
 5  width: $container 
 6 
```

**Compiled CSS**

```
 1  width: 960px;
 2 
```

<h4>Number Functions</h4>

By default Sass includes a handful of [built in
functions](https://sass-lang.com/documentation/modules/math),
many of which are used to manipulate number values as wished.

The percentage() function turns a value into a percentage.
The round() function rounds a value to the closest whole number,
defaulting to rounding up where necessary. The ceil() function rounds a
value up to the closest whole number, and the floor() function rounds a
value down to the closest whole number. Lastly, the abs() function finds
the absolute value of a given number.

-percentage()

-round()

-ceil()

-floor()

-abs()

**Sass**

```
 1  width: percentage(2.5)
 2  width: round(2.5px)
 3  width: ceil(2.5px) 
 4  width: floor(2.5px)
 5  width: abs(-2.5px) 
 6 
```

**Compiled CSS**

```
 1  width: 250%; 
 2  width: 3px;
 3  width: 3px;
 4  width: 2px;
 5  width: 2.5px;
 6 
```

<h4>Color</h4>

Sass provides quite a bit of assistance in working with colors,
providing a handful of different features to alter and manipulate
colors. One of the more popular color features in Sass is the ability to
change a hexadecimal color, or variable, and convert it into an RGBa
value.

**Sass**

```
 1  color: rgba(#8ec63f, .25)
 2  $green: #8ec63f
 3  color: rgba($green, .25)
 4 
```

**Compiled CSS**

```
 1  color: rgba(142, 198, 63, .25);
 2 
```

<h4>Color Operations</h4>

On top of numbers, math may additionally be performed on colors using
addition, subtraction, multiplication, and division. These computations
are performed on the red, green, and blue components, changing them as
intended.

**Sass**

```
 1  color: #8ec63f + #666 
 2  color: #8ec63f * 2
 3  color: rgba(142, 198, 63, .75) / rgba(255, 255, 255, .75)
 4 
```

**Compiled CSS**

```
 1  color: #f4ffa5; 
 2  color: #ffff7e; 
 3  color: rgba(0, 0, 0, .75);  
 4 
```

<h4>Color Alterations</h4>

Using color operators to perform calculations is helpful but can be a
bit challenging as well. In this case color alterations may be a better
option. Color alterations provide the ability to inverse colors, find
complementary colors, mix colors together, or find the grayscale value
of a color.

-invert()

-complement()

-mix()

-grayscale()

**Sass**

```
 1  color: invert(#8ec63f)
 2  color: complement(#8ec63f)  
 3  color: mix(#8ec63f, #fff)
 4  color: mix(#8ec63f, #fff, 10%) 
 5  color: grayscale(#8ec63f)
 6 
```

**Compiled CSS**

```
 1  color: #7139c0; 
 2  color: #773fc6; 
 3  color: #c6e29f; 
 4  color: #f3f9eb; 
 5  color: #838383; 
 6 
```

<h4>HSLa Color Alterations</h4>

HSLa color alterations take things a step further, adding in even more
alterations. Some of the more popular HSLa color alterations
include lighten(), darken(), saturate(), and desaturate().

-lighten()

-darken()

-saturate()

-desaturate()

-adjust-hue()

-fade-in()

-fade-out()

**Sass**

```
 1  color: lighten(#8ec63f, 50%)
 2  color: darken(#8ec63f, 30%) 
 3  color: saturate(#8ec63f, 75%)  
 4  color: desaturate(#8ec63f, 25%)
 5  color: adjust-hue(#8ec63f, 30) 
 6  color: adjust-hue(#8ec63f, -30)
 7  color: fade-in(rgba(142, 198, 63, 0), .4) 
 8  color: fade-out(#8ec63f, .4)
 9 
```

**Compiled CSS**

```
 1  color: white;
 2  color: #3b5319; 
 3  color: #98ff06; 
 4  color: #89a75e; 
 5  color: #4ac63f; 
 6  color: #c6bb3f; 
 7  color: rgba(142, 198, 63, 0.4);
 8  color: rgba(142, 198, 63, 0.6);
 9 
```

<h4>Color Manipulation</h4>

Outside of altering colors Sass can also directly manipulate colors.
Manipulating colors provides the most control over how to finely tune
specific color properties. With this control also comes complexity,
which is why color manipulations are a bit less common than color
alterations.

```
-change-color() --- Set any property of a color\
 $color, ]$red[, ]$green[, ]$blue[, ]$hue[,
 ]$saturation[, ]$lightness[, ]$alpha[

-adjust-color() --- Incrementally manipulate any property of a color\
 $color, ]$red[, ]$green[, ]$blue[, ]$hue[,
 ]$saturation[, ]$lightness[, ]$alpha[

-scale-color() --- Fluidly scale any percentage based on property of
 a color\
 $color, ]$red[, ]$green[, ]$blue[, ]$saturation[,
 ]$lightness[, ]$alpha[
```

**Sass**

```
 1  color: change-color(#8ec63f, $red: 60, $green: 255) 
 2  color: adjust-color(#8ec63f, $hue: 300, $lightness: 50%)  
 3  color: scale-color(#8ec63f, $lightness: 25%, $alpha: 30%) 
 4 
```

**Compiled CSS**

```
 1  color: #3cff3f; 
 2  color: white;
 3  color: #aad46f; 
 4 
```

<h4>Extends</h4>

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

```
 1  .alert  
 2  border-radius: 10px
 3  padding: 10px 20px 
 4  .alert-error 
 5  &#0064;extend .alert 
 6  background: #f2dede
 7  color: #b94a48  
 8 
```

**Compiled CSS**

```
 1  .alert, 
 2  .alert-error {  
 3  border-radius: 10px;  
 4  padding: 10px 20px;
 5  } 
 6  .alert-error {  
 7  background: #f2dede;  
 8  color: #b94a48; 
 9  } 
 10 
```

<h4>Placeholder Selector Extend</h4>

To avoid building a bunch of unused classes purely for extends we can
use what is known as a placeholder selector. The placeholder selector is
initialized with a percentage sign, %, and is never directly compiled
into CSS. Instead, it is used to attach selectors to when it is called
with an extend. In the refined example below notice how
the .alert selector never makes its way into the CSS.

**Sass**

```
 1  %alert  
 2  border-radius: 10px
 3  padding: 10px 20px 
 4  .alert-error 
 5  &#0064;extend %alert 
 6  background: #f2dede
 7  color: #b94a48  
 8 
```

**Compiled CSS**

```
 1  .alert-error {  
 2  border-radius: 10px;  
 3  padding: 10px 20px;
 4  } 
 5  .alert-error {  
 6  background: #f2dede;  
 7  color: #b94a48; 
 8  } 
 9 
```

<h4>Element Selector Extend</h4>

As with classes, extends also work with standard element selectors too.

**Sass**

```
 1  h2
 2  color: #9c6
 3  span 
 4  text-decoration: underline  
 5  .sub-heading 
 6  &#0064;extend h2
 7 
```

**Compiled CSS**

```
 1  h2, .sub-heading { 
 2  color: #9c6; 
 3  } 
 4  h2 span, .sub-heading span {
 5  text-decoration: underline; 
 6  } 
 7 
```

<h4>Mixins</h4>

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

```
 1  &#0064;mixin btn($color, $color-hover)  
 2  color: $color  
 3  &:hover 
 4  color: $color-hover  
 5  .btn 
 6  +btn($color: #fff, $color-hover: #9799a7)  
 7 
```

**Compiled CSS**

```
 1  .btn {  
 2  color: #fff; 
 3  } 
 4  .btn:hover { 
 5  color: #9799a7; 
 6  } 
 7 
```

<h4>Default Arguments</h4>

Using the same example from above we can also specify default argument
values, which may be over written if wished.

**Sass**

```
 1  &#0064;mixin btn($color: #fff, $color-hover: #9799a7) 
 2  color: $color  
 3  &:hover 
 4  color: $color-hover  
 5  .btn 
 6  +btn($color-hover: #9799a7)
 7 
```

**Compiled CSS**

```
 1  .btn {  
 2  color: #fff; 
 3  } 
 4  .btn:hover { 
 5  color: #9799a7; 
 6  } 
 7 
```

<h4>Variable Arguments</h4>

When one or more values need to be passed to an argument the variable
name may end with ... inside of the mixin. In the example below with
box shadows we can pass in comma separated values to the mixin.

```
 1  &#0064;mixin box-shadow($shadow...)  
 2  -webkit-box-shadow: $shadow
 3  -moz-box-shadow: $shadow
 4  box-shadow: $shadow  
 5  .shadows
 6  +box-shadow(0 1px 2px #cecfd5, inset 0 0 5px #cecfd5) 
 7 
```

**Compiled CSS**

```
 1  .shadows { 
 2  -moz-box-shadow: 0 1px 2px #cecfd5, inset 0 0 5px #cecfd5;  
 3  -webkit-box-shadow: 0 1px 2px #cecfd5, inset 0 0 5px #cecfd5;  
 4  box-shadow: 0 1px 2px #cecfd5, inset 0 0 5px #cecfd5; 
 5  } 
 6 
```

<h4>Imports</h4>

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

```
 1  &#0064;import "normalize"
 2  &#0064;import "grid", "typography" 
 3 
```

**Compiled HTML**

```
 1  <link href="styles.css" rel="stylesheet"> 
 2 
```

<h4>Loops & Conditionals</h4>

For a bit more intricate styling Sass supports different control
directives. Its important to understand these directives are not
intended for everyday styling but for creating detailed mixins and
helpers. Many of these will look familiar as they are borrowed from
other programming languages.

<h4>Operators</h4>

Some loops and conditionals will require operators to determine their
behavior, of which can be broken down into relational and comparison
operators. Relational operators looks at the relationship between two
entities, while comparison operators determine equality or different
between to entities.

```
-<\
 Less than

->\
 Greater than

-==\
 Equal to

-<=\
 Less than or equal to

->=\
 Greather than or equal to

-!=\
 Not equal to
```

```
 1  // Relational Operators  
 2  6 < 10 // true 
 3  4 <= 60 // true
 4  8 > 2 // true  
 5  10 >= 10 // true  
 6  // Comparison Operators  
 7  #fff == white // true 
 8  10 + 30 == 40 // true 
 9  normal != bold // true
 10 
```

<h4>If Function</h4>

The @if rule test an expressions then loads the styles beneath that
expression should it return anything other than false or null. The
initial if statement may be proceeded by several else if statements and
one else statement. Once a statement is successful identified the styles
directly tied to it will be applied.

**Sass**

```
 1  $shay: awesome 
 2  .shay
 3  &#0064;if $shay == awesome
 4  background: #ff7b29
 5  &#0064;else if $shay == cool 
 6  background: #0087cc
 7  &#0064;else  
 8  background: #333
 9 
```

**Compiled CSS**

```
 1  .shay { 
 2  background: #ff7b29;  
 3  } 
 4 
```

<h4>For Loop</h4>

The @for rule outputs different sets of styles based off of a counter
variable. There are two different forms available for for loops, those
being to and through. The first, @for $i from 1 to 3 for example, will
output styles up to, but not including, 3. The other form, @for $i from
1 through 3, will output styles up to, and including, 3.

**Sass**

```
 1  &#0064;for $col from 1 to 6  
 2  .col-#{$col}
 3  width: 40px * $col  
 4 
```

**Compiled CSS**

```
 1  .col-1 {
 2  width: 40px; 
 3  } 
 4  .col-2 {
 5  width: 80px; 
 6  } 
 7  .col-3 {
 8  width: 120px;
 9  } 
 1  .col-4 {
 0  width: 160px;
 1  } 
 1  .col-5 {
 2  width: 200px;
 3  } 
 1 
```

<h4>Each Loop</h4>

Simply enough, the @each rule returns styles for each item in a list.
List may include multiple comma separated items.

**Sass**

```
 1  &#0064;each $class in uxd, rails, html, css 
 2  .#{$class}-logo
 3  background: url("/img/#{$class}.jpg")
 4 
```

**Compiled CSS**

```
 1  .uxd-logo {
 2  background: url("/img/uxd.jpg");
 3  } 
 4  .rails-logo {
 5  background: url("/img/rails.jpg"); 
 6  } 
 7  .html-logo { 
 8  background: url("/img/html.jpg");  
 9  } 
 10  .css-logo {
 11  background: url("/img/css.jpg");
 12  } 
 13  
```

<h4>While Loop</h4>

The @while rule repeatedly returns styles until the statement becomes
false. The directive accepts a handful of different operators and the
counter variable can be finely controlled allowing for precise looping.

**Sass**

```
 1  $heading: 1 
 2  &#0064;while $heading <= 6  
 3  h#{$heading}
 4  font-size: 2em - ($heading * .25em)
 5  $heading: $heading + 1 
 6 
```

**Compiled CSS**

```
 1  h1 { 
 2  font-size: 1.75em; 
 3  } 
 4  h2 { 
 5  font-size: 1.5em;  
 6  } 
 7  h3 { 
 8  font-size: 1.25em; 
 9  } 
 10  h4 { 
 11 font-size: 1em; 
 12  } 
 13  h5 { font-size: 0.75em; 
 14  } 
 15  h6 { 16 font-size: 0.5em;  
 5  } 
 1 
```

<h4>Other Preprocessors</h4>

Haml and Sass are far from the only preprocessing languages available,
including JavaScript preprocessors as well. Some of the other popular
preprocessors
including [Jade](http://jade-lang.com/), [Slim](http://slim-lang.com/), [LESS](http://lesscss.org/),
and [CoffeeScript](http://coffeescript.org/).

In the interest of brevity Haml and Sass were the only preprocessors
covered in this lesson. They were also chosen because they are built
using Ruby and fit right into Ruby on Rails applications. They've also
got tremendous community support.

When it comes to choosing which, if any, preprocessor to use it is
important to consider what is best for your team and project. Projects
built in Node.js may likely better benefit from Jade. The most important
aspect to consider, though, is what your team is accustomed to using. Do
your research for each project and make the most educated decision.

<h4>Resources & Links</h4>

-[Haml](http://haml.info/) --- HTML Abstraction Markup
 Language

-[Sass](http://sass-lang.com/) --- Syntactically
 Awesome Stylesheets

-[Haml Documentation
 Reference](http://haml.info/docs/yardoc/file.REFERENCE.html)

-[Sass Documentation
 Reference](https://sass-lang.com/documentation/)

-[Sass Playground](http://sassmeister.com/) via
 SassMeister

-[SassScript
 Function](https://sass-lang.com/documentation/modules) via
 Sass Documentation

[**Lesson 4** [Responsive Web
Design](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)
[**Lesson 6**
[jQuery](https://learn.shayhowe.com/advanced-html-css/jquery/)


<h2 align="center">[Lesson 6] jQuery</h2>

<h3>In this Lesson 6</h3>

**JAVASCRIPT**

-[JavaScript
 Intro](https://learn.shayhowe.com/advanced-html-css/jquery/#javascript)

-[jQuery
 Intro](https://learn.shayhowe.com/advanced-html-css/jquery/#jquery)

-[Selectors](https://learn.shayhowe.com/advanced-html-css/jquery/#selectors)

-[Traversing](https://learn.shayhowe.com/advanced-html-css/jquery/#traversing)

-[Manipulation](https://learn.shayhowe.com/advanced-html-css/jquery/#manipulation)

-[Events](https://learn.shayhowe.com/advanced-html-css/jquery/#events)

-[Effects](https://learn.shayhowe.com/advanced-html-css/jquery/#effects)

**SHARE**

In part of being a web designer or front end developer you will commonly
run into JavaScript, often referred to as JS, and jQuery. Within the top
10,000 websites JavaScript is used within [over
92%](https://trends.builtwith.com/docinfo/Javascript) of
them, and jQuery is used within in [over
63%](https://trends.builtwith.com/javascript/jQuery) of
them. Needless to say, they are fairly popular. You may even aspire
to [write](http://jsforcats.com/) JavaScript or jQuery to
build your own behaviors at one point or another.

If you are asking what exactly are JavaScript and jQuery fear not, this
lesson gives a brief overview of JavaScript and then takes a look at
jQuery.

JavaScript Intro

[JavaScript](https://developer.mozilla.org/en-US/docs/JavaScript/A_re-introduction_to_JavaScript) provides
the ability to add interactivity to a website, and help enrich the user
experience. HTML provides a page with **structure** and CSS provides a
page with **appearance**, JavaScript provide a page with **behavior**.

Like CSS, JavaScript should be saved in an external file with
the .js file extension, and then referenced within an HTML document
using the script element. Where the JavaScript reference is placed with
HTML depends on when it should be executed. Generally speaking, the best
place to reference JavaScript files is right before the
closing </body> tag so that the JavaScript file is loaded after all of
the HTML has been parsed. However, at times, JavaScript is needed to
help render HTML and determine it's behavior, thus may be referenced
within a documents head.

```
 1  <script src="script.js"></script> 
 2 
```

<h4>Values & Variables</h4>

Part of the fundamentals of JavaScript include values and variables.
Values, in general, are the different types of values that JavaScript
will recognize, while variables are used to store and share these
values.

Values may include strings of text, true or false Booleans,
numbers, undefined, null, or other values such as functions or objects.

One popular way variables are defined is with the var keyword, followed
by the variable name, an equal sign (=), then the value, ending with a
semicolon (;). The variable name must begin with a letter, underscore
(&#0095;), or dollar sign ($). Variables cannot begin with numbers, although
they may be used subsequently, and they cannot use hyphens whatsoever.
Additionally, JavaScript is case sensitive so letters
include a through z in both lower and uppercase.

The common convention around naming variables is to
use [camelCase](https://en.wikipedia.org/wiki/CamelCase),
without the use of any dashes or underscores. camelCase consist of
combining words while removing spaces, capitalizing the beginning of
each new word except for the initial word. For
example, shay_is_awesome would more commonly named shayIsAwesome.

```
 1  var theStarterLeague = 125; 
 2  var food_truck = 'Coffee';
 3  var mixtape01 = true; 
 4  var vinyl = ]'Miles Davis', 'Frank Sinatra', 'Ray Charles'[; 
 5 
```

<h4>Statements</h4>

As a whole, JavaScript is a set of statements, of which are executed by
the browser in the sequence they are written. These statements provide
commands which determine the different behaviors to be taken. Statements
come in all different shapes and sizes, with multiple statements
separated with semicolons, ;. New statements should begin on a new line,
and indentation should be used when nesting statements for better
legibility, but is not required.

```
 1  log(polaroid);  
 2  return('bicycle lane');
 3  alert('Congratulations, you ' + outcome);  
 4 
```

<h4>Functions</h4>

Adding to the fundamentals of JavaScript, it is important to take a look
at functions. Functions provide a way to perform a set of scripted
behaviors now, or saved for later, and depending on the function they
may even accept different arguments.

A function is defined by using the function keyword followed by the
function name, a list of commas separated arguments wrapped in
parentheses, if necessary, and then the JavaScript statement, or
statements, that defines the function enclosed in curly braces, {}.

```
 1  function sayHello(name) {
 2  return('Hello ' + name);  
 3  } 
 4 
```

<h4>Arrays</h4>

As you may have recognized, some values may be returned as an array.
Arrays include a way to store a list of items, or values. Arrays are
helpful for many reasons, one being the ability to be traversed with
different methods and operators. Additionally, depending on the
situation, arrays can be used to store, and return, a variety of
different values.

Generally speaking arrays are identified within square brackets, [],
with comma separated items. The items start at 0 and increase from
there. When identifying the third item in a list it is actually
identified as [2].

<h4>Objects</h4>

JavaScript is also built on the foundation of objects, which are a
collection of key and value pairs. For example, there may be an object
named school which includes the keys, also known as
properties, name, location, students, and teachers, and their values.

In the example below the variable school is set up as an object to hold
multiple properties. Each property has a key and value. The entire
object is wrapped inside of curly braces, {}, with comma separated
properties, each having a key followed by a colon and value.

```
 1  // Object  
 2  var school = {  
 3  name: 'The Starter League',  
 4  location: 'Merchandise Mart',
 5  students: 120,  
 6  teachers: ]'Jeff', 'Raghu', 'Carolyn', 'Shay'[ 
 7  };
 8  // Array
 9  var school = ]'Austin', 'Chicago', 'Portland'[;  
 1 
```

![Web Inspector Console](./images/image013.png){width="5.0in"
height="3.201388888888889in"}

Fig. 6

Using the developer tools built into the Chrome web browser, JavaScript
may be run from within the console.

<h4>jQuery Intro</h4>

With a basic understanding of JavaScript and some of it's foundations,
it is time to take a look at jQuery. jQuery is an open source JavaScript
library written by John Resig that simplifies the interaction between
HTML, CSS, and JavaScript. Since 2006, when jQuery was released, it has
taken off, being used by websites and companies large and small.

What has made jQuery so popular is it's [ease of
use](https://tutsplus.com/course/30-days-to-learn-jquery/),
with selections resembling CSS and a comprehensible separation of
behavior. The benefits of jQuery are massive, however for our purpose we
will only be considered about the ability to find elements and perform
actions with them.

<h4>Getting Started with jQuery</h4>

The first step to using jQuery is to reference it from within a HTML
document. As previously mentioned with JavaScript, this is done using
the script element just before the closing </body> tag. Since jQuery
is it's own library it is best to keep it separate from all the other
JavaScript being written.

When referencing jQuery there are a few options, specifically as whether
to use the minified or uncompressed version, and as whether to use a
content delivery network, CDN, such as [Google hosted
libraries](https://developers.google.com/speed/libraries/devguide).
If the code being written is for a live, production environment it is
encouraged to use the minified version for better loading times.
Additionally, using a CDN like Google also helps with loading time, and
potential caching benefits.

```
 1  <script src="//aja
 2  x.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script> 
 3  <script src="script.js"></script> 
```

In the code sample above, notice the second script element referencing a
second JavaScript file. All of the custom, handwritten JavaScript and
jQuery should be written in this file. Additionally, this file is
specifically placed after the jQuery file so that it may reference
jQuery functions already defined.

<h4>Where is the leading http?</h4>

You may have noticed that there isn't a leading http within Google CDN
reference example above. The http has been omitted intentionally to
allow for both http and https connections. When working locally, without
the benefit of a web server, the leading http will need to be included
to prevent attempting to locate the file on the systems local disk
drive.

<h4>jQuery Object</h4>

jQuery comes with it's own object, the dollar sign, $, also known
as jQuery. The $ object is specifically made for selecting an element
and then returning that element node to perform an action on it. These
selections and actions should be written in a new file, referenced
outside of the actual jQuery library.

```
 1  $();
 2  jQuery();  
 3 
```

<h4>Document Ready</h4>

Before trigging any jQuery to traverse and manipulate a page it is best
to wait until the DOM is finished loading. Fortunately jQuery has a
ready event, .ready(), which can be called when the HTML document is
ready to be altered. By placing all of our other custom written jQuery
inside of this function we can guarantee that it will not be executed
until the page has loaded and the DOM is ready.

```
 1  $(document).ready(function(event){  
 2  // jQuery code  
 3  });  
 4 
```

<h4>Selectors</h4>

As previously mentioned, one of the core concepts of jQuery is
to [select elements](http://api.jquery.com/category/selectors/) and
perform an action. jQuery has done a great job of making the task of
selecting an element, or elements, extremely easy by mimicking that of
CSS. On top of the general CSS selectors, jQuery has support for all of
the unique CSS3 selectors, which work regardless of which browser is
being used.

Invoking the jQuery object, $(), containing a selector will return that
DOM node to manipulate it. The selector falls within the
parentheses, ('...'), and may select elements just like that of CSS.

```
 1  $('.feature'); // Class selector  
 2  $('li strong'); // Descendant selector 
 3  $('em, i'); // Multiple selector  
 4  $('a]target="&#0095;blank"['); // Attribute selector
 5  $('p:nth-child(2)'); // Pseudo-class selector
 6 
```

<h4>This Selection Keyword</h4>

When working inside of a jQuery function you may want to select the
element in which was referenced inside of the original selector. In this
event the this keyword may be used to refer to the element selected in
the current handler.

```
 1  $('div').click(function(event){
 2  $(this);  
 3  });  
 4 
```

<h4>jQuery Selection Filters</h4>

Should CSS selectors not be enough there are also
custom [filters](http://api.jquery.com/category/selectors/jquery-selector-extensions/) built
into jQuery to help out. These filters are an extension to CSS3 and
provide more control over selecting an element or its relatives.

```
 1  $('div:has(strong)');  
 2  
```

As they stand these filters may be used inside of the selector, however
not being native to the DOM they are a bit slow. The best results with
using these filters is accomplished by using the :filter() method, which
is part of the traversing feature in jQuery.

<h4>Traversing</h4>

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

```
 1  $('div').not('.type, .collection');
 2 
```

<h4>Chaining Methods</h4>

For even more control as to which elements are selected different
traversing methods may be chained together simply by using a dot
in-between them.

The code sample below uses both the .not() method and
the .parent() method. Combined together this will only select the parent
elements of div elements without a class of type or collection.

```
 1  $('div').not('.type, .collection').parent();  
 2 
```

<h4>Traversing Methods</h4>

jQuery has quite a
few [traversing](http://api.jquery.com/category/traversing/) methods
available to use. In general, they all fall into three categories,
filtering, miscellaneous traversing, and DOM tree traversing. The
specific methods within each category may be seen below.

<h4>Filtering</h4>

-.eq()

-.filter()

-.first()

-.has()

-.is()

-.last()

-.map()

-.not()

-.slice()

<h4>Miscellaneous Traversing</h4>

-.add()

-.andSelf()

-.contents()

-.end()

<h4>DOM Tree Traversal</h4>

-.children()

-.closest()

-.find()

-.next()

-.nextAll()

-.nextUntil()

-.offsetParent()

-.parent()

-.parents()

-.parentsUntil()

-.prev()

-.prevAll()

-.prevUntil()

-.siblings()

<h4>Manipulation</h4>

Selecting and traversing elements in the DOM is only part of what jQuery
offers, one other major part is what is possible with those elements
once found. One possibility is
to [manipulate](http://api.jquery.com/category/manipulation/) these
elements, by either reading, adding, or changing attributes or styles.
Additionally, elements may be altered in the DOM, changing their
placement, removing them, adding new elements, and so forth. Overall the
options to manipulate elements are fairly vast.

<h4>Getting & Setting</h4>

The manipulation methods to follow are most commonly used in one of two
directives, that being *getting* or *setting* information. Getting
information revolves around using a selector in addition with a method
to determine what piece of information is to be retrieved. Additionally,
the same selector and method may also be used to set a piece of
information.

```
 1  // Gets the value of the alt attribute  
 2  $('img').attr('alt');  
 3  // Sets the value of the alt attribute  
 4  $('img').attr('alt', 'Wild kangaroo');
 5 
```

In the examples and snippets to follow methods will primarily be used in
a setting mode, however they may also be able to be used in a getting
mode as well.

<h4>Attribute Manipulation</h4>

One part of elements able to be inspected and manipulated are
attributes. A few options include the ability to add, remove, or change
an attribute or its value. In the examples below the .addClass() method
is used to add a class to all even list items, the .removeClass() method
is used to remove all classes from any paragraphs, and lastly
the .attr() method is used to find the value of the title attribute of
any abbr element and set it to Hello World.

```
 1  $('li:even').addClass('even-item');
 2  $('p').removeClass(); 
 3  $('abbr').attr('title', 'Hello World');  
 4 
```

<h4>Attribute Manipulation Methods</h4>

-.addClass()

-.attr()

-.hasClass()

-.prop()

-.removeAttr()

-.removeClass()

-.removeProp()

-.toggleClass()

-.val()

<h4>Style Manipulation</h4>

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

```
 1  $('h1 span').css('font-size', 'normal'); 
 2  $('div').css({  
 3  fontSize: '13px',
 4  background: '#f60'  
 5  });  
 6  $('header').height(200); 
 7  $('.extend').height(30 + 'em'); 
 8 
```

<h4>Style Manipulation Methods</h4>

-.css()

-.height()

-.innerHeight()

-.innerWidth()

-.offset()

-.outerHeight()

-.outerWidth()

-.position()

-.scrollLeft()

-.scrollTop()

-.width()

<h4>DOM Manipulation</h4>

Lastly, we are able to inspect and manipulate the DOM, changing the
placement of elements, adding and removing elements, as well as flat out
altering elements. The options here are deep and varied, allowing for
any potential changes to be made inside the DOM.

Each individual DOM manipulation method has it's own syntax but a few of
them are outlined below. The .prepend() method is adding a
new h3 element just inside any section, the .after() method is adding a
new em element just after the link, and the .text() method is replacing
the text of any h1 elements with the text Hello World.

```
 1  $('section').prepend('<h3>Featured</h3>');
 2  $('a]target="&#0095;blank"[').after('<em>New window.</em>'); 
 3  $('h1').text('Hello World'); 
 4 
```

<h4>DOM Manipulation Methods</h4>

-.after()

-.append()

-.appendTo()

-.before()

-.clone()

-.detach()

-.empty()

-.html()

-.insertAfter()

-.insertBefore()

-.prepend()

-.prependTo()

-.remove()

-.replaceAll()

-.replaceWith()

-.text()

-.unwrap()

-.wrap()

-.wrapAll()

-.wrapInner()

<h4>Events</h4>

One of the beauties of jQuery is the ability to easily add [event
handlers](http://api.jquery.com/category/events/), which
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

```
 1  $('li').click(function(event){ 
 2  $(this).addClass('saved-item');
 3  });  
 4 
```

<h4>Event Flexibility</h4>

The .click() event method, along with a handful of other event methods,
is actually a [shorthand method](http://jqfundamentals.com/chapter/events) 
which uses the .on() method introduced in jQuery 1.7. The .on() method
provides quite a bit of flexibility, using automatic delegation for
elements that get added to the page dynamically.

Making use of the .on() method the first argument should be the native
event name while the second argument should be the event handler
function. Looking at the example from before, the .on() method is called
in place of the .click() method. Now the click event name is passed in
as the first argument inside the .on() method with the event handler
function staying the same as before.

```
 1  $('li').on('click', function(event){ 
 2  $(this).addClass('saved-item');
 3  });  
 4 
```

<h4>Nesting Events</h4>

It is possible to have multiple event handlers and triggers, nesting one
inside another. As an example, below the .on() event method is passed
the hover argument, thus being called when hovering over any element
with the class of pagination. Upon calling the .on() event
the .click() event is called on the anchor with the up ID.

```
 1  $('.pagination').on('hover', function(event){ 
 2  $('a#up').click(); 
 3  });  
 4 
```

<h4>Event Demo</h4>

Using an alert message as a demo, the following code snippets show how
to create an alert message and then removing that message based upon
clicking the close icon.

<h4>HTML</h4>

```
 1  <div class="notice-warning">
 2  <div class="notice-close">x</div>  
 3  <strong>Warning!</strong> I"m about to lose my cool.  
 4  </div> 
 5  
```

**JavaScript**

```
 1  $('.notice-close').on('click', function(event){
 2  $('.notice-warning').remove();  
 3  });
 4  
```

<h4>Demo</h4>

<h4>Event Methods</h4>

jQuery provides quite a few methods, all of which are based around
registering user behaviors as they interact with the browser. These
methods register quite a few events, most popularly, but not limited to,
browser, form, keyboard, and mouse events. The most popular of these
methods include:

<h4>Browser Events</h4>

-.resize()

-.scroll()

<h4>Document Loading</h4>

-.ready()

<h4>Event Handler Attachment</h4>

-.off()

-.on()

-.one()

-jQuery.proxy()

-.trigger()

-.triggerHandler()

-.unbind()

-.undelegate()

<h4>Event Object</h4>

-event.currentTarget

-event.preventDefault()

-event.stopPropagation()

-event.target

-event.type

<h4>Form Events</h4>

-.blur()

-.change()

-.focus()

-.select()

-.submit()

<h4>Keyboard Events</h4>

-.focusin()

-.focusout()

-.keydown()

-.keypress()

-.keyup()

<h4>Mouse Events</h4>

-.click()

-.dblclick()

-.focusin()

-.focusout()

-.hover()

-.mousedown()

-.mouseenter()

-.mouseleave()

-.mousemove()

-.mouseout()

-.mouseover()

-.mouseup()

<h4>Effects</h4>

Next to events, jQuery also provides a handful of customizable effects.
These effects come by the way of different methods, including event
methods for showing and hiding content, fading content in and out, or
sliding content up and down. All of these are ready to use methods and
may be customized as best see fit.

Each effect method has it's own syntax so it is best to reference the
jQuery [effects documentation](http://api.jquery.com/category/effects/) 
for specific syntax around each method. Most commonly though, effects
generally accept a duration, easing, and the ability to specify a
callback function.

<h4>jQuery CSS Animations</h4>

Custom animations of different CSS properties can be accomplished in
jQuery, although this is a little less relevant as CSS can now handle
animations itself. CSS animations offer better performance from a
browser processing standpoint and are preferred where possible. jQuery
animation effects, with the help of Modernizr, make for a perfect backup
solution to any browser not supporting CSS animations.

<h4>Effect Duration</h4>

Using the .show() method as an example, the first parameter available to
optionally pass in to the method is the duration, which can be
accomplished using a keyword or milliseconds value. The
keyword slow defaults to 600 milliseconds, while the
keyword fast defaults to 200 milliseconds. Using a keyword value is
fine, but millisecond values may also be passed in directly. Keyword
values must be quoted while millisecond values do not.

```
 1  $('.error').show();
 2  $('.error').show('slow'); 
 3  $('.error').show(500);
 4 
```

<h4>Effect Easing</h4>

In addition to setting the duration in which an effect takes place the
easing, or speed at which an animation progresses at during different
times within the animation, may also be set. By default jQuery has two
keyword values for easing, the default value is swing with the
additional value being linear. The default swing value starts the
animation at a slow pace, picking up speed during the animation, and
then slows down again before completion. The linear value runs the
animation at one constant pace for the entire duration.

```
 1  $('.error').show('slow', 'linear');
 2  $('.error').show(500, 'linear');
 3 
```

<h4>jQuery UI</h4>

The two easing values that come with jQuery may be extend with the use
of different plug-ins, of which may offer additional values. One of the
most popular plug-ins is the [jQuery UI](http://jqueryui.com/) suite.

On top of new easing values jQuery UI also provides a handful other
interactions, effects, widgets, and other helpful resources worth taking
a look at.

<h4>Effect Callback</h4>

When an animation is completed it is possible to run another function,
called a callback function. The callback function should be placed after
the duration or easing, if either exist. Inside this function new events
or effects may be placed, each following their own required syntax.

```
 1  $('.error').show('slow', 'linear', function(event){  
 2  $('.error .status').text('Continue');
 3  });  
 4 
```

<h4>Effect Syntax</h4>

As previously mentioned, each effect method has it's own syntax which
can be found in the jQuery [effects documentation](http://api.jquery.com/category/effects/).
The duration, easing, and callback parameters outlined here are common,
but not available on every method. It is best to review the syntax of a
method should you have any questions around it.

<h4>Effects Demo</h4>

Taking the same events demo from above, the .remove() method is now used
as part of a callback function on the .fadeOut() method. Using
the .fadeOut() method allows for the alert message to gradually fade out
rather than quickly disappearing, then be removed from the DOM after the
animation is complete.

<h4>HTML</h4>

```
 1  <div class="notice-warning">
 2  <div class="notice-close">x</div>  
 3  <strong>Warning!</strong> I'm about to lose my cool.  
 4  </div> 
 5  
```

**JavaScript**

```
 1  $('.notice-close').on('click', function(event){  
 2  $('.notice-warning').fadeOut('slow', function(event){  
 3  $(this).remove(); 
 4  });  
 5  });  
 6 
```

<h4>Demo</h4>

<h4>Basic Effects

-.hide()

-.show()

-.toggle()

<h4>Custom Effects</h4>

-.animate()

-.clearQueue()

-.delay()

-.dequeue()

-jQuery.fx.interval

-jQuery.fx.off

-.queue()

-.stop()

<h4>Fading Effects</h4>

-.fadeIn()

-.fadeOut()

-.fadeTo()

-.fadeToggle()

<h4>Sliding Effects</h4>

-.slideDown()

-.slideToggle()

-.slideUp()

<h4>Slide Demo</h4>

<h4>HTML</h4>

```
 1  <div class="panel">  
 2    <div class="panel-stage"></div>
 3    <a href="#" class="panel-tab">Open <span>&#9660;</span></a> 
 4  </div>
 5 
```

**JavaScript**

```
 1  $('.panel-tab').on('click', function(event){  
 2    event.preventDefault();  
 3    $('.panel-stage').slideToggle('slow', function(event){ 
 4      if($(this).is(':visible')){ 
 5        $('.panel-tab').html('Close <span>&#9650;</span>');
 6      } else {
 7        $('.panel-tab').html('Open <span>&#9660;</span>'); 
 8      } 
 9    });  
 10 });  
 11 
```

Demo

Tabs Demo

<h4>HTML</h4>

```
 1  <ul class="tabs-nav"> 
 2  <li><a href="#tab-1">Features</a></li> 
 3  <li><a href="#tab-2">Details</a></li>  
 4  </ul>  
 5  <div class="tabs-stage"> 
 6  <div id="tab-1">...</div>
 7  <div id="tab-2">...</div>
 8  </div> 
 9  
```

**JavaScript**

```
 1  // Show the first tab by default
 2  $('.tabs-stage div').hide(); 
 3  $('.tabs-stage div:first').show(); 
 4  $('.tabs-nav li:first').addClass('tab-active');
 5  // Change tab class and display content 
 6  $('.tabs-nav a').on('click', function(event){  
 7  event.preventDefault();
 8  $('.tabs-nav li').removeClass('tab-active');
 9  $(this).parent().addClass('tab-active');
 10  $('.tabs-stage div').hide(); 
 11  $($(this).attr('href')).show();
 12  });
 13  
```

<h4>Demo</h4>

<h4>Resources &amp; Links</h4>

-[JavaScript For Cats](http://jsforcats.com/)

-[A Re-introduction to
 JavaScript](https://developer.mozilla.org/en-US/docs/JavaScript/A_re-introduction_to_JavaScript) via
 Mozilla Developer Network

-[30 Days to Learn
 jQuery](https://tutsplus.com/course/30-days-to-learn-jquery/) via
 Tuts+ Premium

-[Google Hosted
 Libraries](https://developers.google.com/speed/libraries/devguide)

-[jQuery Documentation](http://docs.jquery.com/)

-[jQuery Fundamentals](http://jqfundamentals.com/) via
 Bocoup

-[jQuery UI](http://jqueryui.com/)

[**Lesson 5**]
[Preprocessors](https://learn.shayhowe.com/advanced-html-css/preprocessors/)
[**Lesson 7**]
[Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/)

<h2 align="center">[Lesson 7] Transforms</h2>

<h3>In this Lesson 7</h3>

GitlabGitLab is the most comprehensive AI-powered DevSecOps Platform.
Software. Faster.

<h4>CSS</h4>

-[Transform
 Syntax](https://learn.shayhowe.com/advanced-html-css/css-transforms/#transform-syntax)

-[2D
 Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/#two-dimensional-transforms)

-[Combining
 Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/#combining-transforms)

-[Transform
 Origin](https://learn.shayhowe.com/advanced-html-css/css-transforms/#transform-origin)

-[Perspective](https://learn.shayhowe.com/advanced-html-css/css-transforms/#perspective)

-[3D
 Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/#three-dimensional-transforms)

-[Transform
 Style](https://learn.shayhowe.com/advanced-html-css/css-transforms/#transform-style)

-[Backface
 Visibility](https://learn.shayhowe.com/advanced-html-css/css-transforms/#backface-visibility)

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
of [Chrome](https://tools.google.com/dlpage/chromesxs/) to
see all of these transforms in action.

<h4>Transform Syntax</h4>

The actual syntax for the transform property is quite simple, including
the transform property followed by the value. The value specifies the
transform type followed by a specific amount inside parentheses.

```
 1  div {
 2  -webkit-transform: scale(1.5); 
 3  -moz-transform: scale(1.5); 
 4  -o-transform: scale(1.5);
 5  transform: scale(1.5);
 6  } 
 7 
```

Notice how the transform property includes multiple vendor prefixes to
gain the best support across all browsers. The un-prefixed declaration
comes last to overwrite the prefixed versions, should a browser fully
support the transform property.

In the interest of brevity, the remainder of this lesson will not
include vendor prefixes. They are, however, strongly encouraged for any
code in a production environment. Over time we will be able to remove
these prefixes, however keeping them in is the safest approach for the
time being.

<h4>2D Transforms</h4>

Elements may be distorted, or transformed, on both a two-dimensional
plane or a three-dimensional plane. Two-dimensional transforms work on
the x and y axes, known as horizontal and vertical axes.
Three-dimensional transforms work on both the x and y axes, as well as
the z axis. These three-dimensional transforms help define not only the
length and width of an element, but also the depth. We'll start by
discussing how to [transform
elements](http://www.css3files.com/transform/) on a
two-dimensional plane, and then work our way into three-dimensional
transforms.

<h4>2D Rotate</h4>

The transform property accepts a handful of different values.
The rotate value provides the ability to rotate an element
from 0 to 360 degrees. Using a positive value will rotate an element
clockwise, and using a negative value will rotate the element
counterclockwise. The default point of rotation is the center of the
element, 50% 50%, both horizontally and vertically. Later we will
discuss how you can change this default point of rotation.

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: rotate(20deg);
 3  } 
 4  .box-2 {
 5  transform: rotate(-55deg);  
 6  } 
 7 
```

<h4>Rotate Demo</h4>

The gray box behind the rotated element symbolizes the original position
of the element. Additionally, upon hover the box will rotate 360 degrees
horizontally. As the lesson progresses, keep an eye out for the gray box
within each demonstration as a reference to the element's original
position and the horizontal rotation to help demonstrate an elements
alteration and depth.

<h4>2D Scale</h4>

Using the scale value within the transform property allows you to change
the appeared size of an element. The default scale value is 1, therefore
any value between .99 and .01 makes an element appear smaller while any
value greater than or equal to 1.01 makes an element appear larger.

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: scale(.75);
 3  } 
 4  .box-2 {
 5  transform: scale(1.25);  
 6  } 
 7 
```

<h4>Scale Demo</h4>

It is possible to scale only the height or width of an element using
the scaleX and scaleY values. The scaleX value will scale the width of
an element while the scaleY value will scale the height of an element.
To scale both the height and width of an element but at different sizes,
the x and y axis values may be set simultaneously. To do so, use
the scale transform declaring the x axis value first, followed by a
comma, and then the y axis value.

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3  <figure class="box-3">Box 3</figure>
 4 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: scaleX(.5);
 3  } 
 4  .box-2 {
 5  transform: scaleY(1.15); 
 6  } 
 7  .box-3 {
 8  transform: scale(.5, 1.15); 
 9  } 
 10  
```

<h4>Multiple Scaling Demo</h4>

<h4>2D Translate</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3  <figure class="box-3">Box 3</figure>
 4 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: translateX(-10px);  
 3  } 
 4  .box-2 {
 5  transform: translateY(25%); 
 6  } 
 7  .box-3 {
 8  transform: translate(-10px, 25%); 
 9  } 
 10 
```

<h4>Translate Demo</h4>

<h4>2D Skew</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3  <figure class="box-3">Box 3</figure>
 4 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: skewX(5deg);  
 3  } 
 4  .box-2 {
 5  transform: skewY(-20deg);
 6  } 
 7  .box-3 {
 8  transform: skew(5deg, -20deg); 
 9  } 
 10 
```

<h4>Skew Demo</h4>

<h4>Combining Transforms</h4>

It is common for multiple transforms to be used at once, rotating and
scaling the size of an element at the same time for example. In this
event multiple transforms can be combined together. To combine
transforms, list the transform values within the transform property one
after the other without the use of commas.

Using multiple transform declarations will not work, as each declaration
will overwrite the one above it. The behavior in that case would be the
same as if you were to set the height of an element numerous times.

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: rotate(25deg) scale(.75); 
 3  } 
 4  .box-2 {
 5  transform: skew(10deg, 20deg) translateX(20px); 
 6  } 
 7 
```

<h4>Combining Transforms Demo</h4>

Behind every transform there is also a matrix explicitly defining the
behavior of the transform. Using the rotate, scale, transition,
and skew values provide an easy way to establish this matrix. However,
should you be mathematically inclined, and prefer to take a [deeper
dive](http://dev.opera.com/articles/view/understanding-the-css-transforms-matrix/) into
transforms, try your hand at using the matrix property.

<h4>2D Cube Demo</h4>

<h4>HTML</h4>

```
 1  <div class="cube"> 
 2  <figure class="side top">1</figure>  
 3  <figure class="side left">2</figure> 
 4  <figure class="side right">3</figure>
 5  </div> 
 6  
```

<h4>CSS</h4>

```
 1  .cube {  
 2  position: relative; 
 3  }  
 4  .side {  
 5  height: 95px; 
 6  position: absolute; 
 7  width: 95px;  
 8  }  
 9  .top {
 10  background: #9acc53;
 11  transform: rotate(-45deg) skew(15deg, 15deg); 
 12  }  
 13  .left {  
 14  background: #8ec63f;
 15  transform: rotate(15deg) skew(15deg, 15deg) translate(-50%, 100%); 
 16  }  
 17  .right { 
 18  background: #80b239;
 19  transform: rotate(-15deg) skew(-15deg, -15deg) translate(50%,
 10  100%);
 21  }  
 22  
```

<h4>Demo</h4>

<h4>Transform Origin</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3  <figure class="box-3">Box 3</figure>
 4  <figure class="box-4">Box 3</figure>
 5 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: rotate(15deg);
 3  transform-origin: 0 0;
 4  } 
 5  .box-2 {
 6  transform: scale(.5); 
 7  transform-origin: 100% 100%;
 8  } 
 9  .box-3 {
 1  transform: skewX(20deg); 
 0  transform-origin: top left; 
 1  } 
 1  .box-4 {
 2  transform: scale(.75) translate(-10px, -10px);  
 3  transform-origin: 20px 50px;
 1  } 
 4 
```

<h4>Transform Origin Demo</h4>

Notably, the transform-origin property does run into some issues when
also using the translate transform value. Since both of them are
attempting to position the element, their values can collide. Use the
two of these with caution, always checking to make sure the desired
outcome is achieved.

<h4>Perspective</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box">Box 1</figure>
 2  <figure class="box">Box 2</figure>
 3  <figure class="box">Box 3</figure>
 4 
```

<h4>CSS</h4>

```
 1  .box {  
 2  transform: perspective(200px) rotateX(45deg);
 3  } 
 4 
```

<h4>Perspective Value Demo</h4>

The following example shows a handful of elements, side by side, all
transformed using the same perspective, accomplished by using
the perspective property on their direct parent element.

<h4>HTML</h4>

```
 1  <div class="group">  
 2  <figure class="box">Box 1</figure>
 3  <figure class="box">Box 2</figure>
 4  <figure class="box">Box 3</figure>
 5  </div>
 6 
```

<h4>CSS</h4>

```
 1  .group {
 2  perspective: 200px;
 3  } 
 4  .box {  
 5  transform: rotateX(45deg);  
 6  } 
 7 
```

<h4>Perspective Property Demo</h4>

<h4>Perspective Depth Value</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: perspective(100px) rotateX(45deg);
 3  } 
 4  .box-2 {
 5  transform: perspective(1000px) rotateX(45deg);  
 6  } 
 7 
```

<h4>Perspective Depth Value Demo</h4>

<h4>Perspective Origin</h4>

As with setting a transform-origin you can also set
a perspective-origin. The same values used for
the transform-origin property may also be used with
the perspective-origin property, and maintain the same relationship to
the element. The large difference between the two falls where the origin
of a transform determines the coordinates used to calculate the change
of a transform, while the origin of a perspective identifies the
coordinates of the vanishing point of a transform.

<h4>HTML</h4>

```
 1  <div class="original original-1">
 2  <figure class="box">Box 1</figure>
 3  </div>
 4  <div class="original original-2">
 5  <figure class="box">Box 2</figure>
 6  </div>
 7  <div class="original original-3">
 8  <figure class="box">Box 3</figure>
 9  </div>
 10  
```

<h4>CSS</h4>

```
 1  .original {
 2  perspective: 200px;
 3  } 
 4  .box {  
 5  transform: rotateX(45deg);  
 6  } 
 7  .original-1 {
 8  perspective-origin: 0 0; 
 9  } 
 10  .original-2 {
 11  perspective-origin: 75% 75%;
 12 } 
 13  .original-3 {
 14  perspective-origin: 20px 40px; 
 15 } 
 16 
```

<h4>Perspective Origin Demo</h4>

<h4>3D Transforms</h4>

Working with two-dimensional transforms we are able to alter elements on
the horizontal and vertical axes, however there is another axis along
which we can transform elements. Using [three-dimensional
transforms](http://24ways.org/2010/intro-to-css-3d-transforms) we
can change elements on the z axis, giving us control of depth as well as
length and width.

<h4>3D Rotate</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3  <figure class="box-3">Box 3</figure>
 4 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: perspective(200px) rotateX(45deg);
 3  } 
 4  .box-2 {
 5  transform: perspective(200px) rotateY(45deg);
 6  } 
 7  .box-3 {
 8  transform: perspective(200px) rotateZ(45deg);
 9  } 
 10 
```

<h4>3D Rotate Demo</h4>

<h4>3D Scale</h4>

By using the scaleZ three-dimensional transform elements may be scaled
on the z axis. This isn't extremely exciting when no other
three-dimensional transforms are in place, as there is nothing in
particular to scale. In the demonstration below the elements are being
scaled up and down on the z axis, however the rotateX value is added in
order to see the behavior of the scaleZ value. When removing
the rotateX in this case, the elements will appear to be unchanged.

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: perspective(200px) scaleZ(1.75) rotateX(45deg);  
 3  } 
 4  .box-2 {
 5  transform: perspective(200px) scaleZ(.25) rotateX(45deg);
 6  } 
 7 
```

<h4>3D Scale Demo</h4>

<h4>3D Translate</h4>

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

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: perspective(200px) translateZ(-50px);
 3  } 
 4  .box-2 {
 5  transform: perspective(200px) translateZ(50px); 
 6  } 
 7 
```

<h4>3D Translate Demo</h4>

<h4>3D Skew</h4>

Skew is the one two-dimensional transform that **cannot** be transformed
on a three-dimensional scale. Elements may be skewed on
the x and y axis, then transformed three-dimensionally as wished, but
they cannot be skewed on the z axis.

<h4>Shorthand 3D Transforms</h4>

As with combining two-dimensional transforms, there are also properties
to write out shorthand three-dimensional transforms. These properties
include rotate3d, scale3d, transition3d, and matrix3d. These properties
do require a bit more math, as well as a
strong [understanding](https://developer.mozilla.org/en/CSS/transform-function) of
the matrices behind each transform. Should you be interested in looking
a bit deeper into them, please do!

<h4>Transform Style</h4>

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

<h4>HTML</h4>

```
 1  <div class="rotate three-d">  
 2  <figure class="box">Box 1</figure>
 3  </div>
 4  <div class="rotate"> 
 5  <figure class="box">Box 2</figure>
 6  </div>
 7 
```

<h4>CSS</h4>

```
 1  .rotate {  
 2  transform: perspective(200px) rotateY(45deg);
 3  } 
 4  .three-d { 
 5  transform-style: preserve-3d;  
 6  } 
 7  .box {  
 8  transform: rotateX(15deg) translateZ(20px);  
 9  transform-origin: 0 0;
 10  } 
 11 
```

<h4>Transform Style Demo</h4>

To see an additional example of the transform-style property in action
check out the
WebKit [explanation](http://www.webkit.org/blog-files/3d-transforms/transform-style.html).

<h4>Backface Visibility</h4>

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
using [animations](https://css-tricks.com/almanac/properties/b/backface-visibility/).

<h4>HTML</h4>

```
 1  <figure class="box-1">Box 1</figure>
 2  <figure class="box-2">Box 2</figure>
 3 
```

<h4>CSS</h4>

```
 1  .box-1 {
 2  transform: rotateY(180deg); 
 3  } 
 4  .box-2 {
 5  backface-visibility: hidden;
 6  transform: rotateY(180deg); 
 7  } 
 8 
```

<h4>Backface Visibility Demo</h4>

<h4>3D Cube Demo</h4>

<h4>HTML</h4>

```
 1  <div class="cube-container">
 2  <div class="cube"> 
 3  <figure class="side front">1</figure>
 4  <figure class="side back">2</figure> 
 5  <figure class="side left">3</figure> 
 6  <figure class="side right">4</figure>
 7  <figure class="side top">5</figure>  
 8  <figure class="side bottom">6</figure>  
 9  </div> 
 10  </div> 
 11 
```

<h4>CSS</h4>

```
 1  .cube-container {
 2  height: 200px;
 3  perspective: 300;
 4  position: relative;
 5  width: 200px;
 6  }
 7  .cube {
 8  height: 100%;
 9  position: absolute;
 10  transform: translateZ(-100px);
 11  transform-style: preserve-3d;
 12  width: 100%;
 13  }
 14 .side {
 15 background: rgba(45, 179, 74, .3);
 16  border: 2px solid #2db34a;
 17  height: 196px;
 18  position: absolute;
 19  width: 196px;
 20  }
 21 .front {
 22  transform: translateZ(100px);
 23  }
 24  .back {
 25  transform: rotateX(180deg) translateZ(100px);
 26  }
 27 .left {
 28  transform: rotateY(-90deg) translateZ(100px);
 29 }
 30  .right {
 31  transform: rotateY(90deg) translateZ(100px); 
 32 } 
 33 .top {  
 34  transform: rotateX(90deg) translateZ(100px); 
 35  } 
 36  .bottom { 
 37  transform: rotateX(-90deg) translateZ(100px);
 38  } 
 40 
```


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


<h2 align="center">[Lesson 8] Transitions &amp; Animations</h2>

<h3>In this Lesson 8</h3>

GitlabGitLab is the only place where enterprises build mission critical software.

<h4>CSS</h4>

-[Transitions](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#transitions)

-[Shorthand
 Transitions](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#shorthand-transitions)

-[Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#animations)

-[Customizing
 Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#customizing-animations)

-[Shorthand
 Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/#shorthand-animations)

**SHARE**

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

<h4>Transitions</h4>

As mentioned, for
a [transition](http://www.alistapart.com/articles/understanding-css3-transitions/) to
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

```
 1  .box {
 2    background: #2db34a;
 3    transition-property: background;
 4    transition-duration: 1s;
 5    transition-timing-function: linear;
 6  }
 7  .box:hover {
 8    background: #ff7b29;
 9  }
 10 
```

<h4>Transition Demo</h4>

<h4>Vendor Prefixes</h4>

The code above, as with the rest of the code samples in this lesson, are
not vendor prefixed. This is intentionally un-prefixed in the interest
of keeping the code snippet small and comprehensible. For the best
support across all browsers, use vendor prefixes.

For reference, the prefixed version of the code above would look like
the following.

```
 1  .box {
 2    background: #2db34a;
 3    -webkit-transition-property: background;
 4    -moz-transition-property: background; 
 5    -o-transition-property: background;
 6    transition-property: background;
 7    -webkit-transition-duration: 1s;
 8    -moz-transition-duration: 1s;
 9    -o-transition-duration: 1s;  
 10   transition-duration: 1s;  
 11   -webkit-transition-timing-function: linear;
 12   -moz-transition-timing-function: linear;
 13   -o-transition-timing-function: linear;
 14   transition-timing-function: linear;
 15 } 
 16 .box:hover {
 17   background: #ff7b29;
 18 } 
```

<h4>Transitional Property</h4>

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

```
 1  .box {  
 2  background: #2db34a;  
 3  border-radius: 6px 
 4  transition-property: background, border-radius; 
 5  transition-duration: 1s; 
 6  transition-timing-function: linear;  
 7  } 
 8  .box:hover { 
 9  background: #ff7b29;  
 10  border-radius: 50%;
 11 } 
 12 
```

<h4>Transition Property Demo</h4>

<h4>Transitional Properties</h4>

It is important to note, **not all properties may be transitioned**,
only properties that have an identifiable halfway point. Colors, font
sizes, and the alike may be transitioned from one value to another as
they have recognizable values in-between one another.
The display property, for example, may not be transitioned as it does
not have any midpoint. A handful of the more popular transitional
properties include the following.

-background-color

-background-position

-border-color

-border-width

-border-spacing

-bottom

-clip

-color

-crop

-font-size

-font-weight

-height

-left

-letter-spacing

-line-height

-margin

-max-height

-max-width

-min-height

-min-width

-opacity

-outline-color

-outline-offset

-outline-width

-padding

-right

-text-indent

-text-shadow

-top

-vertical-align

-visibility

-width

-word-spacing

-z-index

<h4>Transition Duration</h4>

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

```
 1  .box {  
 2  background: #2db34a;  
 3  border-radius: 6px;
 4  transition-property: background, border-radius; 
 5  transition-duration: .2s, 1s;  
 6  transition-timing-function: linear;  
 7  } 
 8  .box:hover { 
 9  background: #ff7b29;  
 10  border-radius: 50%;
 11  } 
 12 
```

<h4>Transition Duration Demo</h4>

<h4>Transition Timing</h4>

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

Each timing function has a [cubic-bezier
curve](http://www.roblaplaca.com/examples/bezierBuilder/) behind
it, which can be specifically set using the cubic-bezier(x1, y1, x2,
y2) value. Additional values include step-start, step-stop, and a
uniquely identified steps(number_of_steps, direction) value.

When transitioning multiple properties, you can identify multiple timing
functions. These timing function values, as with other transition
property values, may be declared as comma separated values.

```
 1  .box {
 2  background: #2db34a;
 3  border-radius: 6px;
 4  transition-property: background, border-radius;
 5  transition-duration: .2s, 1s;
 6  transition-timing-function: linear, ease-in;
 7  }
 8  .box:hover {
 9  background: #ff7b29;
 10 border-radius: 50%;
 11 }
 12 
```

<h4>Transition Timing Demo</h4>

<h4>Transition Delay</h4>

On top of declaring the transition property, duration, and timing
function, you can also set a delay with the transition-delay property.
The delay sets a time value, seconds or milliseconds, that determines
how long a transition should be stalled before executing. As with all
other transition properties, to delay numerous transitions, each delay
can be declared as comma separated values.

```
 1  .box {
 2  background: #2db34a;
 3  border-radius: 6px
 4  transition-property: background, border-radius;
 5  transition-duration: .2s, 1s;
 6  transition-timing-function: linear, ease-in;
 7  transition-delay: 0s, 1s;
 8  }
 9  .box:hover {
 10 background: #ff7b29;
 11 border-radius: 50%;
 12 }
 13  
```

<h4>Transition Delay Demo</h4>

<h4>Shorthand Transitions</h4>

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

```
 1  .box {  
 2  background: #2db34a;  
 3  border-radius: 6px;
 4  transition: background .2s linear, border-radius 1s ease-in 1s;
 5  } 
 6  .box:hover { 
 7  color: #ff7b29; 
 8  border-radius: 50%;
 9  } 
 1 
```

<h4>Shorthand Transitions Demo</h4>

<h4>Transitional Button</h4>

<h4>HTML</h4>

```
 1  <button>Awesome Button</button>
 2  
```

<h4>CSS</h4>

```
 1  button { 
 2  border: 0; 
 3  background: #0087cc;
 4  border-radius: 4px; 
 5  box-shadow: 0 5px 0 #006599; 
 6  color: #fff;  
 7  cursor: pointer; 
 8  font: inherit;
 9  margin: 0; 
 10  outline: 0;
 11  padding: 12px 20px; 
 12  transition: all .1s linear;  
 13  }  
 14 button:active {  
 15  box-shadow: 0 2px 0 #006599; 
 16  transform: translateY(3px);  
 17  }  
 18  
```

<h4>Demo</h4>

<h4>Card Flip</h4>

<h4>HTML</h4>

```
 1  <div class="card-container">
 2  <div class="card"> 
 3  <div class="side">...</div> 
 4  <div class="side back">...</div> 
 5  </div> 
 6  </div> 
 7  
```

<h4>CSS</h4>

```
 1  .card-container {
 2  height: 150px;
 3  perspective: 600;
 4  position: relative; 
 5  width: 150px; 
 6  }  
 7  .card {  
 8  height: 100%; 
 9  position: absolute; 
 10  transform-style: preserve-3d;
 11  transition: all 1s ease-in-out; 
 12  width: 100%;  
 13  }  
 14  .card:hover { 
 15  transform: rotateY(180deg);  
 16  }  
 17  .card .side { 
 18  backface-visibility: hidden; 
 19  height: 100%; 
 20  position: absolute; 
 21  width: 100%;  
 22  }  
 23  .card .back { 
 24  transform: rotateY(180deg);  
 25  }  
 26  
```

<h4>Demo</h4>

<h4>Animations</h4>

Transitions do a great job of building out visual interactions from one
state to another, and are perfect for these kinds of single state
changes. However, when more control is required, transitions need to
have multiple states. In return, this is
where [animations](http://coding.smashingmagazine.com/2011/09/14/the-guide-to-css-animation-principles-and-examples/) pick
up where transitions leave off.

<h4>Animations Keyframes</h4>

To set multiple points at which an element should undergo a transition,
use the @keyframes rule. The @keyframes rule includes the animation
name, any animation breakpoints, and the properties intended to be
animated.

```
 1  @keyframes slide {
 2    0% {
 3      left: 0;
 4      top: 0;
 5    }
 6    50% {
 7      left: 244px;
 8      top: 100px;
 9    }
 10   100% {
 11     left: 488px;
 12     top: 0;
 13   }
 14 }
 15 
```

<h4>Vendor Prefixing the Keyframe Rule</h4>

The @keyframes rule must be vendor prefixed, just like all of the
other transition and animation properties. The vendor prefixes for
the @keyframes rule look like the following:

<ul>
  <li>@-moz-keyframes</li>
  <li>@-o-keyframes</li>
  <li>@-webkit-keyframes</li>
</ul>

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

<h4>Animations Keyframes Demo</h4>

Hover over the ball below to see the animation in action.

<h4>Animation Name</h4>

Once the keyframes for an animation have been declared they need to be
assigned to an element. To do so, the animation-name property is used
with the animation name, identified from the @keyframes rule, as the
property value. The animation-name declaration is applied to the element
in which the animation is to be applied to.

```
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  } 
 4 
```

Using the animation-name property alone isn't enough though. You also
need to declare an animation-duration property and value so that the
browser knows how long an animation should take to complete.

<h4>Animation Duration, Timing Function, & Delay</h4>

Once you have declared the animation-name property on an element,
animations behave similarly to transitions. They include a duration,
timing function, and delay if desired. To start, animations need a
duration declared using the animation-duration property. As with
transitions, the duration may be set in seconds or milliseconds.

```
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  animation-duration: 2s;  
 4  } 
 5 
```

A timing function and delay can be declared using
the animation-timing-function and animation-delay properties
respectively. The values for these properties mimic and behave just as
they do with transitions.

```
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  animation-duration: 2s;  
 4  animation-timing-function: ease-in-out; 
 5  animation-delay: .5s; 
 6  } 
 7 
```

The animation below should cause the ball to bounce once while moving to
the left, however only when hovering over the stage.

<h4>HTML</h4>

```
 1  <div class="stage">  
 2  <figure class="ball"></figure> 
 3  </div>
 4 
```

<h4>CSS</h4>

```
 1  &#0064;keyframes slide {
 2  0% {
 3  left: 0;
 4  top: 0;
 5  }
 6  50% {
 7  left: 244px;
 8  top: 100px;
 9  }
 10  100% {
 11  left: 488px; 
 12  top: 0; 
 13  } 
 14   } 
 15  .stage {
 16  height: 150px;  
 17  position: relative;
 18  } 
 19  .ball { 
 20  height: 50px;
 21  position: absolute;
 22  width: 50px; 
 23  } 
 24  .stage:hover .ball {  
 25  animation-name: slide;
 26  animation-duration: 2s;  
 27  animation-timing-function: ease-in-out; 
 28  animation-delay: .5s; 
 29  } 
 30 
```

<h4>Animation Demo</h4>

Hover over the ball below to see the animation in action.

<h4>Customizing Animations</h4>

Animations also provide the ability to further customize an element's
behavior, including the ability to declare the number of times an
animation runs, as well as the direction in which an animation
completes.

<h4>Animation Iteration</h4>

By default, animations run their cycle once from beginning to end and
then stop. To have an animation repeat itself numerous times
the animation-iteration-count property may be used. Values for
the animation-iteration-count property include either an integer or
the infinite keyword. Using an integer will repeat the animation as many
times as specified, while the infinite keyword will repeat the animation
indefinitely in a never ending fashion.

```
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  animation-duration: 2s;  
 4  animation-timing-function: ease-in-out; 
 5  animation-delay: .5s; 
 6  animation-iteration-count: infinite; 
 7  }
 8  
```

<h4>Animation Iteration Demo</h4>

Hover over the ball below to see the animation in action.

<h4>Animation Direction</h4>

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

```
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  animation-duration: 2s;  
 4  animation-timing-function: ease-in-out; 
 5  animation-delay: .5s; 
 6  animation-iteration-count: infinite; 
 7  animation-direction: alternate;
 8  }
 9  
```

<h4>Animation Direction Demo</h4>

Hover over the ball below to see the animation in action.

<h4>Animation Play State</h4>

The animation-play-state property allows an animation to be played or
paused using the running and paused keyword values respectively. When
you play a paused animation, it will resume running from its current
state rather than starting from the very beginning again.

In the example below the animation-play-state property is set
to paused when making the stage active by clicking on it. Notice how the
animation will temporarily pause until you let up on the mouse.

```
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  animation-duration: 2s;  
 4  animation-timing-function: ease-in-out; 
 5  animation-delay: .5s; 
 6  animation-iteration-count: infinite; 
 7  animation-direction: alternate;
 8  } 
 9  .stage:active .ball { 
 10  animation-play-state: paused;  
 11 } 
 12 
```

<h4>Animation Play State Demo</h4>

Hover over the ball below to see the animation in action. Click to pause
the animation.

<h4>Animation Fill Mode</h4>

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
 1  .stage:hover .ball {  
 2  animation-name: slide;
 3  animation-duration: 2s;  
 4  animation-timing-function: ease-in-out; 
 5  animation-delay: .5s; 
 6  animation-fill-mode: forwards; 
 7  } 
 8  .stage:active .ball { 
 9  animation-play-state: paused;  
 1  } 
 0 
```

<h4>Animation Fill Mode Demo</h4>

Hover over the ball below to see the animation in action. Click to pause
the animation.

<h4>Shorthand Animations</h4>

Fortunately [animations](https://developer.mozilla.org/en-US/docs/CSS/Using_CSS_animations),
just like transitions, can be written out in a shorthand format. This is
accomplished with one animation property, rather than multiple
declarations. The order of values within the animation property should
be animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction, animation-fill-mode, and lastly animation-play-state.

```
 1  .stage:hover .ball {  
 2  animation: slide 2s ease-in-out .5s infinite alternate;  
 3  } 
 4  .stage:active .ball { 
 5  animation-play-state: paused;  
 6  } 
 7 
```

<h4>Shorthand Animations Demo</h4>

Hover over the ball below to see the animation in action. Click to pause
the animation.

<h4>Resources & Links</h4>

-[Understanding CSS3 Transitions](http://www.alistapart.com/articles/understanding-css3-transitions/) 
  via A List Apart

-[CSS Cubic-Bezier Builder](http://www.roblaplaca.com/examples/bezierBuilder/) 
  via Rob LaPlaca

-[The Guide To CSS Animation: Principles and
 Examples](http://coding.smashingmagazine.com/2011/09/14/the-guide-to-css-animation-principles-and-examples/) via
 Smashing Magazine

-[Using CSS
 Animations](https://developer.mozilla.org/en-US/docs/CSS/Using_CSS_animations) via
 Mozilla Developer Network

[<b>Lesson 7</b>] [Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/)
[<b>Lesson 9</b>] [Feature Support & Polyfills](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/)


<h2 align="center">[Lesson 9] Feature Support &amp; Polyfills</h2>

<h3>In this Lesson 9</h3>

<h4>HTML</h4>

-[HTML5
 Shiv](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#html5-shiv)

-[Cross Browser
 Testing](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#cross-browser-testing)

<h4>CSS</h4>

-[Detecting Browser
 Features](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#detecting-browser-features)

<b>JAVASCRIPT</b>

-[Conditionally Loading
 Files](https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/#conditionally-loading-files)

Building a website can be both extremely rewarding and frustrating.
Common frustrations arise from trying to get a website to look and
perform the same in every browser. All front end developers have shared
this frustration at one point or another.

Truth be told, websites <b>do not</b> need to look or perform the same in
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

<h4>HTML5 Shiv</h4>

Perhaps the most popular shiv, and one you may have likely used already,
is the HTML5 Shiv. The HTML5 Shiv was 
<a href="http://paulirish.com/2011/the-history-of-the-html5-shiv/">
created by Remy Sharp</a> to provide the ability to use HTML5 elements within 
versions of Internet Explorer 8 and below. The HTML5 Shiv not only creates 
support for HTML5 elements but also allows them to be properly styled with CSS.

The <a href="https://code.google.com/p/html5shiv/">shiv</a> should be
downloaded from Google, where Remy maintains the latest version, then
hosted on your server. For the best performance, reference the shiv
JavaScript file within the head of the document, after any stylesheet
references. Additionally, you want to reference the shiv inside of
a <a href="https://css-tricks.com/how-to-create-an-ie-only-stylesheet/">
conditional comment</a>, making sure that the file is only loaded within 
versions of Internet Explorer 8 and below.

```
In this case the conditional comment looks like <!&#45;&#45;]if lt IE
9[>...<&#0033;[endif[&#45;&#45;>.


 1  <!&#45;&#45;]if lt IE 9[>
 2  <script src="html5shiv.js"></script>
 3  <&#0033;[endif[&#45;&#45;>  
 4 
```

<h4>The Difference Between a Shiv & a Shim</h4>

Chances are you may have heard of both the HTML5 *Shiv* and
HTML5 *Shim*, and wondered what the difference, if any, may be. Oddly
enough, there is <b>no</b> difference between the HTML5 Shiv and HTML5
Shim. The two words are often used interchangeably and are commonly
transposed.

Additionally, once the new HTML5 elements are created using the shiv,
any block level elements need to be identified and updated using
the display: block; declaration.

```
 1  article,
 2  aside,
 3  details,
 4  figcaption,
 5  figure,
 6  footer,
 7  header,
 8  hgroup,
 9  nav,
 10 section,
 11 summary {
 12 display: block;
 13 }
 14 
```
Lastly, Internet Explorer 8 and 9 do not correctly define styles for a
few HTML5 inline-block level elements. As before, these styles will need
to be explicitly stated. After which, all versions of Internet Explorer
should be good to go using any new HTML5 elements.

```
 1  audio,
 2  canvas,
 3  video {
 4  display: inline-block;
 5  }
 6  
```

<h4>Detecting Browser Features</h4>

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

<h4>Loading Modernizr</h4>

To get feature detection with Modernizr up and running, visit
their [download](http://modernizr.com/download/) page and
customize what features you are looking to detect. Once downloaded,
upload the JavaScript file on your server and reference it within
the head of your HTML document, below any referenced style sheets.

It is worth noting that Modernizr may be configured to include the HTML5
Shiv, in which case the shiv doesn't need to be referenced on top of
Modernizr.

```
 1  <script src="modernizr.js"></script>
 2  
```

<h4>Conditionally Applying CSS Styles</h4>

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

```
 1  button {
 2  border: 0; 
 3  color: #fff; 
 4  cursor: pointer;
 5  font-size: 14px;
 6  font-weight: 600;  
 7  margin: 0; 
 8  outline: 0;
 9  } 
 1  /* With CSS Gradient Styles */  
 .cssgradients button {
 1  border: 1px solid #0080c2;  
 1  background: linear-gradient(#00a2f5, #0087cc);  
 border-radius: 6px;
 3  padding: 15px 30px;
 1  } 
 .cssgradients button:hover {
 5  background: linear-gradient(#1ab1ff, #009beb);  
 1  } 
 .cssgradients button:active {  
 7  box-shadow: inset 0 1px 10px rgba(255, 255, 255, .5); 
 1  } 
 /* Without CSS Gradient Styles */  
 9  .no-cssgradients button {
 2  background: transparent url("button.png") 0 0 no-repeat;  
 padding: 16px 31px;
 1  } 
 2  .no-cssgradients button:hover {
 background-position: 0 -49px;  
 3  } 
 2  .no-cssgradients button:active {  
 background-position: 0 -98px;  
 5  } 
 2 

```

<h4>Feature Detection Demo</h4>

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

<h4>Conditionally Loading Files</h4>

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

```
 1  $(document).ready(function() {
 2  if (Modernizr.localstorage) {  
 3  // Local storage is available  
 4  jQuery.getScript('storage.js'); 
 5  } else {
 6  // Local storage is not available 
 7  jQuery.getScript('storage-polyfill.js');
 8  } 
 9  });  
 1 
```

<h4>Conditionally Loading Based on Media Queries</h4>

One interesting condition Modernizr can test against is media queries.
Doing so provides the ability to only load files based on different
media query conditions. Not loading unnecessary files can be extremely
beneficial for performance.

```
 1  $(document).ready(function() {
 2  if (Modernizr.mq('screen and (min-width: 640px)')) {
 3  jQuery.getScript('tabs.js'); 
 4  } 
 5  });  
 6 
```

Above, Modernizr looks to detect screens above 640 pixels wide,
primarily desktops, and then loads the tabs.js file based off of this
condition. It is important to note that this condition is tested only
once, when the page loads, and that is it. Should a user resize the
page, this condition will not be retested. Should this condition need to
be retested, additional JavaScript would need to be included.

<h4>Conditionally Running Scripts</h4>

Using Modernizr, all of the HTML5 and CSS3 features they detect may be
tested within JavaScript. For example, it may be worth disabling
tooltips on mobile devices due to not having hover capabilities, and
instead showing the tooltip in plain text on the screen. The script for
calling these tooltips could be wrapped in a Modernizr condition,
preventing the script from loading on smaller screens.

```
 1  $(document).ready(function() {
 2  if (Modernizr.mq('screen and (max-width: 400px)')) {
 3  $('.size').text('small'); 
 4  } 
 5  });  
 6 
```

<h4>Conditionally Running Scripts Demo</h4>

Above is a basic example of how JavaScript can be executed based on a
condition established by Modernizr. Upon loading the page, if the screen
is above 800 pixels wide nothing happens. However, if the screen is
below 800 pixels wide, upon being loaded, the word 'small' will be
swapped for 'large' based off of the executed JavaScript.

<h4>HTML5 & CSS3 Polyfills</h4>

Currently there are polyfills for nearly all of the different HTML5 and
CSS3 features. The team over at Modernizr has put together quite an
exhaustive [list of polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills).
These polyfills can be dropped in as needed.

The same people behind Modernizr have also put together
a [list](http://html5please.com/) of all of the new HTML5
and CSS3 features, including instructions on how to use them
responsibly. Understand, not all of these features need polyfills. Quite
a few of them can be used outright or with the use of a fallback.

<h4>Cross Browser Testing</h4>

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

<h6><b>Fig. 9.</b> VirtualBox running on Mac OS X with Internet Explorer
versions 6 through 9.</h6>

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

<h6><b>Fig. 9</b> Internet Explorer 7 running inside of a virtual machine with the Firebug Lite
bookmarklet open for debugging.</h6>

<h4>Resources & Links</h4>

-[HTML5 Shiv](https://code.google.com/p/html5shiv/) via Remy Sharp

-[How To Create an IE-Only
 Stylesheet](https://css-tricks.com/how-to-create-an-ie-only-stylesheet/) via
 CSS-Tricks

-[Modernizr](http://modernizr.com/)

-[Loading Scripts with
 jQuery](https://davidwalsh.name/loading-scripts-jquery) via David Walsh

-[deCSS3](https://github.com/davatron5000/deCSS3) via Dave Rupert

-[HTML5 Cross Browser Polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills)

-[HTML5 Please](http://html5please.com/)

-[Microsoft IE Virtual Machines](https://github.com/xdissent/ievms) via Greg Thornton

<b>[Lesson 8]</b> [Transitions &
Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/)
<b>[Lesson 10]</b> [Extending Semantics &
Accessibility](https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/)

<h2>[Lesson 10] Extending Semantics & Accessibility</h2>

<h3>In this Lesson 10</h3>

<h5>HTML</h5>

<ul>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#semantic-motivation">
    Semantic Motivation</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#structural-semantics">
    Structural Semantics</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#text-level-semantics">
    Text Level Semantics</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#microdata">
    Microdata</a></li>
  <li><a href="https://learn.shayhowe.com/advanced-html-css/semantics-accessibility/#wai-aria">
    WAI-ARIA</a></li>
</ul>

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

<h4>Semantic Motivation</h4>

Occasionally, one may ask if semantics really make a difference. You may
hear they slow down development, are poorly supported, or that they are
even opinionated. While this may have some validity, you still need to
retain integrity and continue to write the best code possible, for
semantics provide a larger meaning in writing code.

The fact of the matter is, 
<a href="http://www.vanseodesign.com/web-design/semantic-html/">semantics largely 
benefit everyone</a>. For starters, semantics provide a shared and unambiguous 
meaning to content. Semantics give content solid structure and value, while also
favoring accessibility, providing better user interfaces and more defined 
information to assistive technologies. Search and globalization is more 
permanent with semantics, making it easier to serve content internationally 
and making it more search engine friendly. Should that not be enough, semantics 
also promote interoperability, allowing the exchange and use of information 
across different platforms and devices.

It's safe to say semantics are important, and here to stay. To briefly
recap, semantics provide:

-Unambiguous, shared meaning within content

-Accessibility

-Search and globalization

-Interoperability

<h4>Structural Semantics</h4>

Within the beginner's guide we discuss the use of 
<a href="https://learn.shayhowe.com/html-css/getting-to-know-html/">
structural semantics</a>, specifically using the header, nav, article, section, 
aside, and footer elements. These elements are used to provide additional
background context to the content within them, communicating their core
meaning to web browsers and other devices. This is important, as it
provides a better way to outline and structure pages, not to mention a
more meaningful solution than divisions.

<h4>Hiding Content</h4>

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

```
 1  <!&#45;&#45; Good &#45;&#45;>  
 2  <div hidden>...</div>  
 3  <!&#45;&#45; Not good &#45;&#45;> 
 4  <div style="display: none;">...</div> 
 5 
```

Imagine a blind user attempting to fill out a form and the first piece
of content, before even filling out the form, is a success message. This
is a poor user experience, and one that can easily be fixed using proper
semantics.

<h4>Text Level Semantics</h4>

The majority of content on the web lives within text, and we primarily
browse the Internet looking for this content. Using the
proper <a href="https://developers.whatwg.org/text-level-semantics.html">
semantic markup</a> for text makes it easier for users to find what they need.

<h4>Bolding Text</h4>

There are a few different ways to make text bold, including multiple
elements and the <a href="https://learn.shayhowe.com/html-css/working-with-typography/">
font weight</a> CSS property. The two main elements used in this case include strong 
and b. While these two elements have the same presentation they have completely
different semantic meanings.

The strong element outlines text that has a <b>strong importance</b>. On
the contrasting side, the b element identifies text that is to
be <b>stylistically offset</b>, without importance. Generally speaking,
the b element should be used solely as a styling hook to change the
presentation of an element, where the strong element should be used to
identify significantly important text.

```
 1  <!&#45;&#45; Strong importance &#45;&#45;>
 2  <strong>Caution:</strong> Falling rocks.
 3  <!&#45;&#45; Stylistically offset &#45;&#45;>
 4  This recipe calls for <b>bacon</b> and <b>baconnaise</b>.
 5  
 6  
```

<h4>Bolding Text Demo</h4>

<h4>Italicizing Text</h4>

Italicizing text falls in line with that of bolding text, where we can
use multiple elements or the [font
style](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
property to achieve a desired presentation. When italicizing text, the
two elements most commonly used are em and i. Again, these share the
same presentation, yet have completely different semantic meanings.

The em element places a <b>stressed emphasis</b> on text, while
the i element identifies text to be expressed in an <b>alternate voice or
tone</b>. Using the em element really drives prominence with an added
importance. On the other hand, the i element is primarily used within
dialog or prose, offsetting text without any added emphasis or
importance.

```
 1  <!&#45;&#45; Stressed emphasis &#45;&#45;> 
 2  I <em>love</em> Chicago!
 3  <!&#45;&#45; Alternative voice or tone &#45;&#45;>  
 4  The name <i>Shay</i> means a gift.  
 5 
 6 
```

<h4>Italicizing Text Demo</h4>

<h4>Using i for Icons</h4>

Recently there has been a small movement of front end programmers using
the i element for including icons on a page, specifically as seen
within [Bootstrap](https://getbootstrap.com/).
The i element is used as a hook, to which a class then determines which
icon background image to apply to the element. Depending on how closely
you wish to follow semantics this may or may not be an acceptable
practices.

<h4>Underlining Text</h4>

Continuing the pattern of having multiple elements with the same
presentation, underlining text is no different. There are a couple of
different elements we can use as well as the [text
decoration](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
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

```
 1  <!&#45;&#45; Added to the document &#45;&#45;>
 2  <ins cite="http://learn.shayhowe.com" datetime="2012-07-01">
 3  Updated: This website now contains an advanced guide. 
 4  </ins>
 5  <!&#45;&#45; Unarticulated annotation &#45;&#45;>
 6  <u>Urushihara Yuuji</u> won <u>Sasuke 27</u>. 
 7 
```

<h4>Underlining Text Demo</h4>

<h4>Striking Text</h4>

Striking text follows the same pattern as before where different
elements may be used, as may the [text
decoration](https://learn.shayhowe.com/html-css/working-with-typography/) CSS
property. The two properties most commonly used include del and s.

The del element is used to identify text <b>deleted or removed from the
document</b>. As with the ins element, it may be used with
the cite and datetime attributes. Each of which hold the identical
semantic values as before, cite specifying a resource that explains the
change and datetime identifying when the content was removed from the
document.

The s element identifies text that is no longer accurate or relevant.

```
 1  <!&#45;&#45; Deleted from the document &#45;&#45;>  
 2  I am an avid cyclist, <del cite="http://shayhowe.com" 
 3  datetime="2012-07-01">
 4  skateboarder</del> and designer.
 5  <!&#45;&#45; No longer accurate or relevant &#45;&#45;>  
 6  <s>$24.99</s> $19.99  
 7 
```

<h4>Striking Text Demo</h4>

<h4>Highlighting Text</h4>

To highlight text for reference purposes the mark element should be
used. Added in HTML5, the mark element provides a clean, semantic way to
identify text, specifically for reference purposes without having to use
an un-semantic text level element.

```
 1  <!&#45;&#45; Highlighted for reference purposes &#45;&#45;> 
 2  Search results for <mark>'chicago'</mark>.
 3 
```

<h4>Highlighting Text Demo</h4>

<h4>Abbreviations</h4>

Abbreviations, the shortened form of a phrase, can be semantically
marked up in HTML using the abbr element. The abbr element should be
used along with the title attribute, of which includes the full value of
the phrase being abbreviated. The acronym element was originally used to
distinguish acronyms from abbreviations but has since been deprecated,
and shouldn't be used.

```
 1  <abbr title="HyperText Markup Language">HTML</abbr>
 2  <abbr title="Cascading Style Sheets">CSS</abbr> 
 3 
```

<h4>Abbreviations Demo</h4>

<h4>Sub & Superscripts</h4>

Subscripts and superscripts may be marked up accordingly using
the sub and sup elements respectively. It is important to note that
these elements should be reserved for typographical conventions, not for
presentational purposes.

```
 1  <!&#45;&#45; Subscript &#45;&#45;>
 2  H<sub>2</sub>O 
 3  <!&#45;&#45; Superscripts &#45;&#45;>
 4  1<sup>st</sup> Place 
 5 
 6 
```

<h4>Sub & Superscripts Demo</h4>

<h4>Meter & Progress</h4>

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

```
 1  <!&#45;&#45; Meter &#45;&#45;> 
 2  <meter value="7" max="10">7 stars</meter>  
 3  <meter value="47" min="0" max="105" low="5" high="65"  optimum="45">The car  
 4  is moving at a decent average mile per hour.</meter>
 5  <!&#45;&#45; Progress &#45;&#45;> 
 6  You are <progress value="50" max="100">50%</progress>  
 7  complete.  
 8  <progress value="50" min="0" max="100">Hold tight, you"re getting there.</progress>
 9 
```

<h4>Meter & Progress Demo</h4>

<h4>Time & Address</h4>

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

```
 1  <!&#45;&#45; Time &#45;&#45;>  
 2  <time>2011-08-24</time> 
 3  <time datetime="2011-08-24" pubdate>August 24th, 2011</time>
 4  <time datetime="15:00">3pm</time> 
 5  <time datetime="2011-08-24T15:00">August 24th, 2011 at 3pm</time> 
 6  <!-- Address -->
 7  <address> <strong>Shay Howe</strong><br>
 8    <a href="http://learn.shayhowe.com">http://learn.shayhowe.com</a><br> 
 9    <a href="mailto:hello@awesome.com">hello@awesome.com</a><br> 
 10    600 W. Chicago Ave.<br>
 11   Suite 620<br> 
 12   Chicago, IL 60654<br> USA  
 13 </address> 
 14 
```

<h4>Time & Address Demo</h4>

<h4>Presenting Code</h4>

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

```
 1  <!&#45;&#45; Inline code samples &#45;&#45;>  
 2  Use the <code>article</code> element. 
 3  <!&#45;&#45; Larger, block level code snippets &#45;&#45;>  
 4  <pre><code>body { 
 5  color: #666; 
 6  font: 14px/20px Arial, sans-serif;
 7  }</code></pre> 
 8 
```

<h4>Presenting Code Demo</h4>

<h4>Line & Word Breaks</h4>

Occasionally you may want to include a line break within a line of text,
in which case the br element may be used. The br element does not have a
closing tag, simply a beginning. In XHTML the br element is self
closing, including a trailing forward slash, <br />.

Line breaks are not to be used for thematic grouping of content.
Paragraphs or other elements are better suited for thematic grouping.
Line breaks are specifically to be used where line breaks exist as part
of the content, for example as within addresses and poems.

In addition to line breaks, you may also specify word breaking
opportunities with the wbr element. Using the wbr element in the middle
of a word ensures that, should the word need to wrap two lines, it does
in a legible fashion.

```
 1  <!&#45;&#45; Line break &#45;&#45;>  
 2  600 W. Chicago Ave.<br>
 3  Chicago, IL 60654<br>  
 4  USA  
 5  <!&#45;&#45; Word break &#45;&#45;>  
 6  http://shay<wbr>howe.com  
 7 
 8 
```

<h4>Line & Word Breaks Demo</h4>

<h4>Side Comments</h4>

Originally the small element was used to render text as one font size
smaller than the default, purely for presentational purposes. As we are
aware, presentation and style should only live within CSS, not HTML.
Within HTML5, the small element preserves the presentation of being
displayed at a smaller font size, however it semantically means to be
rendered as a side comments or small print. This often includes
copyright information or legal print.

```
 1  <!&#45;&#45; Side comments or small print &#45;&#45;> 
 2  <small>&copy; 2012 Shay Howe</small>
 3 
```

<h4>Side Comments Demo</h4>

<h4>Citations & Quotes</h4>

The beginner's guide discusses [citations and
quotes](https://learn.shayhowe.com/html-css/working-with-typography/),
and when to use the cite, q, and blockquote elements accordingly. As a
quick reminder, the cite element refers to a title of work,
the q element identifies dialog or prose, and the blockquote element is
used to code longer formed quotes, commonly from external sources.

<h4>Hyperlink Attributes</h4>

The beginner's guide also
outlines [hyperlinks](https://learn.shayhowe.com/html-css/getting-to-know-html/),
and some of their different behaviors. What is not covered, however, is
some of the semantic benefits to hyperlinks, specifically with the use
of the download and rel attributes.

<h4>Download Attribute</h4>

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

```
 1  <!&#45;&#45; Boolean &#45;&#45;>  
 2  <a href="twitter-logo.png" download>Twitter Logo</a>  
 3  <!&#45;&#45; With a value &#45;&#45;>
 4  <a href="twitter-logo.png" download="Logo">Twitter Logo</a>  
 5 
 6 
```

<h4>Download Attribute Demo</h4>

<h4>Relationship Attribute</h4>

For any hyperlinks including a reference attribute, href, you may also
include the relationship attribute, rel. The rel attribute identifies
the relationship between the current document and the document being
referenced. For example, when linking to a copyright statement
the rel attribute value of copyright should be used.

```
 1  <a href="legal.html" rel="copyright">Terms of Use</a>  
 2  <a href="toc.html" rel="contents">Table of Contents</a>
 3 
```

A few [popular](http://microformats.org/wiki/existing-rel-values) rel attribute
values include:

-alternate

-author

-bookmark

-help

-license

-next

-nofollow

-noreferrer

-prefetch

-prev

-search

-tag

<h4>Microdata</h4>

<a href="http://www.w3.org/TR/microdata/">Microdata</a> is HTML
extended with nested groups of name-value pairs that allow machines,
including browsers and search engines, to pick up additional semantics
and information for rich content. Adding microdata to your website is
accomplished by using predetermined attributes and values. These
attributes and values will then be interpreted, and extended, as
intended. Currently, the more popular uses of microdata reside within
coding contact information and calendar events, however there are 
<a href="http://schema.org/docs/schemas.html">encoding models</a> for products,
reviews, and more.

One example of microdata at work is within Google, where microdata is
interpreted and used within search results to display more relevant
data. Often performing a search for a business location yields the
address and sub sequential contact information within the results.
Chances are this information is being pulled from microdata written on
an existing website.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 16. google microdata (181) ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center" width="100%">
  <img src="./images/image016.jpeg"
   style="width:40%"
   alt="Google Microdata." />
</p>

<h6 align="center">Fig. 10</h6>

Google uses microdata to identify business locations, contact
information, hours, pricing, ratings, and more.

<h4>Microdata vs. Microformats vs. RDFa</h4>

There are actually a handful of rich, structured data standards,
including [microdata](http://www.w3.org/TR/microdata/), [microformats](http://microformats.org/wiki/Main_Page),
and [RDFa](http://www.w3.org/TR/xhtml-rdfa-primer/). All
of these have their pros and cons, and all of which are still viable to
practice.

Microdata is the recommended format
from [Google](https://support.google.com/webmasters/bin/answer.py?hl=en&answer=99170),
and other search engines, as well as part of the HTML5 specification. It
uses findings from both microformats and RDFa to base it's design
around, thus looking to be a solid choice, and the one covered here. It
is, however, recommended you do your research, take the pulse of the
community, find what works best for your situation, and use that. Using
one of these standards is substantially better than not using any. Find
what will provide the best benefit for your users.

<h4>Outlining Microdata</h4>

Microdata is identified using three main
attributes, itemscope, itemtype, and itemprop.

The itemscope Boolean attribute declares the scope of each microdata
item. Place this attribute on the parent element where all of the
microdata information pertaining to this item should reside.

Once you have determined the scope, use the itemtype attribute to
identify what microdata vocabulary should be used. Generally speaking,
some of the more popular microdata item types have been outlined
at [Schema.org](http://schema.org/docs/schemas.html).
There are, however, other websites which outline additional, and
different, item types. You may also write your own item types should you
find the need.

```
 1  <section itemscope itemtype="http://schema.org/Person"> 
 2  ... 
 3  </section> 
 4 
```

Once the scope and type of the item have been determined, properties may
then be set. These properties are identified by different elements which
include the itemprop attribute. The value of this attribute determines
what property is being referenced, and the content within the element
itself most commonly determines the value of the property.

```
 1  <section itemscope itemtype="http://schema.org/Person"> 
 2  <h1 itemprop="name">Shay Howe</h1>
 3  </section> 
 4 
```

Some elements, however, do not get their itemprop value from the content
within the element. Instead, their value is determined from the value of
another attribute on the element. The table below outlines these one-off
elements and what attribute is used for their property value.

  | <b>Element</b>                                       | <b>Value</b>       |
  |------------------------------------------------------|--------------------|
  | &lt;meta&gt;                                               | content attribute  |
  | &lt;audio&gt;, &lt;embed&gt;, &lt;iframe&gt;, &lt;img&gt;, &lt;source&gt;, &lt;video&gt; | src attribute      |
  | &lt;a&gt;, &lt;area&gt;, &lt;link&gt;                                  | href attribute     |
  | &lt;object&gt;                                             | data attribute     |
  | &lt;time&gt;                                               | datetime attribute |

<h4>Person Microdata</h4>

When referring to a person
the [person](http://schema.org/Person) microdata library
should be used. Below is an example of what a person microdata item
might look like. Please notice, the person item type is used, as is the
postal address item type within it. Also, please notice the different
item properties and their corresponding values.

```
 1  <section itemscope itemtype="http://schema.org/Person"> 
 2    <strong itemprop="name">Shay Howe</strong>
 3    <img src="shay.jpg" itemprop="image" alt="Shay Howe">  
 4    <div itemprop="jobTitle">Designer and Front-end Developer</div>  
 5    <a href="http://www.shayhowe.com" itemprop="url">shayhowe.com</a> 
 6    <div itemprop="telephone">(555) 123-4567</div>  
 7    <a href="mailto:shay@awesome.com" itemprop="email">shay@awesome.com</a>
 8    <address itemprop="address" itemscope itemtype="http://schema.org/PostalAddress">  
 9      <span itemprop="streetAddress">600 W. Chicago Ave.</span>
 10     <span itemprop="addressLocality">Chicago</span>,
 11     <abbr itemprop="addressRegion" title="Illinois">IL</abbr> 
 12     <span itemprop="postalCode">60654</span>  
 13   </address> 
 14 </section> 
 15 
```

<h4>Person Microdata Demo</h4>

Please keep in mind, this code is for an individual person. Should you
wish to refer to an organization, a more
specific [organization](http://schema.org/Organization) microdata
library should be followed.

<h4>Event Microdata</h4>

The event microdata is very similar to that of the person microdata,
however it uses
the [event](http://schema.org/Event) microdata library
instead. Common property similarities between the two can be identified,
as can some of the nested item types.

```
 1  <section itemscope itemtype="http://schema.org/Event">  
 2    <a itemprop="url" href="#"> 
 3      <span itemprop="name">Styles Conference</span>  
 4    </a>  
 5    <time itemprop="startDate" datetime="2014-08-2409:00">Sunday, August 24, 
 6      2014 at 9:00 a.m.</time>  
 7    <div itemprop="location" itemscope itemtype="http://schema.org/Place">  
 8      <a itemprop="url" href="http://www.thechicagotheatre.com/">Chicago Theatre</a> 
 9      <address itemprop="address" itemscope itemtype="http://schema.org/PostalAddress">  
 10       <div itemprop="streetAddress">175 N. State St.</div>  
 11       <span itemprop="addressLocality">Chicago</span>,
 12       <abbr itemprop="addressRegion" title="Illinois">IL</abbr> 
 13       <span itemprop="postalCode">60601</span>  
 14     </address> 
 15   </div>
 16 </section> 
 17 
```

<h4>Event Microdata Demo</h4>

Microdata provides a lot of ways to further extend the content of a
page. We have only touched the surface here. Further information on
microdata may be found at <a href="http://diveintohtml5.info/extensibility.html">
Dive Into HTML5 Microdata</a> and <a href="https://developers.whatwg.org/links.html#microdata">
WHATWG Microdata</a>.

<h4>WAI-ARIA</h4>

<a href="http://www.w3.org/WAI/intro/aria">WAI-ARIA</a>, also know as
Web Accessibility Initiative --- Accessible Rich Internet Applications,
is a specification that helps make web pages and applications more
accessible to those with disabilities. Specifically, WAI-ARIA helps
define roles (for what blocks of content do), states (for how blocks of
content are configured), and additional properties to support assistive
technologies.

<h4>Roles</h4>

Setting <a href="https://www.w3.org/TR/wai-aria/#roles">WAI-ARIA roles</a> is
accomplished using the role attribute. These roles then specify what
certain elements and blocks of content do on a page.

```
 1  <header role="banner">...</header> 
 2 
```

WAI-ARIA roles break down into four different categories, including
abstract, widget, document structure, and landmark roles. For this
lesson we will focus primarily on the document structure and landmark
roles. <b>Document structure roles</b> define the organizational structure
of content on a page, while <b>landmark roles</b> define the regions of a
page. Specific role values for each of these categories are broken out
below.

<h4>Document Structure Roles</h4>

-article

-columnheader

-definition

-directory

-document

-group

-heading

-img

-list

-listitem

-math

-note

-presentation

-region

-row

-rowheader

-separator

-toolbar

<h4>Landmark Roles</h4>

-application

-banner

-complementary

-contentinfo

-form

-main

-navigation

-search

HTML5 introduced a handful of new structural elements which commonly
match up against the document structure and landmark roles. Exactly how
these roles match up against specific elements may be seen below. Please
notice, the header and footer elements do not have an implied role, and
the acceptable roles for these elements may only be used <b>once</b> per
page. That said, if you have multiple header and footer elements on a
page the banner and contentinfo roles should be applied on the elements
directly tied to the document from a top level perspective, not elements
nested within other regions of the document structure.


| Element | Implied Role  | Acceptable Roles                        |
|---------|---------------|-----------------------------------------|
| article | article	      | application, article, document, or main |
| aside   | complementary | complementary, note, or search          |
| footer  | —             | contentinfo (Only once per page)        |
| header  | —             | banner (Only once per page)             |
| nav     | navigation    | navigation                              |
| section | region        | alert, alertdialog, application, contentinfo, dialog, document, log, |
|         |               | main, marquee, region, search, or status.                            |

Combining the elements with their matched roles in HTML5 would look like
the following code snippet.

```
 1  <header role="banner">  
 2    <nav role="navigation">...</nav> 
 3  </header>
 4  <article role="article">
 5    <section role="region">...</section>  
 6  </article> 
 7  <aside role="complementary">...</aside>  
 8  <footer role="contentinfo">...</footer>  
 9 
```

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

  <h3>Resources &amp; Links</h3>

  <ul>
 <li><a href="https://developers.whatwg.org/text-level-semantics.html" 
   rel="noopener noreferrer" target="_blank">
   Text-Level Semantics</a> via WHATWG</li>
 <li><a href="http://microformats.org/wiki/existing-rel-values" 
   rel="noopener noreferrer" target="_blank">
   Existing rel Values</a> via Microformats.org</li>
 <li><a href="http://schema.org/docs/schemas.html" 
   rel="noopener noreferrer" target="_blank">
   Organization of Schemas</a> via Schema.org</li>
 <li><a href="http://diveintohtml5.info/extensibility.html" 
   rel="noopener noreferrer" target="_blank">
   Microdata</a> via Dive Into HTML5</li>
 <li><a href="http://www.w3.org/WAI/intro/aria" 
   rel="noopener noreferrer" target="_blank">
   WAI-ARIA Overview</a>) via W3.org</li>
 <li><a href="https://www.w3.org/TR/wai-aria/#roles" 
   rel="noopener noreferrer" target="_blank">
   The Roles Model</a> via W3.org</li>
</ul>

</details>

[<b>Lesson 9</b>] <a href="https://learn.shayhowe.com/advanced-html-css/feature-support-polyfills/" 
  rel="noopener noreferrer" target="_blank">Feature Support &amp; Polyfills</a>

...the end.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~ 0x/0x.  (xx) ~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--
<p align="center" width="100%">
  <img src="./images/image00x.png"
 style="width:40%"
 alt="." />
  <img src="./images/image00x.png"
 style="width:40%"
 alt="." />
</p>
-->
