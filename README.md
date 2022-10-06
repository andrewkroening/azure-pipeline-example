# Example Azure Data Pipeline

### Introduction

#### *Hello! Welcome to this example Azure Data Pipeline. This is a project that is meant to be illustrative. Because I constructed it using a student account in Azure, not all of the normal resources were available, so some engineering cutbacks were made. Conceptually, you can think of anywhere you see "Sharepoint" as a good place to insert "Database-of-some-kind X," or "SQL Something-or-another Y," or something like that. The important thing is that pipelines are important, but do not use them without caution or understanding of what you are trying to do. And equally important, what you are supposed to be doing.*

#### Follow [this link](https://youtu.be/uybarbS3r3A) if you'd like to watch the video demonstration of what I will explain below. If you are looking for the QR code to the survey and don't want to read this explainer, [click here](https://github.com/andrewkroening/azure-pipeline-example/blob/01900bcbb25d0b68d1a589aca06253cd507e1708/screen_shots/QRCode%20for%20Thanks%20for%20visiting%20today!.png).

### Pipelines in General

Here's a little sketch of the generic idea behind a data pipeline. We have a source that is generating data for us. Maybe this is a survey, a table that tracks sales in a database, or something similar. We want to use that data, but where it currently sits isn't valuable. So let's use some trigger (time, scheduled, or event-based) to initiate a sequence that extracts that data, does a transformation on it, and then loads it into an area we can use. The end is an important part to talk about. Everyone gets caught up in the flashy services and transformations in the middle, but don't forget to make your data end somewhere helpful, like in a feeder table for a business intelligence dashboard. A great question to ask is, "so what?"

![alt text](https://github.com/andrewkroening/azure-pipeline-example/blob/fba6b80fa1d08c037fc7d1e84c3676447b13671e/screen_shots/Screen_Shot_3.png?raw=true)

### An Example Pipeline

Here's an example pipeline. We'll use something similar in our demo later. Data is coming in, but its initial landing location isn't useful, so we have to move it along until we get to a final location. The arrows you see drawn are all connections we need to build. Remember, databases ***store*** data, they don't ***move*** data. We have to do that. In this hypothetical example, I've drawn two different data storage options in our generic cloud and a bunch of arrows that could all be individual services. But what if there is a better, cleaner, easier-to-manage way of doing it??

![alt text](https://github.com/andrewkroening/azure-pipeline-example/blob/fba6b80fa1d08c037fc7d1e84c3676447b13671e/screen_shots/Screen_Shot_1.png?raw=true)


As it turns out, some of the tools available to the modern cloud engineer are pretty robust. At the bottom of this example, I drew out a few ways to break this down to find efficiency. Maybe we want to put this entire process inside one service or break it down into two? Those are both possible. It depends on what you try to do and how many intermediate steps there are.

![alt text](https://github.com/andrewkroening/azure-pipeline-example/blob/fba6b80fa1d08c037fc7d1e84c3676447b13671e/screen_shots/Screen_Shot_2.png?raw=true)

### This Project

So that brings us to this specific project. Here's a picture of what we have going on:

![alt text](https://github.com/andrewkroening/azure-pipeline-example/blob/b190a09d8a9b4452916fdcf18f8ad4cc4ac80d55/screen_shots/Screen_Shot_4.png?raw=true)

* A Microsoft Form is catching survey results (QR-enabled) from a fictional store that we own. The Form inherently doesn't move the results; it just holds them
* We need an automated process (event-based in this case) to pick up the responses and move them to a storage location (Sharepoint for this case)
* From that location, we take the comments and send them off to a sentiment analysis service to return POS/NEU/NEG scores
* Those scores are returned to the original item in our storage location (Sharepoint)
* An e-mail alert is sent out if we got a bad review
* *Note: I cut this one short because of license limitations. A good step would be to ensure this data is included in a business intelligence dashboard so we can see the previous day's summary at our morning staff huddle. That report is probably best to be running on a scheduled refresh.*

Here's a picture of the actual Power Flow generated based on that framework. This is just an example; Azure offers hundreds of connectors for various stages of this process. We could use a Twitter trigger, send things to Dataverse, catch messages from Amazon SQS, or even push our outputs to AWS S3. There's a world of options out there.

![alt text](https://github.com/andrewkroening/azure-pipeline-example/blob/e2056c406eb99b8c88c11ee112f99f11d3d93d7c/screen_shots/Screen_Shot_5.png?raw=true)

***And if its the fall of 2022, and you are a student in the MIDS program, go ahead and scan the QR code below to give the survey a shot!! (Assuming University IT hasn't cut me off yet...)***

<img src="https://github.com/andrewkroening/azure-pipeline-example/blob/01900bcbb25d0b68d1a589aca06253cd507e1708/screen_shots/QRCode%20for%20Thanks%20for%20visiting%20today!.png" width=350>
