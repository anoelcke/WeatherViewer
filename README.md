# WeatherViewer

Weather Viewer is a platform where users will be able to access and visualize different weather models in one location.

## The Problem
Weather forecast data from major weather models around the world is often freely available however, many of the products that people would like to use to aid in armature forecasting and professional forecasting alike are behind a paywall. There is also some data that would be lovely to have like the UW WRF model that data is only available in pictures of the model and raw data is not available. As an armature weather enthusiast you will also find yourself going to many different sources to collect all of this data. Professionals have tools they pay for behind paywalls to solve this problem. 

Weather viewer will solve this problem by providing a free open source solution that can easily be configured to store data, view data and give various models a score based on how they did in your local market. Weather viewer will also combine all of this data into one central database. This means that you can use WeatherViewer as your only source for weather model data. The weather viewer UI will allow users to compare models in as many ways as they can come up with. It will allow users to compare different models next to each other or different runs of the same model. Users could even compare different runs of several different ensemble models side by side to pick up trends.

This application will also allow us to feed data from the models and our local observations into an ML algorithm that will help us decide how to weigh models in certain situations. This could be useful because sometimes its hard to tell which models have been reliable in given circumstances. This may also allow us to use ML in the future to better tune local forecasts.

Initially, this solution will be configured for data around the NW but would have applications else where and would be highly configurable. It will be built in a scalable way so that users who have high volume data needs will still be able to leverage this solution. Users will also have the ability to just take the backend system if they'd like to use the database side of the application to feed their own UI or into their own weather system.

## Technology
This platform will consist of several different parts, the data collector, the API, the database and the UI. In this section we will discuss what technology we plan to use foreach as well as touch on some implementation details.

### Data Collection
Data collection will be done mostly in python. This application will function as a cluster where each model that is configured will get it's own cluster. They will also be supervised by a system that will prioritize database access to the highest priority model. This will prevent to much data from being thrown at the database. The data collection software will check the FTP site or other site that has the data to see if there have been any updates. Once there have been updates it will get the data, process it and put it into the database. This system will poll the site that the data is located as often as you want as this value is configurable.

### API
The API will provide access to the data in the database. For the API we are planning to use a .NET 7 API. This should allow quick access to the data. There really isn't much to say about the API except that it will get that data. I'm planning to allow the API to be configured in a variety of of ways so you can tune the API to work for your deployment environment.

### Database
For the database I am planning to use a no SQL implementation. Though weather data from model to model is similar, it isn't that easy to generalize and using a no SQL database will allow use flexibility when storying the data. I'm not sure which no SQL implementation we will pick as it has been a while since I've looked into no SQL databases. I'm planning to benchmark this and choose an option that gives us the best performance and most flexibility. Likely, I will also allow this to be configurable to an extent. For big data users they may want to configure each data source to have its own API. I would also like to support database replication so that we can enable customers with high loads and large data sets. These features however will be prioritized the lowest so early version likely won't have these features.

### UI
I am planning to use React JS to write the UI as well as a charting framework. I haven't worked with a charting framework in some time so I need to do some research on which framework I would like to choose. I am planning to use react because it will allow for a response flexible UI that will give a good user experience. I've worked in react before and find the modular nature of the framework really helpful in this kind of scenario. 

## Requirements and Technical Designs
Given the technical nature of this app most of the requirements will be technically driven. There isn't much business logic in this app because it isn't intended to be a business.Rather it is a pet project that I'd love to see turn into an open source weather data solution for many different people. In this section we will talk about the technical details of each of the systems mentioned above. 

### Data Collection System

### API

### Database

### UI