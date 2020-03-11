---
layout: post
title:  "Playing with Azure Logic Apps | Part 1"
date:   2020-03-10 18:00:00 +0000
categories: Azure Experiment
---
Some of the consultancy work I do involves training. This is normally something that is managed through tools like Eventbrite to keep track of all the attendees.

**Enters the problem**. A lot of our clients we work with don't like the complexity of Eventbrite's backend system - which can be used to check in and look at reports etc. This means we duplicate all this information and summarise it into a spreadsheet for easier access.

This is where [Azure Logic Apps][azure-la] comes in! I am the kind of person who doesn't like to do something I can clearly see is inefficient. My idea to fix this was to create / pull information out of the [Eventbrite API][eventbrite-api], using Azure Logic Apps to streamline and automate this process.

![Azure Logic App Preview](/assets/azure-la-preview.png)

If you haven't use the tool before - it is the brother to Microsoft Flow (renamed Power Automate), which is a visual logic builder. I select different inputs, process these, and create outputs. This could be calling an API from Eventbrite, processing the data received, and then outputting it to a CSV file inside of OneDrive. Pretty awesome! And as far as pricing goes, you would need to run an app thousands of times before you even hit a budget of a few pennies.

Stay tuned - in the next blog I will show you more of how I created this and some of the problems I faced.

[azure-la]: https://azure.microsoft.com/en-us/services/logic-apps/
[eventbrite-api]: https://www.eventbrite.com/platform/api
