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
* Speech Recognition Data ([not sure of format](http://www.voxforge.org/home/downloads/speech/english))
* Mood of Songs Data ([jupyter notebook loads it](https://github.com/rasbt/musicmood))
