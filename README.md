# Chart v. Heart: Spotify User Playlist Trends
### *Examining the relationship between songs that reached No. 1 on the Billboard Hot 100 chart and Spotify user playlist activity  for the period 2010 - 2017*

![Jupyter](https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white)![PYTHON](	https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue)![JSON](https://img.shields.io/badge/json-5E5C5C?style=for-the-badge&logo=json&logoColor=white)![PANDAS](https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white)

Prepared June 2024 for Nashville Software School's Data Analytics program.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Motivation](#motivation)
- [Data](#data)
- [The Question](#the-question)
- [Method](#method)
- [Challenges and Known External Factors](#challenges-and-known-external-facotrs)

## Quick Start
- Clone [repository]
- [Download Spotify Million Playlist Dataset]: Save within repository ``\spotify-user-playlist-trends\data\Spotify``
- Requirements: Jupyter 3.11.7

## In This Repo
- notebook folder: contains two python scripts.   
-- billboard_data_scrape: scrapes Billboard Hot 100 Chart for the analytical period  
-- spotify_billboard_analysis: processes Spotify files and explores activity related to top performing songs  
- viz exports folder: csv exports from the analysis notebook used in creating accompanying visuals, and for Power BI analysis  
- Chart v. Heart.pptx: cute 10 minute presentation that summarizes this analysis and its findings  
- Spotify Billboard Dashboard.pbix: Power BI dashboard that outlines chart and playlist activity for top performing songs  

## Motivation
Lack of data cohesion in the recorded music industry is a [well documented and ever-growing] issue in the recorded music industry.  This analysis is an early step in preparing to be part of a global data solution to empower music creators and consumers with accurate metadata.  Motivation for this analysis is twofold: 
1. Multisource analysis: stems from the desire to source statistics about recorded music from two independent sources and find ways to conduct accurate and reliable analysis.  Existing data sources maintained in recorded music often only have song names and song titles in common -- if that.  One must understand a problem to solve it, no?
2. The chicken or the egg: Do people engage with music because it is popular, or is music popular because people engage with it? Working to better understand behaviors around music consumption trends may provide insight into factors that make or break a song.

[↑ Table of Contents](#table-of-contents)
## Data
#### Billboard Hot 100 Charts
From [Wikipedia]:
> The Billboard Hot 100 is the music industry standard record chart in the United States for songs, published weekly by Billboard magazine. Chart rankings are based on sales (physical and digital), online streaming, and radio airplay in the U.S.  
>
> A new chart is compiled and released online to the public by Billboard's website on Tuesdays but post-dated to the following Saturday, when the printed magazine first reaches newsstands. The weekly tracking period for sales is currently Friday–Thursday, after being changed in July 2015. It was initially Monday–Sunday when Nielsen started tracking sales in 1991. This tracking period also applies to compiling online streaming data. Radio airplay is readily available on a real-time basis, unlike sales figures and streaming, but is also tracked on the same Friday–Thursday cycle, effective with the chart dated July 17, 2021. Previously, radio was tracked Monday–Sunday and, before July 2015, Wednesday–Tuesday.

Billboard Hot 100 charts are hosted online, each chart having a unique URL.  A user is unable to export or download charts.

#### Spotify Million Playlist Dataset
From AIcrowd.com:
>“The Spotify Million Playlist Dataset Challenge consists of a dataset and evaluation to enable research in music recommendations. It is a continuation of the RecSys Challenge 2018, which ran from January to July 2018. The dataset contains 1,000,000 playlists, including playlist titles and track titles, created by users on the Spotify platform between January 2010 and October 2017. The evaluation task is automatic playlist continuation: given a seed playlist title and/or initial set of tracks in a playlist, to predict the subsequent tracks in that playlist. This is an open-ended challenge intended to encourage research in music recommendations, and no prizes will be awarded (other than bragging rights).”

The dataset, as well as other information, is available [here]).  
[↑ Table of Contents](#table-of-contents)

## The Question
Does Spotify user interest in a song precede, contribute to, or follow its rise on the Billboard Hot 100 Charts?  
[↑ Table of Contents](#table-of-contents)
## Method
##### Source Billboard Hot 100 charts from January 2010 - October 2017
Tools used:
- Python
-- BeautifulSoup

Technique:
- For loops and datetime to store all URLs
- Webscraping with BeautifulSoup to extract required chart detail from HTML
- For loops and list concatenation to write chart data to CSVs for further analysts

##### Parse Spotify Million Playlist Dataset
Tools Used
- Python
-- JSON
-- OS
-- Numpy

Technique
- Loop through 1,000 JSON files to identify playlists updated three or fewer times
- Loop through subset to normalize nested JSON files down to the track level
-- Identify tracks belonging to playlists with three or fewer updates
-- Of that subset, identify tracks that held a position on the Billboard Hot 100 Chart

##### Unify - Create a Key
Datasets are independent; key created in each set in the format of ``artistname-songname`` to link datasets by song and ensure the proper songs are sourced for analysis.  Each dataset requires a number of string cleaning operations in order to match:  
Billboard: Artist name replacement ('Ke$ha' > 'kesha'), track name modifiers ('Uptown Funk!' > 'uptown funk'), track name Features and co-Artists  
Spotify: Exclude certain versions of a track ('remix', 'club', 'dub', 'version', 'cover'), removal of featured artists/co-artists  

[↑ Table of Contents](#table-of-contents)
## Challenges and Known External Factors (expressed as song titles)  
- The Times They Are A-Changin':  Billboard and Spotify both underwent major changes between 2010 and 2017 due to the rise in popularity of music streaming services and changes in how music is consumed.  The subsample of the Million Playlist Data is heavily skewed to the years 2016 - 2017.  
- IDGAF:  Spotify users that take time to curate personal playlists may not accurately represent the average listener.  Users interested in curating a playlist are likely attentive listeners with a genre, mood, or theme in mind; in other words, they're more likely to GAF.  
[↑ Table of Contents](#table-of-contents)


[//]: # (reference links)
   [repository]: <https://github.com/hayleymadden/spotify-user-playlist-trends>
   [Download Spotify Million Playlist Dataset]: <https://www.aicrowd.com/challenges/spotify-million-playlist-dataset-challenge/dataset_files?unique_download_uri=376100&challenge_id=277>
   [well documented and ever-growing]: <https://academic.oup.com/edited-volume/35420/chapter-abstract/303172721>
   [here]: <https://www.aicrowd.com/challenges/spotify-million-playlist-dataset-challenge/dataset_files>
   [Wikipedia]: <https://en.wikipedia.org/wiki/Billboard_Hot_100>

   [here]: <https://www.aicrowd.com/challenges/spotify-million-playlist-dataset-challenge/dataset_files>
   [Wikipedia]: <https://en.wikipedia.org/wiki/Billboard_Hot_100>