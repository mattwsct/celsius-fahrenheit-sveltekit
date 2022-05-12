# celsius-fahrenheit-sveltekit

I've added the site to a subdomain on my personal site, so you can see it in your browser. Please go to https://temps.mattwestcott.com to see it. Otherwise it is visible on my GitHub page at https://github.com/mattwsct/celsius-fahrenheit-sveltekit.

## Running the project

```bash
# to install dependencies
yarn

# format and lint the code
yarn format
yarn lint

# to run locally and test it out, try this:
yarn dev

# to build the project
yarn build
```

## Using SvelteKit

Initially this was intended to be a vanilla JavaScript app, but I have seen a lot about Svelte (and SvelteKit) and wanted to try it out. I wanted this app to be as lightweight as possible and I like that Svelte compiles the code down to pure JavaScript, without the bulk of a virtual DOM. It was my first time using Svelte, but I really enjoyed how easy it was to use. Placing variables in HTML was also straight-forward and simple. I think Svelte is a great choice for small, simple apps. The hot-reloading is also very fast during development.

## Decisions about the project

I wanted to keep the design simple and clean, and after creating the project with SvelteKit, I found that there was already counter functionality built in which I could use. So I decided to use the existing counter for celsius, and duplicate it for the fahrenheit counter.

Initially the counter came with an animation that scrolled the numbers up or down depending if the user tapped on the plus or minus buttons. I used that for the first version of the app. The celsius counter started at 24 and would only increment or decrement with the plus and minus buttons, I had also built in the functionality to display the correct temperature in the fahrenheit using: (x \* 1.8) + 32, and for fahrenheit to celsius: (x - 32) / 1.8.

After testing the app and sending it to some friends, I realised that people would want to use their keyboard to enter the temperature, so I decided to add a text input to the celsius and fahrenheit counters. Which also meant I had to remove the scrolling animation. Another friend also suggested that they'd like to see decimal points in the conversion, so I added that as well.

I encountered some issues when I added the text input, which was the unintentional ability to add letters and symbols to the value. I changed the "type" to "number" which solved the issue on Chrome, but the issue remained on Firefox and iPhone browsers. The solution I came up with was to validate the entry after the user presses the enter key, or as the user taps/clicks outside of the input box. Otherwise, the value would be updated with the value the user entered on each key press, as long as it included a positive or negative integer between -999ºF and 999ºF (or the equivalent in celsius).

The decision to limit the temperature range to -999ºF and 999ºF was made because I didn't want the text input to overflow the counter.

In the end the functionality was as follows:

- Incrementing the value with the plus/minus button would display whole numbers only on that counter, while showing up to one decimal point on the opposite counter.
- Text input was allowed, only so the symbols for the decimal point and the minus sign were possible. However, if there is an invalid letter or symbol after the enter button is pressed, or after the user taps/clicks outside of the input, the value becomes zero.
- Users are able to enter many decimals into the counters, but once they press enter or tap/click outside the input, it will be rounded to one decimal place.
- Entering any value above or below the maximum/minimum will change the value to the maximum/minimum.

## UI Design

As mentioned, I wanted to keep the design as clean and simple as possible, I removed as much of the text and titles as I could and left the essentials. Initially I had created a two-page site with an about page. But after reviewing the task I realised it needed to be a single page app, so I added the about text into the home page, under the counters. Perhaps it's not necessary, but the page looked a little too empty without it.

I added semi-transparent backgrounds to the counters which improve the appearance in both light and dark modes (in light mode the appearance is a little subtle, but I liked it). I used the orange Svelte colour for the temperature counters, and the complementary blue colour for the increment/decrement buttons.

## Responsive design

Making my sites responsive for mobile devices is always my main priority, as most users will be viewing our sites on their phones. I took a lot of time pushing new changes to get the element sizes just right to work on every modern phone screen size. I sent a link to my site to some friends and they would show me issues with the design on their particular devices, so I worked hard to improve the design for all device sizes. Initially the counters were always placed on top of each other, but I decided to make them side by side for the desktop view. The decision to add a semi-transparent background to the counters was also made to make the counters stand out better for both mobile and desktop.

## Dark mode

I added a dark mode button to the top right of the app, which changes the background gradient and the text color. I preferred the gradient background to solid colours because otherwise the site looks too plain. I noticed on iPhone browsers that the html tag maintains a white background, so I added additional code to the CSS to toggle the html background to black when dark mode is used also. I like the appearance of dark mode on this site, but I think the light mode looks cleaner, so I left that as the default.

## Issues

One issue I haven't fixed yet is if the user enters leading zeros in a value (eg. 00023), the value will continue to display with leading zeros until another conversion takes place from the other counter, or any of the increment/decrement buttons. However this issue only occurs if the user is intentionally entering leading zeros, and it doesn't affect the functionality of the app. I tried a few methods to remedy this, but the solution that worked best made my code too messy, and I wanted to keep it clean.

## Future additions

- I wanted to add "ºC" and "ºF" to the counters, but it would cause too many issues with the text input. And I'd have to add additional logic to the text input to allow the user to enter the symbols and then convert from that. I figured it wasn't necessary for now.
