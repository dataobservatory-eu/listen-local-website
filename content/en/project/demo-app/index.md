---
title: Demo Recommendation App
summary: Demonstration of a locally relevant alternative recommendation system.
tags:
- recommendations
date: "2020-12-01T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: 
  focal_point: Smart

links:
- icon: twitter
  icon_pack: fab
  name: Follow
  url: https://twitter.com/dataandlyrics
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

A machine learning recommendation system is always following a strict goal, and it keeps getting better and better in achieving that goal. The most fundamental question is who is setting the goal?  A media platform that wants to maximize the time you spend in front of the screen, regularly watching ads.  A digital streaming provider that wants you to always listen to their music.  Or yourself?
Our demo recommendation system allows you to set the target.  You can start from a radio hitlist, a radio playlist, or your own playlist, and design your own target, very similarly to how regulators set their local content requirements.  Do you want to have 20% Slovak language recommendations?  Or 15% performed by artists and bands who identify as Slovak? Or Dutch? Or 20% songs made in Slovakia by Slovaks?

In this demonstration, we modified Spotify’s algorithm, because we believe that it is the best proprietary system in the world with the most open API. While Spotify does not reveal its algorithm or its’ precise goal setting, it gives back a lot of information about the music it can potentially recommend. It also has a relatively well documented system, so we know roughly what is going on behind the scenes.  This is not true for most DSP systems.

Spotify is recommending a playlist of songs or recordings, and we do the same, but we allow you to control the target of the system and we reveal the steps.  Similarly, to Spotify’s or YouTube’s system, we first create many candidates to the playlist, then we narrow it down to songs that we believe fit best your original playlist.

Our [demo recommendation system](https://dataobservatory.shinyapps.io/demo-app/) is a utility-based system because it starts from Spotify’s original, native recommendations, but places a higher value to songs that follow your target settings.

1.	The highest level of utility is given to Spotify’s generic recommendations, if they match the target criteria, i.e., they contain enough music from artists with Slovak identity, or Slovak releases, or Slovak language songs.  We believe that Spotify’s algorithm is great if it works under control. 
2.	The second highest level of utility is given to artists whose works fulfil the criteria, and according to Spotify, they are like the artists’ in the reference playlist. Spotify’s similarity is based on both musicological and descriptive features and user interaction with the music.  When they perceive an artist to be similar, he or she is likely to be similar.
3.	The third highest level of utility is given to songs that are coming from the same genre as (some of the) user’s playlist items, but which are ‘Slovak’.
We create a set of song candidates, and then we compare them to the original songs in the user’s playlist. Using a similarity measure, we eventually create a playlist that fulfils the target criteria set by the user.

{{< figure library="true" src="plots/recommendation_flowchart_plot.png" title="Our recommendation flow" >}}

Most recommendation systems use three type of information: information about the music itself, information about the users who played or interrupted the music, and whatever textual information the provider finds in the data the artists/labels sent in, or journalist or the band wrote about themselves. In our demonstration, we want to show that if you want a system to work for you, you must be able to control the data inputs – for example, the words that describe your music in a way that is understandable for Spotify’s, YouTube’s, or our system.  We demonstrate this with the [Demo Slovak Music Database](https://listenlocal.community/project/demo-sk-music-db/), which is an open access, opt-in, opt-out database. The artists and Slovak musicologists have a say in how the information about the data is treated.

We also want to demonstrate that for the promotion of a labels, a creator collective’s, or a country’s repertoire, it is very important to cleverly set goals. From an ethnomusicological point of view, it is not sufficient to say that you would like to have 20% Slovak music. In our demonstration we are creating a gradual definition of ‘Slovakness’.

There are many targets that can set to promoting “Slovak music”, or “Slovak jazz”, or “European music”, or “new music”.  We can train algorithms that tell you which is the city or country where people listen to most similar music to “Slovak pop”.  We can build an app that gradually introduces classical and contemporary Slovak or European music to pupils in a school, starting with music that they are already familiar with and appreciate, and step-by-step recommending relevant new discoveries, always allowing them to give feedback. Or we can help radio editors to fill up a part of their airtime with artists who live in their city, region, or country.

Algorithms can have many unintended consequences.  For example, they can recommend music that they already know better in a small country, eventually reducing the already small audience reach and market opportunity of local artist. We believe that this can only be prevented if local artists and their managers understand what a streaming providers’ or media platform’s algorithm does – what data goes in and what sort of recommendation comes out.

Our approach is open collaboration – we use data that is open for the participants, and algorithms that can be studied or even modified by our partners.  This way not only bad consequences can be prevented, but the most desired outcome can be achieved by artists, creators, or their representatives. We believe that you can only achieve your goals if you understand and control both the data and the algorithm. 

