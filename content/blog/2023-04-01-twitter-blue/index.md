---
title: Who are Twitter Blue Users?
summary: "In this blog post, I explore who are the Twitter Blue subscribers. It is not celebrities, businesses or governments. It is our regular old Joe with fewer than a hundred followers."
subtitle: "In this blog post, I explore who are the Twitter Blue subscribers. It is not celebrities, businesses or governments. It is our regular old Joe with fewer than a hundred followers."
author: Harshvardhan
date: '2023-04-01'
slug: twitter-blue
categories:
  - life
  - thoughts
  - twitter
  - R
tags: []
---

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>

Almost a six months ago Twitter announced a new subscription service called Twitter Blue. It is a paid subscription service that costs paying \$8 per month (or \$11 per month via mobile purchase). And that monthly fee is a relative bargain: Larger institutions will have to pay at least \$1,000 a month for verification.

One can sign up to get a blue checkmark, prioritised ranking in conversations, half ads, long Tweets, Bookmark Folders, custom navigation, Edit Tweet, Undo Tweet, and more.

Launching a half-baked service is not a news in the tech industry. However, for a uitility service like Twitter which has global users not having the Android version sounds like a bad idea. For instance, Twitter’s largest market is India, an Android market. Plus, the prices are in dollars.

Seriously, who will pay ₹9,400 per year for a social media?

### Starting today, the original Twitter verification marks are gone.

On April 1, Twitter is set to strip away the legacy verification checkmarks from the platform in favor of the paid checkmarks associated with Twitter Blue subscriptions. Then starting April 15, the platform apparently will no longer promote non-paying Twitter Blue subscribers via its recommendation algorithm on the For You feed. (The inability to participate in the polls sucks.)

![On April 1st, we will begin winding down our legacy verified program and removing legacy verified checkmarks. To keep your blue checkmark on Twitter, individuals can sign up for Twitter Blue.](images/ss1.png)

Notable figures and outlets, from LeBron James to the White House, have said they won’t be paying for verification.

So, any Tom, Dick and Harry will have the blue checkmark but not the government agencies, celebrities, and influential figures. We’re gonna see a return of “real” prefixes in profile names.

### Who uses Twitter Blue?

