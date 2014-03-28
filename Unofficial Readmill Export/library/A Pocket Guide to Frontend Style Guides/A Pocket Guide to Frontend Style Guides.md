**A Pocket Guide to Front-end Style Guides** by *Anna Debenham*

Further reading “Front-end Style Guides”, my article on 24 Ways Examples of front-end style guides in the wild, a collection of links on Gimme Bar “CSS Style Guides”, a roundup from Chris Coyier on CSS-Tricks “Responsive Deliverables” by Dave Rupert “Modularity and Style Guides” by David Bushell “Firefox branding”, part of the Mozilla style guide “Writing an Interface Style Guide” by Jina Bolton on A List Apart “Behind the Design: The New Viget”, by Tom Osborne “Easing the Path from Design to Development” by Drew McLellan on 24 ways

---

Stylify Me Stylify Me is an online style guide generator. Simply add your page URL and it will spit out the main colours and typefaces used. This is perfect when you need to kick-start a style guide for an existing site. It includes image dimensions, swatches, typefaces and a screenshot of the page. It is quite basic, however, and it’s on a per-page basis, but it’s a good starting point. Typecast Typecast gives you some text to style – headings, paragraphs, lists – and you can just click on an element to change the style. An adjustable baseline grid is included. This makes a great entry point for building a site from the content out, because you can easily paste in your own content and choose from thousands of different fonts. It also outputs a style sheet, generates a style guide, or you can download a PDF. It’s built specifically for the web, so measurements are in pixels and ems. Frontify Frontify allows you to upload screenshots of your design, and pick the main colours to turn into swatches. You can take screenshots of modules and upload the markup for them. However, it doesn’t generate the module itself from the markup

---

Some clients will immediately get it, others won’t. For those that don’t, Clearleft found it helps to make element collages that they’ve created look less like a webpage by changing the format slightly. “[Jon Aizlewood] soon realised that by presenting these elements together vertically, some stakeholders mistook the output for a web page. He is now using a long, wide horizontal canvas to mitigate against this. He’s also scaling up certain elements, so that the discussion revolves around the overall visual aesthetic, rather than the pixel precision and font sizing of certain components.” — Paul Lloyd, “Visual Design Explorations”, (8 March 2013)

---

On a news site, how will the homepage look during the biggest breaking news story of the year? For an airline site, how would you have informed people about all planes being grounded

---

Design for the unexpected, design for the extremes Very long headings or double-barrelled names can cause unexpected problems, so the content examples you use in your modules should demonstrate text that responds well when it flows onto multiple lines or is bigger than its container. Use the style guide as a way to show these extremes, and prove that you’ve tested and know how to appropriately deal with these situations.

---

Like an identity style guide, you can include guidance on how to apply the branding along with downloadable assets. It’s vital to consider your audience for the style guide and make sure it’s not overwhelming for a non-designer who might just want to do something very simple.

---

Colour swatches I like to add colour swatches to display the colours used on a site and, if I’m using Sass, the variable names I’m using for them.

---

It may help to have a version number on the document, especially if several people are working on it. If you’re using version control, you could pull the last commit ID onto the page. It’s also handy to indicate the last modified date so you can check how up-to-date the style guide is.

---

works like this. The version available on Github includes a PHP script that scans a folder and outputs all the modules in there along with their markup.

---

Paul Lloyd’s Barebones

---

Paul Lloyd’s Barebones

---

Go nuts here; add headings with links, headings in lists, and maybe even throw in some elements you probably don’t need to use very often, like kbd and pre.

---

There are plenty of primers and boilerplates out there to help you to get going. My favourite one to start with is Paul Lloyd’s Barebones, and

---

You might already have the foundation of a front-end style guide in the form of a reset style sheet. Create a basic HTML page with all the relevant text elements on it and you can check that your basic typography looks good. If you don’t use one, a great place to start is Typecast. Here you can style text, change the typeface, adjust the font size, and see how it looks in the browser. You can style specific elements like lists, and you can output it all as CSS.

---

In a talk she gave about working with real estate business Trulia, Nicole Sullivan highlighted the importance of building a living style guide to improve the performance of front-end code. By auditing all the components on the site, she was able to spot style duplications in the CSS and design inconsistencies (these are quite common when sites grow organically). After refactoring the code, she had reduced the HTML by 48%, removed 135Kb of unused CSS, and made load time 21% faster.

---

 Brad’s responsive pattern lab is an example of this system. It can toggle the width of the container so you can quickly see what templates look like at different viewport sizes, and you can manually edit the viewport width in ems.

---

“That’s the way I’ve been starting most of my projects lately: beginning with the atomic units of content and styling them first before even thinking about layout. This ensures that those styles are extremely robust—because they don’t depend on any particular context, they can be safely dropped into any part of a page.”

---

Jeremy Keith creates a pattern primer as part of the process of building a responsive site.

---

There is even a Compass extension that lets you do this, and a marked up equivalent if you want to produce a web-based style tile.

---

Style guides set a precedent, demonstrating how the designer or developer expects something to be done in future.

---

