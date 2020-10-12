---
header:
title: Building an NBA betting model using Google Cloud Platform
categories:
  - Analytics
---
With the NBA season coming to a close, the timing could not be worse - I have developed an [NBA betting model web app](https://nbamodel-223111.web.app/). Although I'm not interested in betting on NBA games anymore, I thought this would be an interesting academic exercise. It has been agood reason to dive deeper into ssome key software enginerring practices.

The model is based largely on Dean Oliver's [Four Factors](https://www.basketball-reference.com/about/factors.html) - the most important statistics that determine who will win a basketball game. Shooting, turnovers, rebounding and free throws. Other advanced team and player statistics will be included in the future to hopefully produce a more accurate model.

The NBA betting model is built using Google Cloud Platform and is completely serverless. NBA team and schedule data is scraped using python scripts taking advantage of packages such as `BeautifulSoup` and are run using GCP's Cloud Functions, the data is then processes to GCS buckets and subsequently BigQuery. The model is then created and run using BigQuery - with scheduled query outputting `json` to another GCS bucket via another Cloud Function invoked by a Pub/Sub Topic. From here a static Vue [website](https://github.com/anthonypiccolo/nbamodel) is hosted via Firebase with a compontent serving the `json` via an Axios HTTP request.

<img src="https://anthonypiccolo.xyz/assets/2020/10/nba-betting-model-architecture.png" alt="NBA model architecture" width="2188" height="1038/>

This software architecture does not use any compute ressources and is not going to incur any billing costs in GCP.

I plan on writing additional posts detailing the code to scrape the NBA data, build the relevant piplines and serve the ultimate line for daily matchups.

