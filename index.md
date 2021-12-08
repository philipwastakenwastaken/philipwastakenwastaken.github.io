---
layout: default
title: 02805 Project
---

# Introduction
<script type="text/javascript" src="https://cdn.bokeh.org/bokeh/release/bokeh-2.3.1.min.js" integrity="sha384-YF85VygJKMVnHE+lLv2AM93Vbstr0yo2TbIu5v8se5Rq3UQAUmcuh4aaJwNlpKwa" crossorigin="anonymous"></script>
<script type="text/javascript">Bokeh.set_log_level("info");</script>

<style>
.bk-root {
display: flex;
justify-content: center;
}

.bk-root > .bk {
flex-shrink: 0;
}

.awesome-marker .fa {
  margin-top: 10px;
}

.plotly-graph-div {
  margin: 20px 0px 20px 0px;
}
</style>

<style>#map {position:absolute;top:0;bottom:0;right:0;left:0;}</style>
<script src="https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.js"></script>
<script src="https://code.jquery.com/jquery-1.12.4.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js"></script>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.css"/>
<!--<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css"/>-->
<!--<link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.0.0/css/bootstrap-glyphicons.css"/>-->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css"/>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css"/>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css"/>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css"/>

<style>
#map_65ec61091708497a980c91eef883828c {
position: relative;
width: 100.0%;
height: 100.0%;
left: 0.0%;
top: 0.0%;
}

#map_5b8f52ff3df2410684f0aee33912544e {
position: relative;
width: 100.0%;
height: 100.0%;
left: 0.0%;
top: 0.0%;
}
</style>

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>

*"I think there is a world market for maybe five computers"* are the now famous (and often ridiculed) words proclaimed by then IBM president, Thomas Watson, in 1943. Ever since the advent of the first computer, the world has been undergoing a *digital revolution*.
Digitalization has made it easy for consumers to **(i)** share their opinions and **(ii)** rely on the opinion of others. This can be seen directly in the popularity of both review aggregators (e.g., *Metacritic*, *Rotten Tomatoes*) and review crowdsourcing (e.g., *Yelp*, *Trustpilot*, *Google Reviews*).

Over the years, *Yelp* has accumulated a bad reputation. Business owners feel forced to cater excessively to *Yelp* reviewers, as even a single negative review can be consequential. In fact, a survey showed that $$78\%$$ of business owners were concerned about negative *Yelp* reviews (Loten 2014), with articles like "*Yelp Is Awful for Everyone Involved*" and "*It's Time to Kill Yelp. It's not worth the harm it causes*" adding to the injury.
On the other hand, the significance of Yelp cannot be ignored. Luca 2016 found that an increase of one star on *Yelp* causes revenue to increase by $$5$$-$$9\%$$. Additionally, Anderson and Magruder 2013 estimated that an extra half-star on a
restaurant's rating causes the business to be fully booked $$19\%$$ more often.

Even though *Yelp* has a negative standing with businesses, some positives can be shown through the *Yelp Open Dataset* (Yelp 2021). The dataset contains millions of user reviews and business characteristics across 8 metropolitan areas throughout the period 2005-2021, however, in this project the focus lies on the city of Austin, Texas. In addition, interesting elements related to reviews are examined that might be able to help potential business owners.

# The social network visualized

We start off by exploring the bare essentials of *Yelp*: yearly growth and rating distribution of user reviews. This will allow us the establish important groundwork for the rest of the article.
The yearly growth should show if *Yelp* is even worth examining, and the rating distribution will give an initial impression of *Yelp* culture.

<!--- network vis here --->
<img src="images/network_vis.png">

Above we see the amount of user reviews published on *Yelp* each year in Austin. **Hover** over a bar column to see the exact amount. Note that *Yelp*, contrary to popular belief, also contains reviews for non-restauration businesses.
First of all, we clearly see that *Yelp* is displaying impressive growth. 2006 contains only 2786 reviews, whereas 2018 contains a whopping 167,037. This matches our expectation that review crowdsourcing has become increasingly important for consumers.
We may attribute the decrease in reviews from 2019 and onwards to the ongoing COVID-19 pandemic.

<!--- degree distribution here --->
{% include yearly_reviews_bokeh.html %}

In a *Yelp* review, the writer, along with an accommodating text, rates their experience at the given business from 1 to 5 stars, with 5 stars being the best.
The figure above is a *stacked bar plot*, which shows how the distribution of user review ratings has changed over time. Each bar column contains five uniquely coloured sub-columns (see legend), where each displays the
relative number of reviews for a given rating.  **Hover** over a column to see the exact star distribution.
Given that *Yelp* is notorious for negative reviews, the large amount of positive (especially 5 star) reviews across the board is surprising. Perhaps even more surprising, this trend seems to be increasing each year, peaking
at $$59.73\%$$ of all reviews being 5 star in 2021. However, we can also see that the proportion of 1 star reviews is increasing, albeit not at the same pace as the 5 star reviews. This indicates that while *Yelp* is becoming more positive, it is also becoming more polarizing. This could indicate that businesses need to take special care, as even small mistakes may shift an otherwise good review to a bad one.

As the years affected by the coronavirus cannot be considered representative, we do not wish to include this time period in further analyses. This means that we from this point on restrict our coverage to the time period 2005-2018.