[Travis Brown](https://github.com/travisbrown/blue/) has collated data on Twitter Blue users from the launch.

> We compiled this list by combining two approaches. The first uses a Twitter profile scraper that is one of the components of the Hassreden-Tracker project, which was supported by Prototype Fund in 2022. The second involves searching the Twitter API for tweets by Twitter Blue subscribers, with queries designed to cover areas of the Twitter graph that the first approach may miss (for example non-English-language accounts).

I thought it would be interesting to see who are they. Here’s the exploration! You can download the R Markdown from my website.

First, I will load the required libraries.

``` r
# libraries
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0     ✔ purrr   1.0.1
    ## ✔ tibble  3.1.8     ✔ dplyr   1.1.0
    ## ✔ tidyr   1.3.0     ✔ stringr 1.5.0
    ## ✔ readr   2.1.4     ✔ forcats 1.0.0
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(lubridate)
```

    ## 
    ## Attaching package: 'lubridate'
    ## 
    ## The following objects are masked from 'package:base':
    ## 
    ##     date, intersect, setdiff, union

``` r
library(DT)
library(scales)
```

    ## 
    ## Attaching package: 'scales'
    ## 
    ## The following object is masked from 'package:purrr':
    ## 
    ##     discard
    ## 
    ## The following object is masked from 'package:readr':
    ## 
    ##     col_factor

``` r
# my favourite theme
theme_set(ggthemes::theme_clean())
theme_set(ggtech::theme_tech(theme = "google"))
```

Reading in the data. Source: <https://github.com/travisbrown/blue>. Since it doesn’t have column names, I will add it. Using `janitor`, I will clean the names. It’s [clean_names()](https://github.com/sfirke/janitor) function is an absolute blast. It converts `CAPITALS` and spaces to `small_letters_with_underscores`. Pretty standard.

``` r
# reading in data
df = read_csv("/Users/harshvardhan/Library/CloudStorage/Dropbox/Personal/personal-website/content/blog/2023-04-01-twitter-blue/accounts.csv", col_names = FALSE)
```

    ## Rows: 576873 Columns: 7
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (3): X2, X3, X7
    ## dbl  (3): X1, X4, X6
    ## date (1): X5
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
# adding column names and using janitor to clean names
names(df) = c("Account ID", "Screen name", "Legacy verification status", "Follower count",
              "Date Blue Sub", "Time Blue Sub", "Sub Status")
df = janitor::clean_names(df)

df
```

    ## # A tibble: 576,873 × 7
    ##    account_id screen_name  legacy_verificat…¹ follo…² date_blu…³ time_…⁴ sub_s…⁵
    ##         <dbl> <chr>        <chr>                <dbl> <date>       <dbl> <chr>  
    ##  1         12 jack         V                  6548240 2022-11-10  1.67e9 U      
    ##  2         18 Adam         <NA>                     4 2022-11-10  1.67e9 S      
    ##  3         22 rabble       <NA>                 18606 2022-11-10  1.67e9 U      
    ##  4         41 drx          <NA>                   130 2023-03-03  1.68e9 B      
    ##  5         58 Darkside     <NA>                  6065 2022-11-18  1.67e9 B      
    ##  6         59 Tim535353    V                     9369 2022-11-11  1.67e9 B      
    ##  7         76 marciadorsey V                    19598 2022-11-11  1.67e9 B      
    ##  8        294 ario         <NA>                  5783 2022-11-10  1.67e9 B      
    ##  9        295 joshk        V                   149304 2023-02-23  1.68e9 B      
    ## 10        324 chrisfralic  V                    41137 2022-12-16  1.67e9 B      
    ## # … with 576,863 more rows, and abbreviated variable names
    ## #   ¹​legacy_verification_status, ²​follower_count, ³​date_blue_sub,
    ## #   ⁴​time_blue_sub, ⁵​sub_status

Here’s a brief detail on columns.

<table style="width:99%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 67%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Column Name</th>
<th>Description</th>
<th>Example Values</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>account_id</td>
<td>Account Identifier</td>
<td>12<a href="#fn1" class="footnote-ref" id="fnref1" role="doc-noteref"><sup>1</sup></a>, 18, 22</td>
</tr>
<tr class="even">
<td>screen_name</td>
<td>Username</td>
<td>jack, Adam, rabble</td>
</tr>
<tr class="odd">
<td>legacy_verification_status</td>
<td><code>B</code> for Business accounts, <code>G</code> for Government accounts and <code>V</code> for Verified but type not specified</td>
<td>B, G, V</td>
</tr>
<tr class="even">
<td>follower_count</td>
<td>How many followers do they have?</td>
<td>6548240, 4, 18606</td>
</tr>
<tr class="odd">
<td>date_blue_sub</td>
<td>Date they first got Twitter Blue</td>
<td>2022-11-10, 2023-03-03</td>
</tr>
<tr class="even">
<td>time_blue_sub</td>
<td>Time they first got Twitter Blue</td>
<td>1668066884, 1668092307</td>
</tr>
<tr class="odd">
<td>sub_status</td>
<td><p>Current Twitter Blue status.</p>
<p><code>B</code> for Subscribed to Twitter Blue, <code>U</code> for Unsubscribed, <code>S</code> for Permanently suspended, <code>D</code> for Self-deactivated</p></td>
<td>B, U, S, D</td>
</tr>
</tbody>
</table>
<section id="footnotes" class="footnotes footnotes-end-of-document" role="doc-endnotes">
<hr />
<ol>
<li id="fn1"><p>I find it funny that Jack Dorsey, the founder of Twitter doesn’t have the first account. Who got it? Some engineer in his team?<a href="#fnref1" class="footnote-back" role="doc-backlink">↩︎</a></p></li>
</ol>
</section>

Let’s dive in.

### Popularity of Twitter Blue

``` r
df1 = df %>% 
  # add year and week to the data
  mutate(year = as.character(year(date_blue_sub)),
         week = as.character(week(date_blue_sub))) %>% 
  
  # join year and week with a W
  mutate(year_week = paste(year, week, sep = "W")) %>% 
  
  # grouping and summarising for plots
  group_by(year_week) %>% 
  summarise(count = n()) %>% 
  
  # adding rounded labels
  mutate(lab = round(count / 1000)) %>% 
  mutate(lab = paste0(lab, "k"))

df1 %>% 
  ggplot(aes(x = year_week, y = count, label = lab)) +
  geom_bar(stat = "identity", position = "dodge", width = 0.7, fill = "#1DA1F2") +
  geom_text(vjust = -0.2, size = 4) +
  theme(axis.text.x = element_text(angle = 90, vjust = 0.5, hjust=1),
        axis.title = element_text(size = 14),
        axis.text.y = element_blank()) +
  labs(x = "Year and Week", y = "Number of New Subscribers",
       title = "Number of New Twitter Blue Subscribers") +
  theme(plot.title = element_text(size = 18))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

Twitter Blue added most number of users in the first two weeks of launch. The next peak is in the second week of 2023. What’s that for? Tell me in comments, if you know.

### Who are the subscribers?

#### Blue Subscribers with Most Followers

The list of Blue subscribers is pretty interesting.

Here’s the list of Blue subscribers with most followers. I am filtering only the users who are still subscribed to the service.

``` r
# All Hail ChatGPT!
scale_cut = function(x)
{
  return(ifelse(x >= 1000000, 
         paste0(round(x/1000000), "M"),
         paste0(round(x/1000), "K")))
}

verification = function(x) {
  y = character(length(x))
  for (i in seq_along(x)) {
    if (is.na(x[i])) {
      y[i] = "Regular"
    } else if (x[i] == "V") {
        y[i] = "Verified"
    } else if (x[i] == "B") {
        y[i] = "Business"
    } else if (x[i] == "G") {
        y[i] = "Government"
    }
  }
  return(y)
}

df %>% 
  filter(sub_status == "B") %>% 
  select(screen_name, legacy_verification_status, follower_count, date_blue_sub) %>% 
  slice_max(order_by = follower_count, n = 100) %>%
  mutate(follower_count = scale_cut(follower_count),
         legacy_verification_status = verification(legacy_verification_status)) %>% 
  datatable(colnames = c("Username", "Old Status", "# Followers", "Joined Blue On"))
```

<div class="datatables html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100"],["elonmusk","jimmyfallon","MileyCyrus","SportsCenter","iamcardib","SpaceX","ActuallyNPH","netflix","VancityReynolds","SnoopDogg","ImRaina","AnupamPKher","RTErdogan","Benzema","MrBeast","theweeknd","RealHughJackman","TwitterSports","FabrizioRomano","TwitterLatAm","PSG_inside","sabqorg","MarvelStudios","UberFacts","BillClinton","TwitterCreators","sonamakapoor","IndirectasRock","thekiranbedi","kata2bijak","TwitterMusic","ToniKroos","pledis_17","heekma","ashwinravi99","Alhilal_FC","paulpogba","IvankaTrump","NetflixFR","anandmahindra","AdamSchefter","TheNotoriousMMA","VictoriaJustice","DonaldJTrumpJr","lopezobrador_","kilicdarogluk","TheDailyShow","tcbestepe","dog_rates","EmmanuelMacron","DjokerNole","TwitterLive","carmeloanthony","TwitterTV","GaryLineker","mcuban","WillyrexYT","haluklevent","ESPNFC","chrishemsworth","abdulrahman","ESPNNBA","cz_binance","NatGeoTravel","chancetherapper","Avengers","cometaorg","Privacidades","Zedd","ANI","sudhirchaudhary","la_patilla","cuneytozdemir","TwitterSupport","hazardeden10","hollywills","kegblgnunfaedh","BDUTT","DisneyStudios","TwitterMovies","FCBayern","marca","seanhannity","RandyOrton","jccaylen","kasimf","introvertsmemes","UmFilosofoCitou","allkpop","FelipeCalderon","MKBHD","booba","TwitterAPI","vinijr","Dream","ActuFoot_","wojespn","TuckerCarlson","JohnLegere","Dev_Fadnavis"],["Verified","Verified","Verified","Business","Verified","Business","Verified","Business","Verified","Verified","Verified","Verified","Government","Verified","Verified","Verified","Verified","Business","Verified","Business","Business","Business","Business","Verified","Verified","Business","Verified","Regular","Verified","Regular","Business","Verified","Verified","Regular","Verified","Business","Verified","Verified","Business","Verified","Verified","Verified","Verified","Verified","Government","Verified","Business","Government","Verified","Government","Verified","Business","Verified","Business","Verified","Verified","Verified","Verified","Business","Verified","Verified","Business","Verified","Business","Verified","Business","Regular","Regular","Verified","Business","Verified","Verified","Verified","Business","Regular","Verified","Regular","Verified","Business","Business","Business","Business","Verified","Verified","Verified","Verified","Regular","Regular","Verified","Verified","Verified","Verified","Business","Verified","Verified","Regular","Verified","Verified","Verified","Verified"],["133M","51M","47M","42M","29M","29M","25M","22M","21M","21M","21M","20M","20M","20M","19M","17M","15M","15M","14M","14M","14M","14M","14M","14M","13M","13M","13M","12M","12M","12M","12M","12M","11M","11M","11M","11M","11M","11M","10M","10M","10M","10M","10M","10M","10M","10M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","7M","7M","7M","7M","7M","7M","7M","7M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M"],["2022-11-10","2023-03-10","2023-03-03","2022-12-19","2023-01-04","2023-03-22","2023-03-24","2023-02-08","2023-02-24","2022-11-10","2023-03-16","2023-02-18","2023-03-16","2022-12-20","2022-11-10","2023-01-08","2023-03-16","2023-01-19","2023-02-23","2022-12-20","2023-02-10","2022-12-06","2022-12-20","2023-01-19","2023-02-10","2023-01-19","2023-03-19","2023-02-11","2023-02-15","2023-02-14","2023-01-19","2022-12-20","2023-03-24","2022-12-23","2023-03-21","2023-03-18","2023-03-04","2022-12-22","2023-02-04","2023-02-18","2023-01-14","2023-03-21","2023-03-23","2023-01-26","2023-03-18","2023-03-21","2022-12-20","2023-03-17","2022-12-29","2023-02-23","2023-03-20","2023-01-19","2022-12-16","2023-01-19","2022-12-29","2023-03-23","2023-03-24","2023-03-23","2022-12-20","2023-02-10","2023-02-16","2022-12-20","2023-03-08","2023-01-10","2023-03-02","2022-12-20","2023-02-16","2023-02-16","2022-11-10","2023-02-09","2023-02-24","2022-12-17","2023-01-21","2022-12-16","2022-12-20","2023-03-18","2023-03-17","2023-02-25","2022-12-20","2023-01-19","2023-02-25","2023-03-07","2022-12-20","2023-03-24","2022-11-28","2023-03-17","2023-03-03","2023-02-14","2023-01-14","2023-03-22","2023-01-26","2023-01-15","2022-12-20","2022-12-20","2022-11-10","2023-02-11","2023-03-09","2023-03-16","2023-03-09","2023-03-16"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>Username<\/th>\n      <th>Old Status<\/th>\n      <th># Followers<\/th>\n      <th>Joined Blue On<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script>

Of the top-10 most popular accounts on Twitter, only Elon musk is the subscriber. This kinda speaks to the popularity of the service.

> [Top-10 Most Followed Accounts on Twitter, Wikipedia](https://www.wikiwand.com/en/List_of_most-followed_Twitter_accounts)
>
> 1.  ElonMusk, 133M
> 2.  BarakObama, 133M
> 3.  justinbieber, 113M
> 4.  katyperry, 108M
> 5.  rihanna, 108M
> 6.  Cristiano, 108M
> 7.  taylorswift13, 93M
> 8.  narendramodi, 88M
> 9.  realDonaldTrump, 87M
> 10. ladygaga, 85M

### How many followers do Blue subscribers have?

For this task, I am going to break down the follower count into smaller groups. Since most Blue subscribers do not have a huge fan following (Elon Musk, again, is an exception), it is a necessary step — else, histograms wouldn’t look relevant.

``` r
x = df$follower_count

# Define the breaks for the bins
breaks = c(0, 100, 1000, 10^4, 10^5, Inf)

# Create a factor variable that represents the bins
bins = cut(x, breaks, labels = c("0-100", "100-1K", "1k-10k", "10k-100k", "100k+"))

table(bins)
```

    ## bins
    ##    0-100   100-1K   1k-10k 10k-100k    100k+ 
    ##   110132   193812   184328    70966    14155

``` r
bins = na.omit(bins)

ggplot(tibble(bins), aes(x = bins)) +
  geom_histogram(stat="count") +
  labs(x = "Follower counts", y = "Number of Blue Subscribers",
       title = "Number of Followers for Blue Subscribers") +
  theme(plot.title = element_text(size = 18),
        axis.title = element_text(size = 14))
```

    ## Warning in geom_histogram(stat = "count"): Ignoring unknown parameters:
    ## `binwidth`, `bins`, and `pad`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

Holy moly, less than 5% of all Blue subscribers are “celebrities” on Twitter. So many have fewer than 100 followers. How many of them are bots!?

### Types of Accounts: Business, Government and Society

``` r
df2 = df %>% 
  # add year and week to the data
  mutate(year = as.character(year(date_blue_sub)),
         month = as.character(month(date_blue_sub))) %>% 
  
  # join year and month with a M
  mutate(year_month = paste(year, month, sep = "M")) %>% 
  
  # grouping and summarising for plots
  group_by(year_month, legacy_verification_status) %>% 
  summarise(count = n()) %>% 
  mutate(legacy_verification_status = verification(legacy_verification_status))
```

    ## `summarise()` has grouped output by 'year_month'. You can override using the
    ## `.groups` argument.

``` r
df2
```

    ## # A tibble: 20 × 3
    ## # Groups:   year_month [5]
    ##    year_month legacy_verification_status  count
    ##    <chr>      <chr>                       <int>
    ##  1 2022M11    Business                        9
    ##  2 2022M11    Government                      2
    ##  3 2022M11    Verified                      743
    ##  4 2022M11    Regular                    140720
    ##  5 2022M12    Business                      411
    ##  6 2022M12    Government                      3
    ##  7 2022M12    Verified                     1014
    ##  8 2022M12    Regular                     61709
    ##  9 2023M1     Business                      641
    ## 10 2023M1     Government                     13
    ## 11 2023M1     Verified                     1753
    ## 12 2023M1     Regular                    139096
    ## 13 2023M2     Business                      157
    ## 14 2023M2     Government                     28
    ## 15 2023M2     Verified                     1465
    ## 16 2023M2     Regular                    110771
    ## 17 2023M3     Business                      142
    ## 18 2023M3     Government                     43
    ## 19 2023M3     Verified                     2016
    ## 20 2023M3     Regular                    116137

``` r
ggplot(df2, aes(x = year_month, y = count, fill = legacy_verification_status)) +
  geom_col(position = "fill") +
  scale_y_continuous(labels = scales::percent) +
  theme(axis.text.x = element_text(angle = 90, vjust = 0.5, hjust=1)) +
  labs(x = "Year Month", y = "New Blue Subscribers")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

It feels like almost all the subscribers are Musk fanboys. There are almost no government accounts, very little business accounts and a few celebrities (who probably wanted to try the Blue service).

### How many of the original Blue Subscribers are still using it?

The data has a column called `sub_status` which has this detail.

``` r
sub_status_change = function(x) {
  y = character(length(x))
  for (i in seq_along(x)) {
    if (is.na(x[i])) {
      y[i] = "NA"
    } else if (x[i] == "B") {
        y[i] = "Still subscribed to Blue"
    } else if (x[i] == "U") {
        y[i] = "Unsubscribed to Blue"
    } else if (x[i] == "S") {
        y[i] = "Account suspended"
    } else if (x[i] == "D") {
        y[i] = "Account deactivated"
    }
  }
  return(y)
}

df %>% 
  mutate(sub_status = sub_status_change(sub_status)) %>% 
  group_by(sub_status) %>% 
  summarise(count = n()) %>% 
  ggplot(aes(x = reorder(sub_status, count), y = count)) +
  geom_bar(stat = "identity") +
  scale_y_continuous(labels = label_number(suffix = " K", scale = 1e-3)) + # for thousands
  labs(x = "", y = "Count",
       title = "Status of Original Twitter Blue Subscribers") +
  theme(plot.title = element_text(size = 18, hjust = 4)) + 
  coord_flip()
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-7-1.png" width="672" />

### Conclusion

There was a huge influx of Blue subscribers after the service was announced. The momentum didn’t last long. The subscriber addition rate fell down significantly, except in January when something extraordinary happened.

Out of the top-10 most followed accounts on Twitter, only Elon Musk himself has a Blue account. Some celebrities and businesses do have a Blue account but their group is dwarfed by regular Twitter Blue users.

Of the group that joined Blue, a good chunk (more than 30%) has left it already. This might be an underestimate given [Twitter is not actively removing verified badges](https://mashable.com/article/twitter-blue-subscriptions-lower) even after people stop the service.

What else do you find interesting? Tell me in the comments.
