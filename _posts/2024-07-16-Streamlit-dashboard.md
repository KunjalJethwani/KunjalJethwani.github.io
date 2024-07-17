---
title : "YouTube API Streamlit Dashboard"
date : 2024-07-16 00:00:00 +0000
categories : [Streamlit]
tags : [Streamlit]
---

# Creating the Dashboard

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/7e3083e3-1bba-43e7-bcd7-368e30b96d5f/Untitled.png)

## Initial Settings

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/ad8d6b04-aa72-41a8-8203-736e823604b4/Untitled.png)

When you visit a webpage, there’s a specific name associated with it, and an icon too (a compact version of the name; for when you have a lot of tabs open). So that’s what the first two parameters in st.config() are for. Next, we have layout and how we want the sidebar to be, when the webpage is opened. More details on https://docs.streamlit.io/develop/api-reference/configuration/st.set_page_config.

Next, we set the theme using the altair library and specify a title for the page.

Okay, having done the initial settings, let’s move on to creating the original dataset.

First we get the API key from the user (no we can’t use our own key every time since it’s risky and every key has a limited quota; for better user experience, we could make it optional for the user to give an API key, so if the user enters an API key, it’s used, else we use our own). Also, we want the user to enter the YouTube channel ID of the channel they want to see a dashboard of. 

<aside>
💡 Extracting the YouTube channel ID of a channel is simple. Go to the homepage of the channel, right-click, and select ‘View Page Source’. Now, do a page search for ‘channel_id’. You should find it in one of the last few references, enclosed in an `href` attribute within a tag, such as:

href="https://www.youtube.com/feeds/videos.xmlchannel_id=ugottagetthispart"

</aside>

Once the API key and channel ID have been received, we create an API client (a tool to use APIs easily), and create our dataframe using the functions discussed earlier. I’ve also created the top views table now itself, you could create it later, right before displaying it (it’s a simple function to sort and get the top n viewed videos, find it in plots.py). 

 Also, we want our dashboard to be laid out in three distinct columns, so we set the relative widths for those. Now this isn’t fixed, you could experiment and see which one suits your choice of charts better. 

## COLUMN 1 - Top Viewed Table & Scatter plot :

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/5ef6a3de-01e3-48d6-ac5c-02e9f8b694d9/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/ea115a41-1ace-4388-9457-87b53bd47ee0/Untitled.png)

This table gives the top performing video titles along with their corresponding view count.

## COLUMN 2 - Views per Year Line Chart & Heatmap :

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/a72f3a54-7763-49c7-a46b-158c3da799ac/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/d8c43d1d-2321-48e5-b83e-82d9d8c82c5e/Untitled.png)

This shows us how the channel viewership has grown over the years. We see a pick at around 2019-20, which is probably due to COVID 19, which saw a surge in digital content consumption, especially technology & education related, worldwide.

Heatmap gives us an idea of the number of video uploads on different hours of the various days of week.

## The word cloud & info box :

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/42a7f16a-b4eb-4e1d-b988-8f09edfc51fe/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/d313c4b5-68aa-4318-8d54-7397d14697f2/784d6385-51da-433f-b421-8512732018df.png)

Word clouds are a great way to get a glimpse of what the channel mostly is about, moreover, it could be used to identify user sentiment, if made with comments.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/46e36ec8-071b-4180-9ec7-65e995e6e8c7/63a46f11-ccfa-4430-86a3-57b8e4792a32/Untitled.png)

This information box is optional, but I thought it just adds to the feel of the project 😄.
