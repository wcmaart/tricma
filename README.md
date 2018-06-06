# TRICMA

The WCMA Tricma (pronounced WickMa TrickMa) is an umbrella project to hold the various parts of the collections, [graphql api](https://github.com/wcmaart/api) and [dashboard](https://github.com/wcmaart/dashboard) projects. There's some common information that's useful to have about all of them and this is the place to put it, as well as tracking issues that don't neatly fit into individual parts.

## Overview

The general idea is that we build a system that allows us to extract data from various data sources, be that CSV, JSON, XML files or a number of TMS system. Then allow that data to be combined and served from a common api source. The technology we've chosen means it looks something like this...

![Over view image](https://raw.githubusercontent.com/wcmaart/tricma/master/media/overview.png)

The three main items in blue are the three repos you can find here on [wcma](https://github.com/wcmaart/dashboard):

+ [The Dashboard](https://github.com/wcmaart/dashboard)

   The is the part of the project that allows to upload the data to the data store, upload images to the image store, set user accounts and other general administration tools such as logging and automating the data uploading.

   It also acts as a place for developers who wish to use the GraphQL endpoint to register for a developer API key and read the documentation.

+ [The API](https://github.com/wcmaart/api)

   This is the API that allows third part developers (with an API key from the [dashboard](https://github.com/wcmaart/dashboard)) to make calls to the API, which returns information about the data we have stored.

   In this case the technology we have chosen is GraphQL

+ The Collection "Spelunker"

   This is an example app, that shows how a developer may interact with the [API](https://github.com/wcmaart/api) and display the results.

### Technology choices

In the above overview we've used general terms for the parts that are external to our three main repositories, they are in turn;

#### "Various sources of information"

For us these consist of a single [TMS system](https://www.gallerysystems.com/products-and-services/tms-suite/tms/) and some well defined JSON files.

#### Authentication

We are using [Auth0](https://auth0.com/) to handle our user login and user roles.

#### Database

Our external datastore is ElasticSearch, in our case hosted on [elastic.co](https://www.elastic.co/) with a [Kibana](https://www.elastic.co/products/kibana) management panel.

#### Image hosting

We are uploading and hosting the images with [Cloudinary](http://cloudinary.com/).

#### Dashboard

Is mainly a Node + Express + express-handlebars application with a bunch of other stuff, see the [repo](https://github.com/wcmaart/dashboard) for more details.

#### API

Is a graphQL server built using Node + Express + express-graphQL, which backs onto the ElasticSearch database, see the [api repo](https://github.com/wcmaart/api) for more.

#### Collections Explorer

Is a node + react web app which pulls data from the graphQL server.

## Installation, aka Before you Begin

Before cloning the three repos you should probably set up accounts for at least...

+ [Auth0](https://auth0.com/)
+ [Cloudinary](http://cloudinary.com/)

...because you will need both of those before you can do anything.

You should also set up a local version of ElasticSearch and Kibana to store any data, see the [dashboard](https://github.com/wcmaart/dashboard) for more information.

Once that is set up you should follow the instructions on the [dashboard](https://github.com/wcmaart/dashboard) to start consuming data, and then follow the instructions on the [API](https://github.com/wcmaart/api) to expose the data as a handy GraphQL endpoint.

If you want to test the endpoint finally clone and run the collection.