This is a summary of my project for OpenAvenues. 

This project simulates a recommendation for users using Data Analysis through the Lambda architecture. It goes over months of data collected from an online store and provides recommendations and insights to the user based on trends calculated. 

## Table of Contents 
* [Motivation](#motivation)
* [Summary of approach](#summary-of-approach)
* [Results](#results)
* [insights](#insights)
* [What I learned](#what-i-learned)
* [How to use this repository](#how-to-use-this-repository)

## Motivation
I use Amazon, Youtube as well as other services on a daily. While browsing these websites I never really thought about how it worked. While working on this project and learning about how recommendations and Kafa architectures work I was intrigued by how these websites do recommendations. I wanted to emulate a consumer website and recommend trending products as well as similar products to what the user interacted with as seen in this screenshot of Amazon

## Summary of approach
For this project, I decided to follow the basic Lambda architecture as seen below. Here is a sketch of me using the same architecture and brainstorming features I wanted. I decided to connect the BatchLayer and ServingLayer and have the SpeedLayer run adjacent to it and have the data feed into the Batch and ServingLayers as well as the results being fed into the query as you can see above. 

## Results
* Batch Layer Results:
* Bucket 0: Trending items: {1307153: 0.5, 4100346: 0.25}
* Bucket 1: Trending items: {45300114: -0.5, 1307153: -0.5, 5100542: -0.5, 3600666: -0.5, 4804137: -0.5, 4100346: -0.25}
* Bucket 2: Trending items: {45300114: 0.5, 3600666: 0.5, 4804137: 0.5}
* Bucket 3: Trending items: {23100035: -0.5, 1002633: -0.5, 12711562: -0.5, 2800396: -0.5, 1801739: -0.5, 5100817: -0.5, 45300114: -0.5, 3600661: -0.5, 5000475: -0.5, 3600666: -0.5, 5300125: -0.5, 3700766: -0.5, 5301663: -0.5, 17300769: -0.5, 1004836: -0.5, 12703015: -0.5, 12708392: -0.5, 4804137: -0.5, 26300078: -0.5, 26401582: -0.5, 1002542: -0.5, 1005105: -0.5, 1004210: -0.5, 12719535: -0.5, 26300084: -0.5, 5300405: -0.5, 1004856: -0.6666666666666666, 26400314: -0.5, 1005116: -0.5, 23900093: -0.5, 1005115: -0.5, 1004863: -0.5, 4900420: -0.5, 8700229: -0.5, 1004741: -0.5, 3801416: -0.5, 1005003: -0.5, 1005144: -0.5, 3300315: -0.5, 1004767: -0.8, 4802400: -0.5, 1500258: -0.5, 3900003: -0.5, 45100016: -0.5, 4100346: -0.5, 6700796: -0.5, 24100862: -0.5, 1307135: -0.5}
* Product IDs: [1307153, 4100346, 45300114, 5100542, 3600666]
* Trending Percentages: [1.0, 1.0, 1.0, 1.0, 1.0]
* Speed Layer Results:
* Similar Product Recommendations for User 532647354: [49100009, 1304409, 1005100, 2601423, 1005115]
* Precomputed results stored.
* Serving Layer Results:
* Stored Results: [(1307153, 1.0), (4100346, 1.0), (45300114, 1.0), (5100542, 1.0), (3600666, 1.0)]
* Product with the Highest Trending Percentage: 1307153
* Most Similar Product from Speed Layer: 49100009
* Recommending [Product ID: 1307153, Category: computers.notebook, Brand: lenovo and Product ID: 49100009, Category: nan, Brand: laston]

*Results showcase trending items out of 10000 rows that were sampled, similar products to what user 532647354 interacted with along with recommendations for said user*

## Insights
The data showcases a system that identifies trending products across different groupings, termed "buckets". Each product, denoted by an ID, has a trending percentage in these buckets; a positive value indicates rising popularity, while a negative hints at decreasing interest. For example, product "1307153" sees both growth and decline in different buckets.The speed layer offers real-time product recommendations for individual users, distinct from the general trend analysis. Lastly, the serving layer amalgamates these insights, pinpointing top trending products and interweaving real-time user-specific recommendations. Negative percentages, especially, highlight products witnessing waning demand or shifting consumer preferences in their respective categories.

## What I learned
* Sometimes, just analyzing data can teach us a lot, even without advanced predictions.
* Planning ahead is important. Decide what data you want to input and get out of your model before you start.
* What Kfka and Lamda architectures are
* How to create an advanced data pipeline in python that


## How to use this repository
This repository has a main_code file which you should download as well as the dataset_link file which leads you to the datasets used. Download them in the same file and rub the main_code file preferably on JypterNotebook or GoogleColab. Main_code_outputs shows all the outputs I got, when you run the file you should get something similar. The rest of the files showcase what I learned week by week while working on this project with OpenAvenues.
