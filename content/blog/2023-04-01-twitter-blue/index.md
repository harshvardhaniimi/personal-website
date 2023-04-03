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
draft: false
---

<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>

<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

Around half a year ago, Twitter made an exciting announcement about a new paid subscription service called Twitter Blue. For \$8 per month (or \$11 per month via mobile purchase), users can sign up for a host of exclusive features, including a blue badge, prioritized conversation ranking, fewer ads, bookmark folders, custom navigation, tweet editing, undoing tweets, and more.

As handy as these features, the service is not yet fully available to all users, as it can only be purchased via the iOS app or web, not Androids. It’s unclear what the tangible benefits for common users are, except for a visibility boost. In my opinion, being able to edit tweets is unnecessary — you don’t need the ability to edit, you just need to forgive yourself.

While launching a half-baked service is not a new phenomenon in the tech industry, it’s concerning for a utility service like Twitter, which has a global user base, not to have an Android version. Twitter’s largest market is India, which is predominantly an Android market. Moreover, the prices for Twitter Blue are quite steep - who would pay ₹9,400 per year for a social media platform?

### Starting today, the original Twitter verification marks are gone.

On April 1, Twitter is stripping away the legacy verification badges from the platform in favor of the paid badges associated with Twitter Blue subscriptions. Then starting April 15, the platform apparently will no longer promote non-paying Twitter users via its recommendation algorithm on the For You feed. (The inability to participate in the polls sucks.)

> ![On April 1st, we will begin winding down our legacy verified program and removing legacy verified checkmarks. To keep your blue checkmark on Twitter, individuals can sign up for Twitter Blue.](images/ss1.png)

While these changes may seem concerning, they are part of Twitter’s ongoing efforts to increase revenue and create a more sustainable business model. Majority of their past earnings were from advertisements.

![](images/revenue.png)

