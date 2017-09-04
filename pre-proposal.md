## Boys & Girls Club Program Analysis

Executive Director needs to annually report to the state on effect of Boys & Girls Club after-school program. This program helps struggling students and is funded by the state. His immediate goal would be me completing EDA, next goal would be definitively showing effect (or lack thereof), and “moonshot” would be a predictive model that identifies the important features and help identify students with most need.

**What am I attempting?** To build a model that could predict how much students would improve with after-school tutoring based on current performance and (carefully used) demographic data

**Expected to use:**
* EDA: python and Excel
* Algorithm: Linear Regression or Random Forest
* Presentation: Slides with some visualizations

**Data Sources** are readily available, just need background check
* State Data (.csv), ~1000 students, ~20 features
* Program Data (.csv), ~2000 studetns, ~30 features

**My take on this project is** that this isn't technically impressive or interesting to me, but demonstrates business value. A good backup plan.

## Chatbots that can emulate personalities

Chatbots are usually designed to answer questions or guide/motivate a user through a process. I want to see if I can make a chatbot troll somebody, make a chatbot get offended by somebody.

**What am I attempting?** I am attempting to 1) build model for sentiment analysis and 2) build model that can emulate conversation using that sentiment analysis as context.

**Expected to use:**
* EDA: python, (AWS for big data)
* Algorithm: NLP sentiment analysis
* Presentation: Web app to demonstrate chatbot

**Data Sources** are available, not sure if complete/consistent
* Positive/Negative Sentiment analysis ([csv](http://www.sananalytics.com/lab/twitter-sentiment/)), 5513 tweets, 4 classes
* Conversation Data ([Microsoft Maluuba](https://datasets.maluuba.com/Frames/dl))
* Question/Answer Data ([AWS S3](https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs)), ~400k questions, 2 classes

**My take on this project is** that it is technically impressive but aiming high. I would really enjoy it but may not get a working model in time for graduation.

## Sentiment Analysis of Speech

Classify customer service calls into positive or negative. I actually found out a company already does this (callminer).

**What am I attempting?** I am attempting to build model for sentiment analysis voice data.

**Expected to use:**
* EDA: python, (AWS for big data)
* Algorithm: NLP sentiment analysis
* Presentation: Slides with visualizations to show results, maybe a demo

**Data Sources** are unlabeled or not an exact fit
* Speech Recognition Data ([not sure of format](http://www.voxforge.org/home/downloads/speech/english/davidlynnthomson-20170222-hej#-jNRPfqpMudd0ArtQ0ZusQ))
* Mood of Songs Data ([jupyter notebook loads it](https://github.com/rasbt/musicmood))

## Predicting Traffic Accidents

#### This seems to be the most interesting to everyone I've talked to (Chris, Dan, Ryan, Edward)

Predict traffic accidents using past accident information, weather, and event info (such as ACL) into account.

**What am I attempting?** To predict the roads/areas where traffic accidents are most likely to occur. Understand the dominant features, look at trends over time.

**Expected to use:**
* EDA: python, (AWS for big data)
* Algorithm:
* Presentation: Slides with visualizations to show results

**Data Sources** Traffic data is public and has everything I could imagine (minus personal/identifying information)
* Accident data ([csv](https://cris.dot.state.tx.us))
* Traffic data (csv from city of austin, google waze)
* Weather data (likely to be available, haven't looked)
* Event data (web scrape austin512, acl, etc)

## Predicting Movie Success

Predicting a movie's success (measured in either rotten tomato score or worldwide revenue)

**What am I attempting?** Does the people involved with a movie (writer, director, actors, studio) predict a movie's success? Is movie length/topic an important factor? Are certain topics hard/easy to succeed with?

**Expected to use:**
* EDA: python, (AWS for big data)
* Algorithm:
* Presentation: Slides with visualizations to show results

**Data Sources** I know datasets exist and that web scraping the following sites is possible, havent looked into it more though
* IMDB (people involved)
* Rotten tomato (ratings/reviews)
* Some screenplays are publicly available via IMDB