# Community detection
In order to easier visualize the dataset, we narrow our focus to Austin, Texas. Austin is a city located in the United States within the state of Texas, serving as the state capital city. With a population of 978,908, it is the 11th largest city in the US
by population count. The city is therefore populous enough to be representative of the *Yelp* dataset. Austin also encompasses more than 100 neighbourhoods, making it ideal for map-style visualizations.

{% include b_per_neighbourhood_plotly.html %}

The above map shows the most central neighbourhoods in Austin, and the amount of businesses each neighbourhood has with at least one *Yelp* review. Neighbourhoods are colour-coded, where purple contains the least amount of businesses, and yellow contains the most. **Hover** over each neighbourhood to see the exact amount of businesses it contains. Most neighbourhoods are in the same range, with the only clear outlier being downtown Austin with 2026 businesses.

# The spoken word of *Avatar: The Last Airbender*

<!--- summarize the structure of avatar, episode counts, seasons etc.... --->
<!--- explain about the character dialogue.... --->

<!--- show word distribution here --->

## Nationality and speech

<!--- show word clouds here --->
As we have already mentioned, Austin is compartmentalized into several neighbourhoods. We will now explore the significance of location as a business owner in Austin.

The map below shows the colour-coded (defined by the chart to the right) review average for a given neighbourhood. **Hover** over a neighbourhood to see name, number of reviews and review average.
We see *clear* groupings when considering the review average. Central, South, West, Southwest and Northwest are generally considered to be the *desired* parts of Austin (Lin and Ji 2014). These are high income areas
with low crime rates, and are typically not ethnically diverse. These parts of Austin enjoy a high review average - most neighbourhoods have an average in the $$3.8$$-$$4.3$$ range.

## Business Attributes of Food-Places
The *Yelp* dataset contains several *attributes* for each business, denoting which additional facilities and services are provided. For example, this could be whether a business accepts credit card, allows dogs, provides free
versus paid WiFi and so on. These attributes are interesting, since we can use them to compare the average rating of a business that provides an attribute versus a business that does not.

{% include attributes_and_avg_review.html %}

The bar plot above compares the review average for five different attributes for specifically *food places*. Some attributes are binary (e.g., wheelchair accessible), while others (such as price range) contain multiple values. **Hover** over a bar column to see the exact value.
We implore the reader to explore the visualization on their own - but *dog lovers be aware*: the results might not be as you would have liked. As an example, try to also consider a business' smoking policy. In this case, there is a clear preference by the reviewers. Some of these results might be interesting, but remember that we must interpret them with a grain of salt, as correlation does not necessarily imply causation. The results are more so included for novel reasons.

# Final Words
As stated, *Yelp* has a negative reputation. However, by examining the *Yelp* dataset, some interesting elements could be found about the culture of *Yelp*, its impact and some elements potential business owners should have in mind. Reviews are getting more positive, though also more polarized. However, it is quite clear that social inequalities are reflected in the user reviews, which adds to the negative aspects of *Yelp*. We also saw how attributes affect the rating how a business, much to the dismay of dog owners. Either way, *Yelp* has, by the looks of it, come to stay. But business-owners-to-be might need to consider more than e.g. just the quality of their food, as other variables seem to impact reviews. Furthermore, reviewers of *Yelp* (which might include you), need to consider the impact of reviews and be fair.

# More Details

## Download
To download the scraped data from the fandom wiki, one can you this [link](https://drive.google.com/drive/folders/1clkgTPeM7uLm30IFX5zSLVsI_2E0MgXT?usp=sharing).

The google drive folder consists of three files:
- `episode_info_df.csv`: contains episode names, episode numbers, season numbers etc. for all episodes of both series.
- `avatar_data.csv`: contains the names of every character used and their nationality.
- `atla_lok_transcript.csv`: contains attributed dialogue for all characters.

The datasets are small and relatively easy to work with, so feel free to explore on your own.

## Explainer notebook
The more technically inclined readers can take a look at our *explainer notebook*. This notebook contains all the nitty-gritty details required for making this website, right from data scraping to full-on sentiment analysis. The notebook can be viewed in your browser using [nbviewer](https://nbviewer.org/github/philipwastakenwastaken/social-graphs-project-2021/blob/main/explainer.ipynb).

You can also view and download it from [Github](https://github.com/philipwastakenwastaken/social-graphs-project-2021). Note that running
the notebook yourself will take **several hours**, so only do so if you have patience.

# References

- Luca, Michael (2016). "Reviews, Reputation, and Revenue: The Case of Yelp.com". In: *Harvard Business School NOM Unit Working Paper No. 12-016*. Available at SSRN: https://ssrn.com/abstract=1928601 or http://dx.doi.org/10.2139/ssrn.1928601.
- Anderson, M.L., and J. Magruder (2013). "Does Yelp Affect Restaurant Demand?" In: *ARE Update 16(5):1-4*. University of California Giannini Foundation of Agricultural Economics.
- Loten, Angus (2014). "Yelp Regularly Gets Subpoenas About Users". In: *The Wall Street Journal*.
- Yelp (2021). "Yelp Open Dataset". Retrieved from: https://www.yelp.com/dataset at 08/05/2021.
- Lin, Carol and Ji, Matt (2014). "Austin Neighbourhoods". Retrieved from https://www.austintexasinsider.com/austinneighborhoods.html at 09/05/2021.