> Annual revenue of Twitter from 2010 to 2021, by segment. Advertising revenue has been increasing while data licensing revenues are relatively constant. Source: [Statista](https://www-statista-com.utk.idm.oclc.org/statistics/274566/twitters-annual-revenue-by-channel/).

It remains to be seen how these changes will affect the user experience on the platform and whether they will be beneficial in the long run.

> Legacy verification badges on Twitter provided credibility and legitimacy to users, but with the introduction of paid badges, some may view the process as exclusive and biased towards those who can afford it.

The decision to no longer promote non-paying users via Twitter’s recommendation algorithm on the For You feed has raised concerns among influencers. This change may disproportionately affect smaller accounts and marginalized communities, who may not have the resources to pay for Twitter Blue subscriptions.

But not all are excited about it. In fact, most Twitter Blue subscribers are nothing close to influencers — over 20% has fewer than a hundred followers. Notable figures and outlets, from LeBron James to the White House, have said they won’t be paying for verification.

So, any Tom, Dick and Harry will have the blue checkmark but not the government agencies, celebrities, and influential figures. We’re gonna see a return of “real” prefixes in profile names.

### Who uses Twitter Blue?

[Travis Brown](https://github.com/travisbrown/blue/) has collected data on Twitter Blue users from its launch.

> We compiled this list by combining two approaches. The first uses a Twitter profile scraper that is one of the components of the Hassreden-Tracker project, which was supported by Prototype Fund in 2022. The second involves searching the Twitter API for tweets by Twitter Blue subscribers, with queries designed to cover areas of the Twitter graph that the first approach may miss (for example non-English-language accounts).

I thought it would be interesting to see who are they. Here’s the exploration! [You can download the R Markdown from my Github](https://github.com/harshvardhaniimi/personal-website/blob/main/content/blog/2023-04-01-twitter-blue/index.Rmd).

### Reading in the data

Data source: <https://github.com/travisbrown/blue>.

Since the doesn’t have column names, I will add it. Using `janitor`, I will clean the names. It’s [clean_names()](https://github.com/sfirke/janitor) function is an absolute blast. It converts `CAPITALS` and spaces to `small_letters_with_underscores`. Pretty standard. [See the code on my Github.](https://github.com/harshvardhaniimi/personal-website/blob/main/content/blog/2023-04-01-twitter-blue/index.Rmd)

#### Data

Here are the first ten rows of the data frame. I am using `kable` for printing a good looking table. (Later on, I will use `DT` for an interactive table where you can sort, filter and search.)

<table class=" lightable-paper" style="font-family: &quot;Arial Narrow&quot;, arial, helvetica, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:right;">
account_id
</th>
<th style="text-align:left;">
screen_name
</th>
<th style="text-align:left;">
legacy_verification_status
</th>
<th style="text-align:right;">
follower_count
</th>
<th style="text-align:left;">
date_blue_sub
</th>
<th style="text-align:right;">
time_blue_sub
</th>
<th style="text-align:left;">
sub_status
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
12
</td>
<td style="text-align:left;">
jack
</td>
<td style="text-align:left;">
V
</td>
<td style="text-align:right;">
6548240
</td>
<td style="text-align:left;">
2022-11-10
</td>
<td style="text-align:right;">
1668066884
</td>
<td style="text-align:left;">
U
</td>
</tr>
<tr>
<td style="text-align:right;">
18
</td>
<td style="text-align:left;">
Adam
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
4
</td>
<td style="text-align:left;">
2022-11-10
</td>
<td style="text-align:right;">
1668092307
</td>
<td style="text-align:left;">
S
</td>
</tr>
<tr>
<td style="text-align:right;">
22
</td>
<td style="text-align:left;">
rabble
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
18606
</td>
<td style="text-align:left;">
2022-11-10
</td>
<td style="text-align:right;">
1668111426
</td>
<td style="text-align:left;">
U
</td>
</tr>
<tr>
<td style="text-align:right;">
41
</td>
<td style="text-align:left;">
drx
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
130
</td>
<td style="text-align:left;">
2023-03-03
</td>
<td style="text-align:right;">
1677853595
</td>
<td style="text-align:left;">
B
</td>
</tr>
<tr>
<td style="text-align:right;">
58
</td>
<td style="text-align:left;">
Darkside
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
6065
</td>
<td style="text-align:left;">
2022-11-18
</td>
<td style="text-align:right;">
1668748244
</td>
<td style="text-align:left;">
B
</td>
</tr>
<tr>
<td style="text-align:right;">
59
</td>
<td style="text-align:left;">
Tim535353
</td>
<td style="text-align:left;">
V
</td>
<td style="text-align:right;">
9369
</td>
<td style="text-align:left;">
2022-11-11
</td>
<td style="text-align:right;">
1668139623
</td>
<td style="text-align:left;">
B
</td>
</tr>
<tr>
<td style="text-align:right;">
76
</td>
<td style="text-align:left;">
marciadorsey
</td>
<td style="text-align:left;">
V
</td>
<td style="text-align:right;">
19598
</td>
<td style="text-align:left;">
2022-11-11
</td>
<td style="text-align:right;">
1668142394
</td>
<td style="text-align:left;">
B
</td>
</tr>
<tr>
<td style="text-align:right;">
294
</td>
<td style="text-align:left;">
ario
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
5783
</td>
<td style="text-align:left;">
2022-11-10
</td>
<td style="text-align:right;">
1668076741
</td>
<td style="text-align:left;">
B
</td>
</tr>
<tr>
<td style="text-align:right;">
295
</td>
<td style="text-align:left;">
joshk
</td>
<td style="text-align:left;">
V
</td>
<td style="text-align:right;">
149304
</td>
<td style="text-align:left;">
2023-02-23
</td>
<td style="text-align:right;">
1677191326
</td>
<td style="text-align:left;">
B
</td>
</tr>
<tr>
<td style="text-align:right;">
324
</td>
<td style="text-align:left;">
chrisfralic
</td>
<td style="text-align:left;">
V
</td>
<td style="text-align:right;">
41137
</td>
<td style="text-align:left;">
2022-12-16
</td>
<td style="text-align:right;">
1671171125
</td>
<td style="text-align:left;">
B
</td>
</tr>
</tbody>
</table>

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

Let’s dive in to the analysis.

### Popularity of Twitter Blue

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

Twitter Blue added most number of users in the first two weeks of launch. The next peak is in the second week of 2023. What’s that for?

Tell me in comments, if you know.

### Who are the subscribers?

#### Blue Subscribers with Most Followers

The list of Blue subscribers is pretty interesting.

Here’s the list of Blue subscribers with over a million followers. I am filtering only the users who are still subscribed to the service. (So users who “tried” the service for a month aren’t included.)

To make the table interactive where users can sort and search, I used `DT`. I like `DT` for it’s simplicity. Its function `datatable()` is great for creating interactive tables easily. I’ve tried picking up several other table packages in the past like `kable`, `gt` is good for beautiful tables but they’re not interactive, yada yada.

<div class="datatables html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100","101","102","103","104","105","106","107","108","109","110","111","112","113","114","115","116","117","118","119","120","121","122","123","124","125","126","127","128","129","130","131","132","133","134","135","136","137","138","139","140","141","142","143","144","145","146","147","148","149","150","151","152","153","154","155","156","157","158","159","160","161","162","163","164","165","166","167","168","169","170","171","172","173","174","175","176","177","178","179","180","181","182","183","184","185","186","187","188","189","190","191","192","193","194","195","196","197","198","199","200","201","202","203","204","205","206","207","208","209","210","211","212","213","214","215","216","217","218","219","220","221","222","223","224","225","226","227","228","229","230","231","232","233","234","235","236","237","238","239","240","241","242","243","244","245","246","247","248","249","250","251","252","253","254","255","256","257","258","259","260","261","262","263","264","265","266","267","268","269","270","271","272","273","274","275","276","277","278","279","280","281","282","283","284","285","286","287","288","289","290","291","292","293","294","295","296","297","298","299","300","301","302","303","304","305","306","307","308","309","310","311","312","313","314","315","316","317","318","319","320","321","322","323","324","325","326","327","328","329","330","331","332","333","334","335","336","337","338","339","340","341","342","343","344","345","346","347","348","349","350","351","352","353","354","355","356","357","358","359","360","361","362","363","364","365","366","367","368","369","370","371","372","373","374","375","376","377","378","379","380","381","382","383","384","385","386","387","388","389","390","391","392","393","394","395","396","397","398","399","400","401","402","403","404","405","406","407","408","409","410","411","412","413","414","415","416","417","418","419","420","421","422","423","424","425","426","427","428","429","430","431","432","433","434","435","436","437","438","439","440","441","442","443","444","445","446","447","448","449","450","451","452","453","454","455","456","457","458","459","460","461","462","463","464","465","466","467","468","469","470","471","472","473","474","475","476","477","478","479","480","481","482","483","484","485","486","487","488","489","490","491","492","493","494","495","496","497","498","499","500","501","502","503","504","505","506","507","508","509","510","511","512","513","514","515","516","517","518","519","520","521","522","523","524","525","526","527","528","529","530","531","532","533","534","535","536","537","538","539","540","541","542","543","544","545","546","547","548","549","550","551","552","553","554","555","556","557","558","559","560","561","562","563","564","565","566","567","568","569","570","571","572","573","574","575","576","577","578","579","580","581","582","583","584","585","586","587","588","589","590","591","592","593","594","595","596","597","598","599","600","601","602","603","604","605","606","607","608","609","610","611","612","613","614","615","616","617","618","619","620","621","622","623","624","625","626","627","628","629","630","631","632","633","634","635","636","637","638","639","640","641","642","643","644","645","646","647","648","649","650","651","652","653","654","655","656","657","658","659","660","661","662","663","664","665","666","667","668","669","670","671","672","673","674","675","676","677","678","679","680","681","682","683","684","685","686","687","688","689","690","691","692","693","694","695","696","697","698","699","700","701","702","703","704","705","706","707","708","709","710","711","712","713","714","715","716","717","718","719","720","721","722","723","724","725","726","727","728","729","730","731","732","733","734","735","736","737","738","739","740","741","742","743","744","745","746","747","748","749","750","751","752","753","754","755","756","757","758","759","760","761","762","763","764","765","766","767","768","769","770","771","772","773","774","775","776","777","778","779","780","781","782","783","784","785","786","787","788","789","790","791","792","793","794","795","796","797","798","799","800","801","802","803","804","805","806","807","808","809","810","811","812","813","814","815","816","817","818","819","820","821","822","823","824","825","826","827","828","829","830","831","832","833","834","835","836","837","838","839","840","841","842","843","844","845","846","847","848","849","850","851","852","853","854","855","856","857","858","859","860","861","862","863","864","865","866","867","868","869","870","871","872","873","874","875","876","877","878","879","880","881","882","883","884","885","886","887","888","889","890","891","892","893","894","895","896","897","898","899","900","901","902","903","904","905","906","907","908","909","910","911","912","913","914","915","916","917","918","919","920","921","922","923","924","925","926","927","928","929","930","931","932","933","934","935","936","937","938","939","940","941","942","943","944","945","946","947","948","949","950","951","952","953","954","955","956","957","958","959","960","961","962","963","964","965","966","967","968","969","970","971","972","973","974","975","976","977","978","979","980","981","982","983","984","985","986","987","988","989","990","991"],["elonmusk","jimmyfallon","MileyCyrus","SportsCenter","iamcardib","SpaceX","ActuallyNPH","netflix","VancityReynolds","SnoopDogg","ImRaina","AnupamPKher","RTErdogan","Benzema","MrBeast","theweeknd","RealHughJackman","TwitterSports","FabrizioRomano","TwitterLatAm","PSG_inside","sabqorg","MarvelStudios","UberFacts","BillClinton","TwitterCreators","sonamakapoor","IndirectasRock","thekiranbedi","kata2bijak","TwitterMusic","ToniKroos","pledis_17","heekma","ashwinravi99","Alhilal_FC","paulpogba","IvankaTrump","NetflixFR","anandmahindra","AdamSchefter","TheNotoriousMMA","VictoriaJustice","DonaldJTrumpJr","lopezobrador_","kilicdarogluk","TheDailyShow","tcbestepe","dog_rates","EmmanuelMacron","DjokerNole","TwitterLive","carmeloanthony","TwitterTV","GaryLineker","mcuban","WillyrexYT","haluklevent","ESPNFC","chrishemsworth","abdulrahman","ESPNNBA","cz_binance","NatGeoTravel","chancetherapper","Avengers","cometaorg","Privacidades","Zedd","ANI","sudhirchaudhary","la_patilla","cuneytozdemir","TwitterSupport","hazardeden10","hollywills","kegblgnunfaedh","BDUTT","DisneyStudios","TwitterMovies","FCBayern","marca","seanhannity","RandyOrton","jccaylen","kasimf","introvertsmemes","UmFilosofoCitou","allkpop","FelipeCalderon","MKBHD","booba","TwitterAPI","vinijr","Dream","ActuFoot_","wojespn","TuckerCarlson","JohnLegere","Dev_Fadnavis","radenrauf","FaZeClan","cuppymusic","JJWatt","wikileaks","BillSimmons","benshapiro","LeventUzumcu","SportsNation","Cobratate","BETMusic","ARYNEWSOFFICIAL","charlidamelio","DisneyPlus","sundarpichai","Schwarzenegger","NatGeoPhotos","GameSpot","billboardcharts","MTVNEWS","NBCTheVoice","INDONESIAinLOVE","nflnetwork","ABZayed","GreysABC","ArabicBest","Haberturk","VitalikButerin","RealMikeWilbon","Patriots","DaniCarvajal92","jakepaul","choquei","MedvedevRussia","lukamodric10","rahulkanwal","Guarromantico_","altonbrown","dallascowboys","wroetoshaw","MnbrAlhilal","SF_Moro","WimShakespeare","HergunYeniBilg","verified","NazareAmarga","SintoniaVerso","MarioGoetze","SadhguruJV","dbongino","rameshsrivats","jordanbpeterson","cher","RapSheet","mikslmnc","ntsana_","KP24","KTRBRS","iamjoshuagarcia","Julius_S_Malema","RJ_Balaji","TheArabHash","WaltDisneyWorld","Boity","LalitKModi","soyfdelrincon","fashionpressnet","GMA","HumansNoContext","Jemima_Khan","steelers","Eagles","Jason_Aldean","VoceNaoSabiaQ","ReceinAja","ESPNNFL","DisneyAnimation","itfeelword","charlieputh","TwitterSafety","FreakyTheory","iCarly","takapon_jp","voiceofworldco","TwitterFashion","thibautcourtois","KellyannePolls","EspacioNoticias","DezBryant","THarmharm","Polo_Capalot","GeorgeTakei","FUKADA0318","susipudjiastuti","SouthPark","RondaRousey","billionaire_key","matteorenzi","nbcsnl","MrAncelotti","TwitterMENA","atsushiTSK","quackity4k","Vikkstar123","kayleighmcenany","YounusYSN","MiaMalkova","TheChainsmokers","KSASociety","arynewsud","pulte","SoyFedelobo","GilDoVigor","MovSto","nachofi1990","PrimeVideo","sopitas","News_Brk24","drharshvardhan","David_Alaba","MCHammer","jaketapper","DineshDSouza","WholesomeMeme","Ahmed1Afify","kojiharunyan","CaptainAmerica","Panthers","OCriador","ESPNCFB","TwitterFrance","archillect","CollegeGameDay","CarryMinati","robdyrdek","saylor","Nadeshot","TrollFootball","faridyu","russellcrowe","MLP_officiel","Variety","okx","jamesmaslow","Behzinga","marcoasensio10","BitcoinMagazine","Franklin_Graham","RodrygoGoes","PatMcAfeeShow","Inter","DestinyTheGame","Iron_Man","NumanKurtulmus","mishacollins","recehtapisayng","nevsinmengu","m_bukairy","itfeelstory","Broncos","marwilliamson","engineers_feed","SpongeBob","TwitterNews","mtvspain","RyanSheckler","ProjectLincoln","GwynethPaltrow","amrmsalama","AlwatanNews24","lexfridman","KEEMSTAR","thorofficial","DaneCook","charlieINTEL","adelalbdaljbar","drdrew","VogueRunway","ErinAndrews","Gxx_6","SilvestreFDC","packers","ClarissaYorke","hilalstuff","Seahawks","alaa_saeed88","MTVBrasil","BolsonaroSP","DrDisrespect","Dekchaikumkom","MoistCr1TiKaL","TfL","TheTopVideo","Koreaboo","NatbyNature","SpiderMan","vanehupp","SpeakerMcCarthy","AtlantaFalcons","AlissaViolet","MTVUK","abdelbariatwan","49ers","TwitterIndia","unge","toskofacts","herkesicinCHP","DJFreshSA","LouDobbs","euovitinn","RealGDT","KlasraRauf","ZerkaaHD","jessicakevibes","laurenboebert","msstol","TwitterGov","HongKong_Doll","spectatorindex","BuildIntoGames","Chiefs","khanfarw","sixers","TheBabylonBee","siasatpk","FrasesDeRenato","DisneyParks","TwitterJP","nybooks","NatGeoTV","KomsakAddams","RepMattGaetz","Acosta","nikolas_dm","BeatsByAssassin","whale_alert","SirKunt","AnwarLodhi","dallasmavs","bsindia","TrueKofi","TwitterBrasil","kaj33","blobyblo","HulkHogan","_nuna_V","AlbertoRavell","ericschmidt","BW","PyongLeeTV","s8n","iyiTweet","ozgurmumcu","ESPNDeportes","gtconway3d","TulsiGabbard","MTVteenwolf","GameGrumps","instablog9ja","kittyxkum","cristinafoxtv","TomFitton","bod_republic","notthefakeSVP","nacigorur","jakeowen","umitozdag","BillyM2k","fedeevalverde","futpicante","kimguilfoyle","Biakicis","JackPosobiec","New_M3lomat","mattgaetz","6BillionPeople","ChicagoBears","libsoftiktok","badassceo","WIREDScience","12numaraorg","ShamsCharania","taylornation13","ThatSummy","Giants","williecolon","nksthi","LAClippers","JudicialWatch","DiamondandSilk","SinEscritoss","kiyo_saiore","Sawarinni","thenanaaba","MTVLA","thereallisaann","chartdata","Lucasvazquez91","sfkkfs_","HoustonTexans","TwitterDE","himantabiswa","yummychiyo","maiconkusterk","DrStrange","odatv","FINALLEVEL","gorgeous4ew","Raiders","AmericanIdol","SantapanMinda","iamblackbear","itextosoff","domeelipa","tferriss","13burctahmin","k_alemat","hodgetwins","0xPolygonLabs","Cointelegraph","AFCAjax","sarameikasai","OANN","MissBNasty","Guardians","UnMatchedTier","ImagesAlbum","imamhussainorg","amouredelavie","BabyDogeCoin","Ravens","theblackpanther","RobertAlai","justsanaa","FightHaven","takigare3","DCoronell","bilio_muydunuz","blogdokter","muni_gurume","_dieuoff","WatcherGuru","KennyHamilton","TerribleMaps","hvgoenka","FirstTake","ESPNStatsInfo","cat_auras","PreetBharara","abhisar_sharma","daniellachavezc","NoContextBrits","MCChampionship_","Punztw","ToniRuediger","SypherPK","TwitterDesign","Footballogue","_Talal1","Saints","RealityPornKing","CNET","violetsaucy","futebol_info","_BeFootball","HaberturkTV","NunziatoLindi","BoredElonMusk","ErnestoChavana","kauweb","RM4Arab","PlobJai","AndrewYang","barisyarkadas","BuffaloBills","Overlokcu12","TmarTn","TO_TOSHIMITSU","CatWorkers","BishoujoMom","Awraaq","AHSFX","Suns","DeadlineDayLive","gadgetlab","historyinmemes","chamath","yisucrist","UGGLYTRUTH","AmericanAir","shitpostverdade","mimilkss","TheLeoTerrell","kiranshaw","APompliano","tuncsoyer","ABCWorldNews","coingecko","OuWrd","Siir_Sokaktadir","staryuukiii","modelpress","MaryLTrump","ConorMaynard","JamiiForums","RudyGiuliani","TheWalkingDead","arminvanbuuren","Temperrr","criminalminds","CathieDWood","dariusrucker","ChrisExcel102","ajitanjum","tiff08_","catturd2","Browns","Disneyland","AmongUsGame","SdqJaan","bayu_joo","AirdropDet","JaydenCole","SwaggerSouls","ReinaldoProfeta","ManuelaDavila","Azfarheri","yummykimmyx","Rconstantino","hnurwahid","DailyLoud","airdropinspect","Karchezzz","MuseDrip","latelateshow","Timcast","BashirAhmaad","trailblazers","HasbullaHive","sophiedee","TEDchris","Vikings","Lions","lenatheplug","LachlanYT","Jirayu_jj","Erdayastronaut","Korseries","maydarlingx","Almagro_OEA2015","RobSchneider","ShouldHaveCat","marissamayer","HowThingsWork_","JETAR9","KendraLust","MAKadhimi","4i_ui","laurenxburch","krakenfx","markets","Abdulaziz_Hmadi","bunnie_wifey","SaraCarterDC","PastorMalafaia","GustavoBolivar","NYRangers","BretBaier","tsuda","AlisaPikaPika","TOKAI_ONAIR","geoffkeighley","cctv_idiots","MannyMua733","omarepps","Ballislife","w_terrence","CelebsArabic","hicetikdegill","Bengals","bernalacin35","UranRigoberto","Dennysiregar7","SushantBSinha","DikenComTr","thelilianajas","soogz1","AirdropStario","PatoBullrich","escritosheart","AoTWiki","GabbbarSingh","Chris_Broussard","s_hm2030","MikominCosplay","AntMan","CynthiaLIVE","kenichiromogi","Garrett_Watts","kicksonfire","1qadem","canyilmaz1","hogrbe","HuobiGlobal","al3raabq8q8","papikunno","ZackSnyder","TraceeEllisRoss","KeyJayandMax","JennaLynnMeowri","trondao","Commanders","Alanqri_fahad","captainmarvel","shirtsthtgohard","InternetH0F","emarrbb","sherryrehman","MontanaBlack","BOHHOT","jenfoxxuwu","oO0Eve0Oo","brithume","khairulaming","KapilMishra_IND","StrangestMedia","valenciacf","utdreport","ClownWorld_","MichelleDBeadle","makaumutua","IndiaHistorypic","eh12__","LeadershipNGA","nuggets","Alyri_tv","ManUnitedZone_","iorimoe_five","TwitterBusiness","bilim_adami","SneakerNews","elizarosewatson","PopCrave","theofficetv","BRSHarish","KimDotcom","Grimezsz","1inch","stargazete","Unexplained","nyjets","NMenonRao","SinghLions","jrisco","safemoon","FavReports","SpicygumL","SeffSaid","TansuYegen","TwitterTurkiye","Lapreviaok_","takuya_hyon","oman1_news","JokesMemesFacts","GettyMuseum","realpfigueiredo","chocofah","hotlygirl","t_adabi","MeshalSari","oricon","FiveThirtyEight","Saiiyansam","CiervoKing","realFFK","videonet_","JanelleMonae","FortniteBR","Trendulkar","haneame_cos","TwitterEng","felipeprior","JimCantore","Diegor_Barros","Buccaneers","Quicktake","MASAI_Fischers","ALFINETEI","dwitasaridwita","MTVMusicUK","hamagohan_r","MarvelLatin","FalleNCS","TwitterKorea","XBIZ","DiwaPh","_IDVL","2em2e","60Minutes","squishubunny","JayGlazer","g0ulaarte","puppiwi","KaiCenat","TheToriant","KateMillerGems","NurkoNicole","mischiefanimals","M2MPD","i9_76","DiscoverMag","RicardoBSalinas","eisincera","SECNetwork","RuPaulsDragRace","suisei_hosimati","unusual_whales","SeriesBrasil","LILBTHEBASEDGOD","FootyHumour","kimpaim","ajplus","youtooz","YaOnlyLivvOnce","Ali_Albukhaiti","Forsan_71","OTerrifying","HelloVacay","bbcrussian","joncoopertweets","espnmma","BTC_Archive","TawakkolKarman","Christian_Sty","RamsNFL","MiamiDolphins","GameOverGreggy","PFF","maisbrasil","pmarca","ycombinator","Colts","mshambuliaji","iKONIC_143","Tim_Onlyfans","OfficialPDPNig","Mkktarat","ankara_kusu","EXOGlobal","SarahHuckabee","JDaIey","khalidjassem74","IIAdeb","ManyVids","redditSpacePorn","disclosetv","zachclayton","Espngreeny","gabrielleydon","brian_armstrong","ginacarano","stanzaselvaggia","mmpadellan","tyomateee2","MejoresTwits","TurkiShalhoub","WakeupPeopIe","mimsy","aramco","kigogo2014","PhillyD","emiliaclarke","majornelson","ESLCS","uri11_27","1pcornwell","BunnyAyu","Toptap_jirakit","bstvlive","sikorskiradek","Fresh","mtvgeordieshore","greta","MrAndyNgo","Sehtkk","motivational","MedvedevRussiaE","chefjoseandres","Katyuskamoonfox","trpresidency","TopSaudiNews2","AflamWorld","delsasolorzano","akaihaato","yoxrgravity","jeonghee1414","LibardoIsaza","KrackinasssKeyy","chiitan7407","pang3pongsow","TheAmberNova","natgeowild","StrangerNews11","48FF_","chicagotribune","TO_yumemarucas","ThomasSowell","thebrittanyxoxo","mtvema","MVRNoticias","AZCardinals","AgentsofSHIELD","MichaelBucwa","xCryboy","rcavada","PTI","Project_Veritas","heartt_6","Trafico_ZMG","LIVEpositivity","andreitaxgar","ShiinaBR","Jessewelle","TheHoopCentral","Merryweatherey","EnglandRugby","GenFlynn","AlNassrFC_EN","goal_f9","KSAEJ3","EnsedeCiencia","Nightline","ClayTravis","Klm_91","JackPhan","Cernovich","chunmomo0127","luculucuaaan","shouldhaveaduck","Sibi_Sathyaraj","GeorgiaFootball","caroandlace","Canucks","funder","alinaa_rose9","ONEChampionship","caseykfrey","futbolarena","TakerMetal","microsiervos","TheCryptoLark","lamegff","sweetroad5","SoldadoFerid0","ABCPolitics","chargers","peartunwarat","ladyfrengie","DJCLUE","BungieHelp","itsJeffTiedrich","Babu_Bhaiyaa","1AGH_","Rainmaker1973","brandi_love","Benioff","WeAreMessi","dawallach","TsuyoshiWood","iyiTriloji","rusherkingg","PrinceKaybee_SA","Ghrebaa","mvngokitty","UseTips","ValorLeaks","i_5mile","MollyJongFast","paufrancolopez","LizbethEden","RWMaloneMD","Lacoste","peta","ZubyMusic","MikaPikaZo","revistaoeste","ayachan0619","colbertlateshow","ai_hongo_","eskitvitler","TwitterGaming","NuBraveIN","mtvitalia","biya1024","romi_chase","NFLonCBS","NYCTSubway","alphaINTEL","NowHipHopNews_","teninchtopx","misskatie2021","EHSANFAKEEH","Mateopromo92","lukecombs","ie_76","yenisafak","MeiRiDaZuoZhan","muselk","LilReese300","BoredApeYC","SakimiChanArt","foreplay","TVGuide","_frame1","yoneyamai","woonomic","TweetsOfCats","Bitboy_Crypto","iraqfpg","nikkibenz","TheNBACentral","JuliaaBurch","egymeme11","NCIS_CBS","iamvictoryaa","LUFC","MZHemingway","JeffPassan","TwitterMktg","Genshinmem","ID_AA_Carmack","nexta_tv","NEWS_MAKER","thegameawards","edermilitao","Rap","saidercan","AlMayadeenLive","dezeen","Titans","BillKristol","JohnStossel","Charming24N","NawafNetwork","OrionDepp","bambiblacks_uk","NCMKSA","_missdridri","literlandweb1","Sora_Sakurai","JohnPiper","ExoticaSlim","ThisIsKyleR","crockpics","Kuukow002","carlosvecchio","1iTariq","FlavioDino","FieldYates","eLDeeTheDon","alniopulesitivt","whyyoutouzhele","daddys_anon","NRGgg","AlmiraCrypto","bernabephoto","iihtishamm","NFLFantasy","a7kie","waleeddhafeeri","Facwow2","PITERALBEIRO","sozmuhendisi","FutSheriff","Advait_Prashant","emilywillisxoxo","Romi_Rain","Scaramucci","lindseyvonn","LeadToday","TheKenFolk","flightradar24","BuckSexton","1abo_turky","GrantCardone","ShathaSa3eed","lawandordertv","lavecinarubia","Juezcentral","peachyboy25","UglyGod"],["Verified","Verified","Verified","Business","Verified","Business","Verified","Business","Verified","Verified","Verified","Verified","Government","Verified","Verified","Verified","Verified","Business","Verified","Business","Business","Business","Business","Verified","Verified","Business","Verified","Regular","Verified","Regular","Business","Verified","Verified","Regular","Verified","Business","Verified","Verified","Business","Verified","Verified","Verified","Verified","Verified","Government","Verified","Business","Government","Verified","Government","Verified","Business","Verified","Business","Verified","Verified","Verified","Verified","Business","Verified","Verified","Business","Verified","Business","Verified","Business","Regular","Regular","Verified","Business","Verified","Verified","Verified","Business","Regular","Verified","Regular","Verified","Business","Business","Business","Business","Verified","Verified","Verified","Verified","Regular","Regular","Verified","Verified","Verified","Verified","Business","Verified","Verified","Regular","Verified","Verified","Verified","Verified","Verified","Business","Verified","Verified","Verified","Verified","Verified","Verified","Business","Regular","Business","Verified","Verified","Business","Verified","Verified","Business","Business","Business","Business","Business","Regular","Business","Government","Business","Regular","Business","Verified","Verified","Business","Verified","Verified","Verified","Government","Verified","Verified","Regular","Verified","Business","Verified","Regular","Verified","Regular","Regular","Business","Regular","Regular","Verified","Verified","Verified","Verified","Verified","Verified","Verified","Regular","Regular","Verified","Regular","Regular","Verified","Verified","Regular","Business","Verified","Verified","Verified","Business","Business","Regular","Verified","Business","Business","Verified","Regular","Regular","Business","Business","Regular","Verified","Business","Regular","Business","Verified","Regular","Business","Verified","Verified","Regular","Verified","Regular","Verified","Verified","Regular","Verified","Business","Verified","Regular","Verified","Business","Verified","Business","Regular","Verified","Verified","Verified","Regular","Verified","Verified","Regular","Verified","Verified","Verified","Verified","Regular","Verified","Business","Business","Regular","Verified","Verified","Verified","Verified","Verified","Regular","Verified","Verified","Business","Business","Regular","Business","Business","Regular","Regular","Verified","Verified","Verified","Verified","Regular","Verified","Verified","Government","Business","Business","Verified","Verified","Verified","Business","Verified","Verified","Verified","Business","Verified","Business","Verified","Verified","Regular","Verified","Verified","Regular","Business","Verified","Regular","Business","Business","Business","Verified","Verified","Verified","Verified","Regular","Verified","Verified","Business","Verified","Business","Regular","Verified","Business","Verified","Regular","Verified","Business","Regular","Regular","Business","Verified","Business","Verified","Verified","Regular","Verified","Verified","Regular","Verified","Verified","Business","Verified","Government","Business","Verified","Business","Verified","Business","Business","Verified","Regular","Verified","Verified","Verified","Regular","Verified","Verified","Verified","Regular","Verified","Regular","Business","Regular","Regular","Regular","Business","Verified","Business","Business","Verified","Regular","Business","Business","Verified","Business","Regular","Government","Verified","Regular","Regular","Regular","Regular","Regular","Business","Regular","Verified","Business","Verified","Verified","Verified","Regular","Verified","Verified","Business","Verified","Regular","Regular","Regular","Business","Verified","Verified","Business","Verified","Regular","Regular","Regular","Verified","Regular","Verified","Regular","Verified","Verified","Verified","Verified","Business","Verified","Verified","Verified","Regular","Verified","Verified","Business","Regular","Regular","Business","Verified","Verified","Verified","Regular","Business","Verified","Regular","Business","Business","Verified","Regular","Verified","Regular","Verified","Business","Verified","Regular","Verified","Regular","Business","Business","Verified","Regular","Regular","Business","Verified","Verified","Regular","Business","Business","Regular","Verified","Regular","Regular","Verified","Regular","Regular","Verified","Regular","Regular","Business","Regular","Business","Regular","Business","Regular","Regular","Regular","Regular","Verified","Business","Business","Verified","Verified","Regular","Verified","Verified","Regular","Regular","Regular","Regular","Regular","Verified","Regular","Verified","Business","Business","Regular","Verified","Verified","Verified","Regular","Regular","Verified","Verified","Verified","Business","Regular","Regular","Business","Regular","Business","Regular","Regular","Regular","Business","Verified","Regular","Verified","Verified","Regular","Regular","Verified","Regular","Business","Regular","Verified","Verified","Regular","Regular","Regular","Business","Business","Regular","Business","Regular","Verified","Regular","Regular","Business","Regular","Regular","Regular","Verified","Verified","Verified","Business","Regular","Regular","Regular","Regular","Business","Verified","Verified","Verified","Verified","Regular","Verified","Verified","Business","Verified","Regular","Regular","Regular","Regular","Regular","Business","Business","Business","Regular","Regular","Regular","Regular","Verified","Verified","Verified","Regular","Regular","Regular","Verified","Regular","Regular","Regular","Regular","Business","Verified","Verified","Business","Regular","Verified","Verified","Business","Business","Verified","Verified","Regular","Verified","Regular","Regular","Verified","Verified","Regular","Verified","Regular","Regular","Verified","Verified","Regular","Regular","Business","Business","Verified","Regular","Verified","Verified","Verified","Regular","Verified","Verified","Regular","Regular","Verified","Regular","Verified","Verified","Business","Verified","Regular","Regular","Business","Regular","Verified","Regular","Verified","Verified","Regular","Regular","Regular","Verified","Regular","Regular","Regular","Verified","Regular","Regular","Business","Verified","Verified","Verified","Regular","Regular","Verified","Regular","Business","Regular","Regular","Verified","Verified","Business","Regular","Business","Business","Regular","Business","Regular","Regular","Regular","Verified","Verified","Regular","Verified","Verified","Verified","Regular","Verified","Regular","Business","Regular","Regular","Verified","Verified","Regular","Regular","Business","Business","Regular","Regular","Verified","Business","Regular","Regular","Regular","Regular","Business","Regular","Verified","Verified","Business","Business","Regular","Business","Verified","Verified","Verified","Verified","Regular","Regular","Regular","Verified","Business","Regular","Verified","Regular","Regular","Business","Regular","Regular","Regular","Regular","Regular","Business","Business","Regular","Regular","Verified","Regular","Verified","Regular","Verified","Regular","Business","Regular","Verified","Regular","Business","Business","Verified","Regular","Regular","Business","Regular","Verified","Verified","Business","Verified","Regular","Regular","Regular","Business","Regular","Verified","Regular","Regular","Verified","Regular","Regular","Regular","Regular","Business","Regular","Verified","Verified","Regular","Business","Business","Regular","Verified","Verified","Verified","Regular","Regular","Business","Verified","Verified","Verified","Verified","Regular","Regular","Business","Verified","Business","Regular","Verified","Regular","Business","Business","Verified","Verified","Regular","Verified","Regular","Business","Regular","Regular","Regular","Verified","Regular","Regular","Regular","Verified","Verified","Verified","Regular","Verified","Regular","Regular","Verified","Verified","Regular","Verified","Verified","Verified","Verified","Regular","Regular","Verified","Regular","Regular","Business","Verified","Verified","Regular","Verified","Business","Regular","Verified","Regular","Regular","Regular","Verified","Verified","Business","Verified","Verified","Regular","Regular","Government","Verified","Regular","Government","Regular","Regular","Verified","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Business","Regular","Regular","Business","Regular","Regular","Regular","Business","Regular","Regular","Business","Regular","Regular","Verified","Business","Regular","Regular","Regular","Regular","Regular","Verified","Verified","Regular","Verified","Business","Regular","Verified","Regular","Regular","Regular","Business","Verified","Regular","Verified","Verified","Regular","Regular","Regular","Verified","Business","Regular","Business","Verified","Regular","Business","Verified","Verified","Regular","Verified","Verified","Regular","Regular","Regular","Business","Business","Regular","Regular","Verified","Business","Regular","Regular","Regular","Regular","Regular","Verified","Regular","Verified","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Verified","Regular","Regular","Regular","Business","Verified","Verified","Regular","Regular","Regular","Business","Regular","Regular","Business","Regular","Business","Regular","Regular","Business","Verified","Regular","Regular","Regular","Regular","Verified","Regular","Verified","Regular","Business","Regular","Verified","Regular","Business","Verified","Regular","Business","Regular","Regular","Regular","Regular","Verified","Regular","Verified","Regular","Regular","Regular","Business","Regular","Business","Verified","Verified","Business","Regular","Verified","Verified","Regular","Business","Verified","Business","Verified","Regular","Regular","Business","Verified","Verified","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Verified","Verified","Regular","Regular","Regular","Regular","Verified","Regular","Government","Verified","Verified","Regular","Regular","Regular","Business","Regular","Verified","Verified","Business","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Regular","Verified","Verified","Verified","Regular","Regular","Business","Verified","Regular","Verified","Regular","Business","Verified","Regular","Regular","Verified"],["133M","51M","47M","42M","29M","29M","25M","22M","21M","21M","21M","20M","20M","20M","19M","17M","15M","15M","14M","14M","14M","14M","14M","14M","13M","13M","13M","12M","12M","12M","12M","12M","11M","11M","11M","11M","11M","11M","10M","10M","10M","10M","10M","10M","10M","10M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","9M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","8M","7M","7M","7M","7M","7M","7M","7M","7M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","6M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","5M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","4M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","3M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","2M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M","1M"],["2022-11-10","2023-03-10","2023-03-03","2022-12-19","2023-01-04","2023-03-22","2023-03-24","2023-02-08","2023-02-24","2022-11-10","2023-03-16","2023-02-18","2023-03-16","2022-12-20","2022-11-10","2023-01-08","2023-03-16","2023-01-19","2023-02-23","2022-12-20","2023-02-10","2022-12-06","2022-12-20","2023-01-19","2023-02-10","2023-01-19","2023-03-19","2023-02-11","2023-02-15","2023-02-14","2023-01-19","2022-12-20","2023-03-24","2022-12-23","2023-03-21","2023-03-18","2023-03-04","2022-12-22","2023-02-04","2023-02-18","2023-01-14","2023-03-21","2023-03-23","2023-01-26","2023-03-18","2023-03-21","2022-12-20","2023-03-17","2022-12-29","2023-02-23","2023-03-20","2023-01-19","2022-12-16","2023-01-19","2022-12-29","2023-03-23","2023-03-24","2023-03-23","2022-12-20","2023-02-10","2023-02-16","2022-12-20","2023-03-08","2023-01-10","2023-03-02","2022-12-20","2023-02-16","2023-02-16","2022-11-10","2023-02-09","2023-02-24","2022-12-17","2023-01-21","2022-12-16","2022-12-20","2023-03-18","2023-03-17","2023-02-25","2022-12-20","2023-01-19","2023-02-25","2023-03-07","2022-12-20","2023-03-24","2022-11-28","2023-03-17","2023-03-03","2023-02-14","2023-01-14","2023-03-22","2023-01-26","2023-01-15","2022-12-20","2022-12-20","2022-11-10","2023-02-11","2023-03-09","2023-03-16","2023-03-09","2023-03-16","2023-02-26","2023-01-28","2022-12-28","2023-03-22","2022-12-22","2022-12-23","2022-12-15","2023-03-16","2022-12-20","2022-12-22","2022-12-20","2022-12-30","2023-03-22","2022-12-20","2023-03-21","2023-03-09","2023-01-10","2023-03-21","2023-03-20","2022-12-20","2022-12-20","2023-02-14","2023-01-09","2022-12-23","2022-12-20","2023-01-14","2023-03-18","2023-02-10","2023-03-24","2023-01-09","2022-12-20","2022-12-22","2023-03-11","2023-03-21","2022-12-20","2023-02-15","2023-03-15","2022-12-22","2023-01-09","2022-11-10","2022-11-13","2023-03-17","2022-11-13","2023-03-17","2022-12-16","2023-01-27","2023-02-06","2023-02-24","2023-02-15","2022-11-10","2023-02-14","2022-12-22","2023-01-27","2023-02-23","2022-11-13","2023-03-17","2022-12-17","2023-02-24","2023-03-25","2023-03-22","2023-03-11","2023-02-05","2022-12-19","2023-03-22","2023-02-11","2023-03-18","2023-02-04","2022-12-20","2023-01-13","2023-03-25","2023-01-09","2023-01-09","2022-12-16","2023-02-14","2023-02-14","2022-12-19","2022-12-20","2023-03-24","2023-03-17","2022-12-20","2023-02-14","2022-12-20","2023-01-13","2023-01-07","2023-02-08","2022-12-20","2023-03-21","2023-03-17","2023-01-13","2023-03-25","2023-03-21","2023-02-14","2022-12-28","2023-03-20","2022-12-20","2023-03-03","2022-12-31","2023-03-05","2022-12-19","2022-12-23","2022-12-22","2023-01-15","2023-03-22","2023-02-25","2023-03-24","2023-02-17","2023-02-19","2023-01-06","2022-11-13","2023-01-10","2022-12-16","2023-03-23","2023-01-14","2023-01-28","2022-12-29","2023-02-13","2023-02-08","2023-03-24","2023-03-17","2022-12-26","2023-01-19","2023-03-10","2023-01-24","2023-03-22","2023-03-03","2023-01-15","2022-12-20","2023-01-09","2023-02-14","2022-12-20","2023-01-10","2023-01-11","2022-12-20","2023-02-18","2023-03-23","2023-01-13","2023-02-16","2022-12-17","2023-01-19","2023-01-14","2023-02-14","2023-01-24","2023-02-16","2023-02-23","2023-03-22","2023-01-10","2023-02-10","2022-12-22","2022-12-20","2022-12-29","2023-03-22","2023-03-10","2022-12-20","2023-03-24","2023-02-16","2023-03-17","2023-03-17","2023-02-11","2023-03-17","2023-01-09","2023-01-11","2023-03-03","2022-12-20","2023-01-19","2022-12-20","2023-03-17","2023-01-23","2023-03-24","2023-02-02","2022-11-13","2023-01-13","2022-12-30","2022-12-20","2023-02-10","2023-03-13","2023-01-11","2022-12-22","2023-03-17","2023-03-23","2022-11-13","2023-02-11","2023-01-09","2023-03-22","2022-11-13","2023-01-09","2023-02-26","2022-12-20","2023-02-14","2023-03-22","2023-01-21","2023-02-10","2023-03-25","2023-02-05","2022-11-10","2023-01-11","2022-12-20","2023-03-22","2023-03-18","2023-01-10","2022-11-11","2022-12-20","2023-01-28","2023-01-09","2022-12-30","2023-02-26","2023-03-25","2023-03-17","2023-02-22","2022-12-16","2023-02-02","2023-02-10","2023-02-14","2022-11-10","2022-11-11","2023-03-09","2023-02-18","2023-01-19","2022-11-17","2022-12-22","2022-11-13","2023-01-09","2023-03-23","2023-03-04","2022-12-16","2022-12-16","2023-02-14","2022-12-20","2022-12-20","2022-12-14","2023-01-10","2023-03-16","2023-02-08","2023-03-22","2023-02-23","2023-01-20","2023-03-08","2022-12-31","2022-11-13","2023-02-08","2023-02-15","2022-12-31","2022-12-30","2023-03-09","2023-02-11","2023-02-18","2023-03-15","2022-12-17","2023-03-21","2022-12-20","2023-03-17","2022-12-28","2023-03-25","2023-03-21","2022-12-21","2023-01-23","2023-02-10","2022-12-20","2023-03-21","2022-11-10","2022-11-10","2022-12-22","2023-01-05","2022-12-17","2023-03-21","2023-03-22","2023-02-24","2023-03-14","2023-02-10","2022-12-25","2022-12-20","2023-02-24","2023-03-18","2023-01-20","2023-03-04","2022-11-10","2022-11-10","2023-01-09","2022-11-10","2023-01-13","2023-03-16","2022-12-30","2023-02-24","2023-03-25","2023-02-11","2023-01-09","2023-01-14","2023-03-08","2023-03-17","2023-01-05","2022-12-14","2022-11-13","2023-01-22","2023-03-22","2023-02-24","2023-01-10","2022-11-10","2022-11-10","2022-12-28","2023-03-15","2023-01-10","2022-12-27","2023-03-14","2023-02-22","2023-02-18","2022-12-20","2023-03-16","2022-12-30","2022-11-13","2023-01-10","2022-12-20","2023-03-15","2023-01-20","2023-03-08","2023-03-24","2023-03-03","2023-02-16","2023-03-22","2023-02-10","2022-12-30","2022-11-10","2023-03-18","2022-11-11","2022-12-19","2022-11-10","2022-12-20","2022-11-13","2022-11-10","2022-11-13","2022-12-30","2022-11-11","2023-01-10","2022-12-19","2022-12-20","2023-02-24","2022-12-19","2023-02-11","2023-02-17","2023-03-22","2023-02-14","2023-02-11","2023-02-11","2022-12-22","2023-01-21","2023-02-10","2023-02-17","2022-12-20","2022-12-20","2022-11-11","2023-03-21","2023-03-01","2023-03-17","2023-02-24","2022-12-31","2023-02-10","2022-12-25","2023-01-20","2023-01-19","2023-02-11","2023-02-23","2023-01-10","2023-03-08","2023-01-31","2023-02-01","2023-02-14","2022-11-13","2023-03-25","2023-03-09","2022-11-10","2023-01-15","2023-01-10","2023-02-02","2023-03-17","2023-01-19","2023-03-17","2023-01-10","2023-03-04","2022-11-10","2023-01-15","2022-11-10","2022-11-10","2023-03-22","2022-12-20","2023-03-17","2022-11-10","2023-03-23","2022-11-11","2022-12-23","2023-02-11","2022-11-13","2023-02-09","2022-12-16","2023-03-15","2022-12-16","2023-02-17","2023-02-06","2023-03-22","2022-12-20","2023-01-09","2023-02-07","2022-12-16","2022-11-13","2023-03-08","2023-03-24","2023-03-13","2023-03-16","2023-03-22","2023-03-13","2023-03-16","2023-01-05","2022-12-20","2022-12-16","2022-12-20","2023-03-24","2023-02-14","2022-11-11","2022-11-10","2023-01-09","2022-12-20","2023-03-15","2023-02-28","2023-03-02","2023-03-22","2022-12-22","2023-03-17","2023-02-04","2023-03-21","2023-03-17","2022-11-10","2023-01-26","2023-02-25","2022-11-10","2022-12-17","2023-03-04","2022-11-10","2023-01-10","2023-02-10","2023-03-23","2023-03-23","2022-12-16","2023-03-11","2023-01-20","2023-01-09","2023-01-10","2023-02-24","2023-03-14","2023-03-17","2023-02-10","2023-03-24","2023-01-21","2023-03-09","2023-02-06","2023-03-23","2023-03-07","2022-11-10","2022-12-31","2023-01-12","2023-03-04","2023-03-04","2022-11-11","2023-03-13","2022-12-20","2023-02-11","2023-03-23","2023-01-11","2023-03-16","2022-12-30","2022-12-22","2023-03-21","2023-01-13","2023-03-23","2023-01-21","2023-01-19","2022-11-10","2023-02-24","2022-11-11","2023-02-05","2023-02-14","2022-11-13","2023-02-24","2023-01-09","2023-03-24","2023-03-24","2023-02-18","2023-02-14","2023-03-14","2022-11-10","2022-11-10","2023-03-24","2023-03-24","2022-11-13","2023-03-14","2023-02-14","2023-03-03","2023-02-11","2023-02-04","2022-12-20","2022-12-28","2023-01-28","2023-02-22","2023-01-21","2022-11-15","2023-03-16","2023-03-07","2023-01-31","2023-01-19","2023-03-24","2023-03-20","2022-12-02","2022-12-20","2022-11-10","2023-03-22","2023-01-10","2022-11-11","2022-12-20","2022-12-22","2022-11-10","2023-01-06","2023-01-14","2023-02-10","2023-02-07","2022-11-10","2023-02-01","2022-12-14","2023-03-22","2023-03-13","2023-02-14","2023-02-11","2022-12-31","2022-11-10","2023-01-05","2022-12-06","2023-03-04","2023-01-28","2022-12-16","2023-02-11","2022-11-10","2022-11-13","2023-01-18","2022-12-20","2023-02-24","2023-03-24","2023-01-27","2022-11-10","2022-12-20","2023-02-16","2022-12-22","2022-12-22","2023-03-10","2023-01-10","2023-02-10","2023-01-09","2023-03-13","2023-03-16","2023-03-18","2023-01-27","2022-12-30","2022-11-14","2023-02-10","2022-12-22","2022-12-30","2023-03-15","2023-01-14","2022-11-13","2023-03-18","2023-03-16","2022-12-17","2023-01-14","2023-03-22","2023-02-24","2023-03-15","2023-02-11","2022-12-20","2022-11-10","2023-03-17","2023-03-23","2023-01-11","2023-02-11","2022-11-10","2023-02-15","2023-01-14","2023-01-19","2023-03-08","2023-03-16","2022-12-01","2023-01-09","2022-12-20","2023-01-14","2023-03-18","2023-03-15","2022-12-20","2023-02-14","2022-12-16","2023-02-24","2023-01-10","2023-01-24","2022-11-14","2022-11-13","2023-03-04","2022-12-20","2022-12-20","2023-03-22","2023-02-14","2022-11-13","2023-02-16","2023-01-18","2023-03-17","2022-12-22","2023-02-10","2022-12-13","2023-02-16","2023-01-27","2023-03-16","2023-01-13","2022-12-20","2022-12-19","2023-03-22","2023-01-31","2023-03-16","2023-01-11","2022-11-10","2022-11-11","2022-11-10","2022-11-11","2022-12-17","2022-11-10","2023-03-25","2022-12-15","2022-11-10","2023-03-19","2023-03-17","2022-12-20","2022-11-10","2023-03-17","2022-12-01","2023-01-09","2023-01-09","2023-03-24","2023-03-09","2022-12-30","2022-11-10","2023-03-07","2023-01-10","2023-01-11","2023-03-24","2022-11-10","2023-03-21","2023-02-18","2023-02-23","2023-02-14","2023-01-26","2022-11-10","2023-03-15","2023-02-26","2023-03-05","2022-12-16","2023-02-10","2023-03-25","2023-03-22","2022-11-11","2023-01-19","2022-12-17","2023-03-22","2022-12-29","2023-02-06","2023-03-22","2023-01-14","2023-02-14","2022-11-10","2023-03-17","2022-11-14","2023-01-19","2023-03-04","2023-02-25","2023-03-15","2023-01-14","2023-01-13","2022-12-16","2023-03-24","2023-02-23","2023-03-18","2022-12-31","2023-01-10","2023-01-05","2022-12-30","2023-02-04","2022-12-30","2023-03-22","2023-02-14","2023-01-31","2023-03-18","2022-11-13","2022-11-13","2023-01-20","2023-03-04","2023-03-24","2023-03-22","2023-03-15","2022-12-04","2023-03-04","2023-03-17","2022-11-11","2023-01-11","2023-02-14","2023-03-04","2023-02-26","2023-01-14","2022-12-16","2022-11-10","2023-01-10","2023-03-17","2023-01-10","2022-12-20","2023-03-22","2023-02-11","2023-01-28","2022-12-20","2022-12-17","2022-11-13","2023-03-22","2022-11-10","2023-03-12","2023-03-22","2023-02-10","2022-11-10","2023-03-08","2023-02-17","2023-01-25","2023-03-09","2023-01-28","2023-02-14","2023-03-17","2022-12-19","2023-02-10","2023-02-04","2023-02-10","2023-03-23","2023-01-20","2023-03-24","2023-02-28","2023-02-18","2023-02-15","2022-11-11","2023-03-16","2022-11-10","2022-11-10","2023-02-22","2023-03-03","2023-03-16","2023-02-18","2023-02-14","2023-01-24","2022-11-10","2023-01-13","2023-02-14","2022-12-19","2023-01-09","2023-03-24","2023-02-26","2023-03-25","2023-03-13","2023-03-03","2023-02-16","2022-12-16","2023-02-10","2022-12-22","2023-01-19","2023-03-17","2023-03-16","2023-03-02","2023-01-27","2023-03-22","2023-03-22","2023-03-24","2022-11-11","2023-01-11","2022-11-10","2022-11-13","2023-01-14","2023-03-02","2023-01-19","2022-12-16","2023-02-22","2022-12-14","2023-02-03","2023-01-13","2023-02-23","2023-01-22","2022-12-19","2023-01-21","2023-02-28","2023-01-19","2023-02-14","2023-01-10","2023-03-17","2022-11-13","2022-12-20","2023-03-13","2023-02-04","2023-01-19","2023-01-20","2022-12-01","2023-03-14","2023-03-04","2023-03-04","2023-03-12","2023-03-08","2023-01-25","2023-03-11","2023-01-31","2023-02-10","2023-02-03","2022-12-06","2023-03-15","2023-03-22","2023-01-27","2023-01-19","2022-11-10","2022-12-22","2023-02-14","2023-03-03","2023-02-28","2022-11-10","2023-02-11","2022-12-20","2022-11-10","2023-02-01","2023-02-18","2023-03-22","2023-01-19","2022-12-22","2023-03-09","2023-03-09","2022-11-11","2023-02-02","2023-01-10","2023-02-17","2023-03-21","2023-01-13","2023-03-11","2023-01-09","2023-02-27","2023-02-21","2023-03-11","2023-02-28","2023-03-02","2022-11-11","2023-02-11","2022-11-20","2023-03-10","2023-02-21","2023-03-03","2022-12-12","2022-11-10","2022-12-30","2022-12-16","2023-01-15","2023-01-13","2023-02-22","2023-02-23","2023-03-09","2022-11-13","2023-02-06","2022-11-10","2023-02-28","2022-11-10","2022-12-22","2022-11-10","2023-01-09","2023-03-04","2022-11-10","2023-01-19","2022-11-13","2023-03-22","2023-02-14","2022-11-13","2022-11-11","2022-11-10","2023-01-27","2023-03-02","2022-11-10","2022-11-15","2023-03-16","2023-02-01","2022-12-15","2023-01-13","2023-02-01","2022-12-20","2023-02-26","2023-02-16","2022-11-30","2023-01-05"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>Username<\/th>\n      <th>Old Status<\/th>\n      <th># Followers<\/th>\n      <th>Joined Blue On<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false}},"evals":[],"jsHooks":[]}</script>

Of the top-10 most popular accounts on Twitter, only Elon musk is the subscriber. This kinda speaks to the popularity of the service.

![](images/Screenshot%202023-04-03%20at%2012.26.08%20AM.png)

> Twitter accounts with most followers worldwide as of January 2023. All numbers are reported in millions. Source: [Statista](https://www-statista-com.utk.idm.oclc.org/statistics/273172/twitter-accounts-with-the-most-followers-worldwide/).

### How many followers do Blue subscribers have?

For this task, I am going to break down the follower count into smaller groups. Since most Blue subscribers do not have a huge fan following (Elon Musk, again, is an exception), it is a necessary step — else, histograms wouldn’t look relevant.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

<table class=" lightable-paper" style="font-family: &quot;Arial Narrow&quot;, arial, helvetica, sans-serif; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
Number of Followers
</th>
<th style="text-align:left;">
Number of Blue Subscribers
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
0-100
</td>
<td style="text-align:left;">
110K
</td>
</tr>
<tr>
<td style="text-align:left;">
100-1K
</td>
<td style="text-align:left;">
194K
</td>
</tr>
<tr>
<td style="text-align:left;">
1k-10k
</td>
<td style="text-align:left;">
184K
</td>
</tr>
<tr>
<td style="text-align:left;">
10k-100k
</td>
<td style="text-align:left;">
71K
</td>
</tr>
<tr>
<td style="text-align:left;">
100k+
</td>
<td style="text-align:left;">
14K
</td>
</tr>
</tbody>
</table>

Blue seems to be more popular among the less popular accounts on Twitter. That’s interesting.

#### How many accounts have less than 10 followers?

25,550 accounts have fewer than 10 followers. Out of that, 3,480 have zero followers. Who are these people and what’s the value of using Twitter Blue for them? Is it just an act of curiosity — are they simply [early adopters of the service](https://www.harsh17.in/gartner-hype-cycle/)? Or are they in strong defiance of old Twitter, grabbing the opportunity of premium Twitter as soon as it shows up? Maybe they’re just very expensive bots.

Here’s a histogram of number of followers for accounts with fewer than 1,000 followers.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-8-1.png" width="672" />

This is especially interesting because the average number of followers for an active Twitter user is around 159 (in the US). For someone willing to pay extra for a service, you would expect them to be heavy users. You wouldn’t expect them to be lurkers; they’d be core users.

On the other hand, 391 million Twitter accounts have no followers at all.

### Types of Accounts: Business, Government and Society

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-1.png" width="672" />

It feels like almost all the subscribers are Musk fanboys. There are almost no government accounts, very little business accounts and a few celebrities (who probably wanted to try the Blue service).

### How many of the original Blue Subscribers are still using it?

The data has a column called `sub_status` which has this detail.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-10-1.png" width="672" />

### Who left Twitter Blue?

A vast majority of unsubscribers (122,823) are regular users. My guess is they were experimenting with the service as [early adopters](https://www.harsh17.in/gartner-hype-cycle/). 499 of them were verified accounts who later chose not to continue their verification. 21 of the unsubscribers are businesses, and eight of them are government agencies.

Here’s the list of government agencies: TimWattsMP, UNDPEurasia, RepRaulGrijalva, DenverOEM, JoaquinCastrotx, TDEM, SteveScalise, EPAMichaelRegan .

### Conclusion

Twitter Blue, the premium subscription service offered by Twitter, saw a massive surge in subscriber numbers immediately following its announcement. However, this momentum was short-lived, and the rate of new subscriber additions declined significantly, with one exception. In January, something extraordinary happened, which resulted in a notable increase in new subscribers.

It’s worth noting that out of Twitter’s top-10 most followed accounts, only Elon Musk has a Blue account. While some celebrities and businesses do have Blue accounts, they are vastly outnumbered by regular Twitter Blue users.

Interestingly, a significant percentage of the group that initially signed up for Blue has already left the service. However, it’s difficult to determine the exact number, as apparently [Twitter is not actively removing verified badges](https://mashable.com/article/twitter-blue-subscriptions-lower) even after people stop their subscription.

What are your thoughts on this? Do you find these trends surprising or expected? Share your insights in the comments below!

The codes for this project can be found on my [Github](https://github.com/harshvardhaniimi/personal-website/blob/main/content/blog/2023-04-01-twitter-blue/index.Rmd).
