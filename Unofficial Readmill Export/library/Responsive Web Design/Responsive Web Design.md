**Responsive Web Design** by *Ethan Marcotte*

But there’s always room for improvement—and this rough little prototype is no exception. For example, we could potentially restrict our slideshow to only appear on certain types of displays, making the script resolution dependent. For example, if we wanted to prevent it from loading at all on smaller screens, we could work a simple resolution test into our script: if (screen.width > 480) { $(document).ready(function() { … }); } That opening if statement is the JavaScript equivalent of a min-width: 480px media query: if the screen is narrower than 480 pixels, then the enclosed JavaScript won’t fire (FIG 5.20).

---

