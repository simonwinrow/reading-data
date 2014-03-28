**The Smashing Book #4: New Perspectives on Web Design** by *Smashing Magazine & Various Authors*

FPS Counter An older but equally useful tool for visualizing frame rate and jank is the real-time frames-per-second counter. This can be enabled in DevTools by going to the Settings menu and checking “Show FPS meter.” When activated, you will see a dark box in the top-right corner of your page with frame statistics. The counter can be used during live editing to diagnose what in your page is causing a drop-off in frame rate without having to switch back and forth with the Timeline view.

---

Animation We’ve talked about requestAnimationFrame, but did you know that even more efficient than lighter JavaScript animation in your callbacks is no JavaScript at all? There’s no perfect solution for avoiding interruptions in requestAnimationFrame callbacks, but you can get some mileage using CSS animations to remove the need for them. In browsers like Opera Mobile and Chrome for Android, CSS animations can be run by the browser while JavaScript is running thanks to multi-threading.

---

. There is natural downtime in the interaction with our apps. For example, people will spend some time entering data into forms. So why not use that time to load additional resources? A focus handler on the first text field could trigger a nice-to-have resources download. If the user never enters the form, nothing needs to happen.

---

Opening the Chrome developer tools revealed two things: first, the HTML of the button was the following: <a class="button eula-download-button" href="javascript:void(0)" data-g-label="download chrome" data-g-event="cta"> … </a> Second, the error console greeted you with “TypeError: chrm.download is undefined.” What happened? Well, something in the JavaScript went wrong and took the button with it. javascript:void(0) is not a valid URL and has no business being in an href attribute. It is a blinking warning sign that somewhere in the development process Google threw in the towel and created everything in JavaScript. On investigation, I found out that the purpose of the code is to show an end user license agreement before download (as hinted in the class name), and the JavaScript automatically detects the operating system to provide the appropriate install package for Chrome. Both very good uses for this page, but the way they were implemented meant Google lost half a day of Chrome downloads. The remedy is straightforward: instead of pointing the link to a small inline JavaScript that does nothing at all, it should point to a download page that lists all the downloadable versions of Chrome. This could be a great resource in any case, as sometimes I might want to download a version not for my OS (for example, if I am on a fast connection somewhere). You can still add an event handler to the link to do all the other necessary things done in the JavaScript that was never called.

---

if (window.addEventListener && document.querySelector) { var v = document.querySelector('video'), sources = v.querySelectorAll('source'), lastsource = sources[sources.length-1]; lastsource.addEventListener('error', function(ev) { var d = document.createElement('div'); d.innerHTML = v.innerHTML; v.parentNode.replaceChild(d, v); }, false); } What’s going on here? When a browser fails to play a video, it fires an error handler on the last source element in the video element. So, we test that the browser understands addEventListener() and querySelector() (which is the standard way of jQuery’s $(), really) and then get the last source element in the video element. If there is an error event being fired, we create a div element and replace the video with that one.

---

. Animations and transitions in CSS are hardware-accelerated; JavaScript animations are not. So are transformations in CSS, which means that a transform: translate(x,y) beats a position:absolute; top: x; left: y; when it comes to performance.

---

A requestAnimationFrame() lets you change things and only display them when the result can end up onscreen. Furthermore, when the browser tab your script runs in is inactive (when the user is in another tab or window), the animation doesn’t run, thereby not wasting computation time and shortening battery life. In contrast, a setTimeout() hopes that the browser is ready to draw and runs whether the user is viewing your animation or not.

---

. Only then should we add layers and layers of awesomeness for those browsers which can deal with them. For example, take the wonderful and standardized addEventListener(). OldIE doesn’t understand that, so we wrote a filler to overwrite attachEvent(). Bad plan. This is software ballast we’ll carry with us for years to come and it caters to a tiny subgroup of users that will get smaller and smaller. Why not just wrap all of our JavaScript in if (window.addEventListener) {} and never pester OldIE with the demanding JavaScript we write these days?

---

Forms have come a long way, too. A simple required attribute on an input element means the user cannot submit the form until that data has been entered. Adding a pattern attribute allows you to define a rule in the form of a regular expression.

