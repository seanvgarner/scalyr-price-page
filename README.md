# Pricing Page

This is my swing at the Scalyr pricing page with the interactive slider. To test it out and get it running locally, download the repository, open terminal and cd into the root of the directory and run the following commands:

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

```

With that, it should open your preferred browser and take you to the page, Or you can open any browser of choice and navigate to localhost:8080

## Implementation

I decided to take on this project using Vue.js as I wanted to become more familiar with the framework (I love it so far!) and being that the current marketing site is built using Vue, I figured this would feel like a logical extension as well. In order to get something up and running quickly I used vue-cli and webpack to aid in getting a local server running and module/asset bundling.

The slider functionality is pretty straight forward but there were a couple tricky things to work around. For instance, the easiest slider to get up and running is the html input type="range" tag, and  even though cross browser capability wasn't a focus of the project, the problem with this slider is it doesn't have great support for mobile/touch devices at all. Because there was a goal to have the page be responsive to a smaller mobile viewport, I was hesitant to use the input range tag, plus they aren't very customizable in terms of styling. To solve this, in the Vue.js documentation I found a plugin called vue-slider-component that I used as my slider and it takes care of the mobile/touch screen issue. It is a tad more verbose to get up and running than the html tag, but I believe the trade off was worth it, and also allowed me to style more accurately to the design mock up.

The other concern was that the slider needed to reflect non-linear values. It is supposed to start from 1GB and range to 100TB, and we want the pricing to be automatically updated to reflect depending on the GB of the slider position. But we also want to switch at 1TB and beyond to a link that says "Get a Quote". If the slider was totally linear, being that 100TB is equal to 100,000GB and we begin at 1GB only, the start of the slider would reflect prices as intended, but then it would very quickly jump to the "Get a Quote" link and remain that way for the rest of the slider range. This isn't exactly intuitive and user friendly. I solved this by fixing the length of the slider's range (0-16) and using its value to index into an array of specific GB values. This allows Scalyr to highlight certain price points. What I have as the default GB/Price points is just an example, this could easily be adjusted to different price points if needed. Also, the relationship between GB and price can be completely customized with just a few more lines of code.

The page is responsive to multiple screen sizes and with that, I have the hamburger functioning to show/hide the top links when in a smaller viewport. After all, what good is a hamburger if it doesn't do anything?

I had good time with this project, and hope you enjoy. I am happy to answer any questions you may have!
