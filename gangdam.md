author:            Mariusz Saramak
summary:           TomTom Maps SDK Introduction
id:                24242
categories:        sdk
environments:      android
status:            draft
feedback link:     github.com/mariopce
analytics account: 0

# TomTom Creating a custom Gangdam vector map style

## Overview of the tutorial
Duration: 0:05

This tutorial shows you how to create custom vector map style. In this tutorial you will do the following: 

* Modify a default TomTom style for vector maps with use of the Maputnik editor 
* Apply the newly created style 

Prerequesites

* API key
* Npm and Node.js

We recommend you to have npm and Node.js already installed on your machine to quickly boot up a http server.

Negative
: To get an API key you need register or sign in to TomTom Developer Portal. Request an evaluation API key to access the service you want to use the SDK with. 

Positive
: It is possible to have a single key(app) for all TomTom services, but you can also  choose : to have individual keys for the different services.

## Download our Maps SDK offline examples
Duration: 0:10

Before you start, you need to download the latest version of our offline functional examples from [here](https://developer.tomtom.com/maps-sdk-web/downloads) [Download functional examples](https://api.tomtom.com/maps-sdk-js/4.23.3/jssdk-4.23.3-distribution-vector.zip).

![tomtom_portal](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step1.png)

## Extract the examples
Duration: 0:05

Create a new directory and extract the examples there.

For this tutorial, I created a directory called "examples". This is how it should look like after the extraction:

![sdk_dir](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step2a.png)

The contents of the "sdk" folder should look like this:

![style_dir](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step2b.png)

There are several directories and files, but we are only interested in the following ones:

* glyphs - contains fonts used for rendering vector maps
* sprites - contains images used for rendering vector maps
* styles - contains json files with style definition

TomTom vector maps styles are compatible with Mapbox Styles Specification. This format defines rendered maps properties - fill colors, line styles and thickness, etc. To read more about this specification, please go to [here](https://www.mapbox.com/mapbox-gl-js/style-spec/) .

To be able to provide labels and additional images on the map (e.g. road shields) two more assets are required:

* glyphs - these are fonts in a binary pbf format. They are transformed to speed up rendering process. To read more about it, please go to here. This is a rather advanced article.
* sprites - they consist of two files:
  - image file - a png file containing concatenated images
  - index file - a json file describing content of an image file. 

Sprites might be provided in an additional form appropriate for high-DPI devices. In that case "@2x" suffix should be appended to the file names, e.g. "sprites@2x.png"
More about sprites can be found here.

## Run server with examples
Duration: 0:10

This step is a prerequisite needed to configure the styles editor. In order to accomplish it, you need to have Node.js installed (this is out of the scope of this tutorial). Please, refer to [https://nodejs.org/en/download/](https://nodejs.org/en/download/), if you need further assistance with this task.  

Open a console terminal and go to a directory created to host offline examples. Now, type in the following instruction:

``` bash
npm install && npm start
```

After a while, you should see text similar to the one in this picture:

![console](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step3.png)

If you would like to know more about running offline examples, you may take a look at one of our tutorials: [Running examples locally](https://developer.tomtom.com/maps-sdk-web/tutorials-basics/running-examples-locally)

## Upload styles
Duration: 0:15

There are several ways to edit styles. You may do this manually in a text editor of your choice, but we prefer to use Maputnik - a visual map designer. You may find it here: [https://maputnik.github.io/editor/](https://maputnik.github.io/editor/)

The first step is to upload a file containing a style definition to Maputnik. Click on the "Open" button.
![screen1](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step4a.png)

Now, in a popup window, select the "Upload" button.
![screen2](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step4b.png)

For this particular tutorial, we will edit the "basic_main.json" style. You may find it in the "styles" directory described in the"Extract the examples" step.

## Provide an API key in order to access data sources
Duration: 0:05

One of the prerequisites for this tutorial is to obtain API key for an Online Map product. Now we will use it.
  
Click on the "Sources" button.

![step5a](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step5a.png)

Next, replace "{key}" placeholder in each of the tile URLs with your API key.

![step5b](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step5b.png)

Close the overlay to apply the changes by clicking on X in the top right corner.

## Update glyphs and sprites paths
Duration: 0:05

In order to complete this step, we will use the http server with examples run in one of the previous steps. Click on the "Style Settings" button.

![step6a](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step6a.png)

In a popup window, replace "Sprite URL" with

```
http://localhost:8080/sdk/sprites/sprite
```

and "Glyphs URL" with

```
http://localhost:8080/sdk/glyphs/{fontstack}/{range}.pbf
```

![step6b](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step6b.png)

Close the overlay to apply the changes by clicking on X in the top right corner.

## Edit a style
Duration: 0:15

Now, you should be able to see a map in the editor. From now on, you may edit all style properties and you will see an impact of your changes instantly. To give you a glimpse of possibilities, we will change the color of oceans. Click on an ocean on a map and select the "Ocean or sea" layer name from a popup.

![step7a](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step7a.png)

From "Paint properties", select "Color".
![step7c](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step7c.png)

Set a color of your choice. After this operation, oceans should be filled with a chosen color.
![step7d](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step7d.png)

## Export a style
Duration: 0:05

In order to download an edited style, click on the "Export" button.

![step8a](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step8a.png)

In a popup window, choose the **"Download"** button.

![step8b](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step8b.png)

Your new style should be available on your computer. Rename to gangdam.json ;) :) 

## Test your new style
Duration: 0:10

Now, it's time to test your style. Go [here](https://developer.tomtom.com/maps-sdk-web/functional-examples#vector-map-style-altering) and upload the modified style (click on the "Choose File" button). After a while you should achieve a following result:


![step9](https://image.ibb.co/b1pFAS/gangdam.png)

Above steps allow you configure a default TomTom style for edition in Maputnik. If you are interested in the topic of vector tiles or the style customization, please find the following list of suggested further readings:

1. Online Maps Vector Tile documentation (https://developer.tomtom.com/online-maps/online-maps-documentation-vector/tile) in order to create custom styles you need to know more about a data source. In advanced use cases, it is useful to know possible layers' names and their types.
2. Maputnik editor documentation (https://github.com/maputnik/editor/wiki) guides and tutorials for the Maputnik editor




