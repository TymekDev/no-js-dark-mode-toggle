_This is an excerpt from [my blog post published on 2024-01-11][]._

[my blog post published on 2024-01-11]: https://blog.tymek.dev/no-js-dark-mode-toggle/

## A Dark Mode Toggle Without JavaScript
Have you ever seen a toggle on a website that allows you to switch between a
dark and light mode? Now it's possible to implement one without JavaScript,
thanks to [`:has()` CSS selector][].

[`:has()` CSS selector]: https://developer.mozilla.org/en-US/docs/Web/CSS/:has

`:has()` premise is simple. Select a parent that has a given selector. Be it
children or sibling using `+` or `~`. With Firefox stable adding support for
`:has()` last month, [the browser support reached 90% according to
caniuse.com][]!

[the browser support reached 90% according to caniuse.com]: https://caniuse.com/css-has

Without further ado, let's start with HTML for the toggle:

```html
<!-- ... -->
<body>
  <label>
    <input id="dark" type="checkbox">
    Dark mode
  </label>
</body>
<!-- ... -->
```

I hope you see where this is going! Now, the CSS for this is _packed_. Packed
with tiny bits and tricks I learned. These are: declaring variables on elements
for an override, using `:has()`, and using `:checked` state selector.

```css
body {
  --fg: black;
  --bg: white;
  color: var(--fg);
  background-color: var(--bg);
}

body:has(#dark:checked) {
  --fg: white;
  --bg: black;
}
```

There are a couple more things that we can do such as:
- Making use of label's `for` attribute to decouple the label from the checkbox
- Hiding the checkbox
- Styling the toggle
- Changing labels based on the theme we are in
- `@media (prefers-color-scheme: dark)` support

---

In this repository you will find an implementation with these improvements. You
can view a deployed version at [tymekdev.github.io/no-js-dark-mode-toggle][].

[tymekdev.github.io/no-js-dark-mode-toggle]: https://tymekdev.github.io/no-js-dark-mode-toggle
