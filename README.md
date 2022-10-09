# WeRateDogs
> Udacity Data Analysis Professional Nanodegree Program
# Introduction
Real-world data rarely comes clean. Using Python and its libraries, you will gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it. This is called data wrangling. You will document your wrangling efforts in a Jupyter Notebook, plus showcase them through analyses and visualizations using Python (and its libraries) and/or SQL.
# Dataset
> The dataset that you will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user @dog_rates, also known as [WeRateDogs](https://twitter.com/dog_rates). WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "they're good dogs Brent." WeRateDogs has over 4 million followers and has received international media coverage. 
* Enhanced Twitter Archive: The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything. One column the archive does contain though: each tweet's text, which I used to extract rating, dog name, and dog "stage" (i.e. doggo, floofer, pupper, and puppo) to make this Twitter archive "enhanced." Of the 5000+ tweets, I have filtered for tweets with ratings only (there are 2356). I extracted this data programmatically, but I didn't do a very good job. The ratings probably aren't all correct. Same goes for the dog names and probably dog stages (see below for more information on these) too. You'll need to assess and clean these columns if you want to use them for analysis and visualization.
* Additional Data via the Twitter API: Back to the basic-ness of Twitter archives: retweet count and favorite count are two of the notable column omissions. Fortunately, this additional data can be gathered by anyone from Twitter's API. Well, "anyone" who has access to data for the 3000 most recent tweets, at least. But you, because you have the WeRateDogs Twitter archive and specifically the tweet IDs within it, can gather this data for all 5000+. And guess what? You're going to query Twitter's API to gather this valuable data.
* Image Predictions File: One more cool thing: I ran every image in the WeRateDogs Twitter archive through a neural network that can classify breeds of dogs. The results: a table full of image predictions (the top three only) alongside each tweet ID, image URL, and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images).

# Data Wrangling:
> After gathering data from different resources, assessing it visually and programatically, the fowwling issues were found and cleand:

*Quality Issues:*

1-	Archive DF:

* not all of them are original tweets. (78 replies, 181 retweets)
*	erroneous data type of (tweet_id, timestamp) columns.
*	some ratings were wrongly generated, some dogs aren't rated. (id=810984652412424192 for example), 
*	wrong representing of null values for some columns. (doggo, floofer, puppo, pupper)
*	inconsistent dog class names. (Some start with upper case) (Pupper/pupper).
*	dogs' classes must be of type category.

2-	Images DF:
*	erroneous data type of tweet_id column.
*	undescriptive column names.
*	some tweets don't have images.

3-	Tweets DF:
*	missing some tweets as they were removed.
*	erroneous data type of tweet_id column.

*Tidiness Issues:*
*	1 type of observational unit in 3 tables. (archive_df, tweets_df, images_df)
*	1 variable in the archive_df (dog_class) is in 4 columns.

# Key Findings:
*Using visualisation to find insights and answer questions:*
* The first question that popped in my mind is how active is this Twitter Account? it looks like he was more active at the beginning with a max of 350 tweets only in January 2016! But maybe he is getting disappointed with peoples’ not interacting with his tweets? Humm, that doesn't seem the answer :/ more fans fall for the cute dogs he posts over time, they even love to share the fun with their friends looking at the retweet’s growth graph! 

* But what do people love most in his account? Small little puppers or the old wisdom doggos? Oh, they seem to LOVE the oldies who have mastered that life thing! 
* WeRateDogs account has a unique rating system out of 10 where he gives most dogs (not the naughty ones) a numerator > 10. Why? Because "they're good dogs, Brent." But is he fair at giving those ratings? Does he also prefer old doggos or maybe he has another opinion? Looks like  pupers are a little naughty here. :) the wisdom doggo-puppo kicks again! And there is also a good relationship between high ratings and favorites’ count, good dogs deserve G-R-E-A-T LOVE. 


* Now let us move to their images to see how our 3 neural network algorithms did predicting dogs' breeds: 
  The Golden Retrievers, Labrador Retrievers, and the cute Chihuahuas were the most successful predictions.




