Hello, so I want to build an application based on open street map. The idea is that I make it easier for people to explore what kind of dogs are popular in what kind of regions of Zurich. Luckily, we have all the information really detailed on what kind of dog is it, which kind of gender, which kind of color, like what, what, what type is it? Is it like orange or black or whatever? Is it what kind of race is it? How old is it? And we see that on, on, on Quartier level, like Altstetten, Seebach, and so on. And what I want to build is really an interactive map based on open street map where we can go through all the different regions. And yeah, how should this work?

So first of all, I want that I see the map of Zurich and then each of the Quartier should be one area. And then this area should be like, there should be a pattern (Muster), and this pattern should be rendered using PNG that you convert from an SVG. So first for each race that we have - first of all, what I want you to do is you go and look through the data, the data will be from essentially an API, it's a CSV file, and we should go through and create an inventory of all the different races that we have. And then for each race that you have, I want you to create an SVG. And then this SVG, because it's not nicely supported everywhere, we also want to generate a PNG out of it. And then essentially, we should have a map and we should use open street map, and then for each area, we should have the most popular dog breed animated, right?

And then we can also have another view. We can create like multiple interesting layers. One other layer is like if the female versus the male dogs are like more popular. So yeah, it should really be a specific application where you can explore and go through each of those and basically visualize it, right?

So from a UX perspective, there's like the different Kreise, right? And then Quartier. So for each Quartier, we will need to have like a few location area. Maybe do it on Kreis level probably, but it would be cool if it actually would be on Quartier level too. So we need to create an open street map using the Quartiere and Kreise.

For the SVG generation please use subagents (10-20 at a time) to implement it quickly. The SVGs should show their typical face. Filter out "Unbestimmt" breed. I should be able to switch between Quartier and Kreis view. The SVG should be rendered bigger when I click on one of them.

And then there should be like a year slider, right? So the data goes from like 2014 to 2025 and I want to be able to slide through the years and see how the popular dogs change over time, like which breeds become more popular and which ones go down. So that should be like a slider at the top or wherever, and then the map updates accordingly.

And then what would be really cool is we should also pull in other data from the Stadt Zurich open data portal, like data.stadt-zuerich.ch, and correlate it with the dog data. So for example:

- The median income per Quartier, right? So we can see like, do richer areas prefer certain breeds? Like is there a pattern where like Seefeld has more Labrador Retrievers and Altstetten has more Mischlings or whatever?
- Population density, like do areas with higher density have fewer dogs per person or more?
- Education level, like the tertiary education percentage, like do people with PhDs prefer poodles or something?
- Household size, like do single households have more small dogs and families have more big dogs?
- Demographics, like the median age, so do younger areas have more trendy breeds like French Bulldogs and older areas have more classic breeds like Dachshunds?
- Green space, like the percentage of green area, of parks and forests, do areas with more green space have more large dogs? Because, you know, they need more space to run around.
- The most common surnames per Quartier, right? And then we can combine that with the most popular dog breed and say like, oh, the Mullers of Seebach love Chihuahuas, you know? That would be funny.

So all of these correlation layers, I want them to be displayed directly on the map. Not like a separate panel or overlay, but like directly as choropleth coloring on the map polygons. So there should be like a dropdown or a layer selector where you can switch between:
- The top breed view (default, with the pattern fill)
- Income
- Population density
- Dogs per capita
- Education
- Household size
- Median age
- Green space
- Small breed share
- Large breed share
- French Bulldog share
- Fun facts view

And each of these should color the areas with a nice color gradient, like greens for income, oranges for density, blues for education, whatever. And there should be like a legend bar at the bottom showing the min and max values and the color scale. And when you click on an area it should show the metric value prominently and also the rank, like rank 3 of 34 Quartiere or whatever.