---

All switch statement cases must end with break, throw, return, or a comment indicating a fall-through. Judging by this guideline, there is definitely a stylistic error and that means there could be a logic error. If the first case was supposed to fall through to the second case, then it should look like this: switch(value) { case 1: doSomething(); // falls through case 2: doSomethingElse(); break; default: doDefaultThing(); } If the first case wasn’t supposed to fall through, then it should end with a statement such as break. In either case, the original code doesn’t match the style guide and that means you need to double-check the intended functionality. In doing so, you might very well find a bug.

---

For example, consider the JavaScript switch statement. It’s a very common error to mistakenly allow one case to fall through into another, such as this: switch(value) { case 1: doSomething(); case 2: doSomethingElse(); break; default: doDefaultThing(); } The first case falls through into the second case so if value is 1, then both doSomething() and doSomethingElse() are executed. And here’s the question: is there an error here? It’s possible that the developer forgot to include a break in the first case, but it’s also equally possible that the developer intended for the first case to fall through to the second case. There’s no way to tell just from looking at the code. Now suppose you have a JavaScript style guide that says something like this:

---

The reason it was so fast was simple: automation. You can automate find and replace but you cannot automate CSS refactoring. My process was simple. I just ran: $ git grep "$CLASS_I_WANTED_TO_FIND" This gave me a list of all the files containing that class in my project. I then opened all these files in my text editor and ran a global find and replace. Easy.

---

Finally, you should never combine the two. If a class does a specific job, it should have an equally explicit name (e.g. .user-profile_name rather than .name). Takeaway: Make sure the names you use for selectors are appropriate, and that they expose as much information as they can. Do not worry about being long-winded with classes (I recently wrote a class of .accordion__trigger--closed), and name them so that other developers will find them practical and sensible to work with.

---

To quote Google developer, Jens O. Meiert: “Use names that are as short as possible but as long as necessary”16.

---

: Class names should communicate useful information to developers. […] Tying your class name semantics tightly to the nature of the content has already reduced the ability of your architecture to scale or be easily put to use by other developers.

---

. What is useful is knowing a class isn’t tied to a particular type of content, and that it is abstracted enough to be reused elsewhere. Nicole Sullivan’s media object14 is a perfect example of this way of thinking. Class names that don’t allude at all to the type of content are highly reusable.

---

Takeaway: Keep your selectors as short as possible, keep their specificity low at all costs, keep them as combinable as possible, keep them on the SRP and make sure they have sound selector intent. 

---

The pursuit of clean markup and semantic classes and all that came with it was well-intentioned but helped no one. It led to verbose, difficult to maintain, tangled style sheets. The price of omitting a few classes was having to write giant, convoluted selectors to target these orphaned, unnamed DOM elements. As the saying goes, we robbed Peter to pay Paul. We were writing clean markup at the cost of writing verbose, messy and convoluted CSS. We just moved the mess somewhere else.

---

As Nicole Sullivan once said, “Our (CSS) best practices are killing us7”; our desire to write markup that doesn’t use any classes serves no one, and often causes ourselves problems.

---

Sensibleness is about ease of maintenance, longevity and how much sense something makes to a human being, because humans are the only things to take any amount of meaning from class names.

---

Semantics is not about how we name our classes or IDs; the only things to gather meaning from classes and IDs are humans. Anything else that reads or accesses a class or an ID merely matches it;it does not derive any meaning from them at all. This, straight from the HTML(5) spec: Particular meanings should not be derived from the value of the ID attribute.

---

Semantics in front-end developments concerns whether to use a div or a header, or if some text should be a paragraph or a heading, or whether a list is to be ordered or unordered, and so on.

---

The client doesn’t care if you managed to avoid using any classes and wrote no extraneous markup, but if using two classes and an extra div makes your job easier, and makes the site easier to maintain, you should opt for the extra code every time. There is no use making your life more difficult because you think that avoiding an extra few characters of HTML is the right way to go. Be kind to yourself and your team.

---

Code is to a website what bricks and mortar are to a building: very important, but not really what people turn up to see. 

---

