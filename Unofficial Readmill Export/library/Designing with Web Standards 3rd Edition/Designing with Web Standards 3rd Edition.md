**Designing with Web Standards (3rd Edition)** by *Jeffrey Zeldman, Ethan Marcotte*

Myth: A Text-Only Version Satisfies the Requirement for Equal or Equivalent Access

Not true. Adaptive technology has come a long way, and almost anything on a conventional web page can be made fully or at least partially accessible, with no visible alteration to your layout. (Remember: the work takes place under the hood.) Shuttling disabled visitors off to a text-only site assumes that the color blind can’t see at all, or that those who have limited mobility have no use for images. It also assumes that these users have no interest in shopping on your commerce site or participating in an online discussion forum. In short, the outdated text-only approach helps no one. Not only that, creating and maintaining text-only pages costs far more (and is far less reliable) than simply adding assistive tags and attributes to your site.

---

If you attain WCAG 1.0 or WCAG 2.0 Priority 2 accessibility, you will also automatically achieve Section 508 compliance. Of course, if you prefer to work directly to the Section 508 guidelines, you certainly can. Like we said at the top, pick a standard, and begin applying it.

---

The 62.5% Solution

In 2004, developer Richard Rutter gave the world a 62.5% solution to the problem of the complex math inherent in em-based design (www.clagnut.com/blog/348). 62.5% of the 16px default size is 10px. Set the body to 62.5% and the rest of the math is easy (because it’s based on 10):

body { font-size: 62.5%; }
p { font-size: 1.2em; line-height: 1.5; }
h1 { font-size: 2.4em; }
In the example above, p text is 12px tall (1.2 x 10px), its line-height is 15px (1.5 x 10px), and h1 headline text is 24px (2.5 x 10px). Easy-peasy!

Using Rutter’s method, you can attain near-pixel-perfect control without running afoul of IE’s unwillingness to scale pixels. Web designers were quick to seize on Rutter’s brilliant idea, and it has become a best practice.

---

The fourth value, however, is the interesting bit, allowing the user to set the color’s alpha channel, specifying the transparency of the color. This value can range from 0.0 (completely transparent) to 1.0, which is fully opaque. Miner has used this fourth value to subtle yet stunning effect, setting his site’s font color to rgb(30, 40, 30) (again, that’s #1E281E for you hex-heads), but screened at 90% transparency (0.9). As a result, his text will automatically maintain its pleasing contrast if he ever changes his body’s background

---

As this book goes to press, Firefox only supports the Ogg codec (www.xiph.org/downloads). No matter! You can find Ogg music files for Firefox via www.vorbis.com/music_links.

---

