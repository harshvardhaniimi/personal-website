---
title: How much do we know about our ancestors?
subtitle: Genome, Geneology and DNA Tests
summary: Genome, Geneology and DNA Tests
author: Harshvardhan
date: '2022-02-03'
slug: how-much-do-we-know-about-our-ancestors
categories:
  - blog
  - life
  - thoughts
tags:
  - blog
  - life
---

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/plotly-binding/plotly.js"></script>
<script src="{{< blogdown/postref >}}index_files/typedarray/typedarray.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/plotly-htmlwidgets-css/plotly-htmlwidgets.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/plotly-main/plotly-latest.min.js"></script>

![Sirius Black’s Family Tree as seen in Harry Potter and the Order of the Phoenix.](Black-Family-Tree.jpg "Sirius Black's Family Tree as seen in Harry Potter and the Order of the Phoenix.")

When I first saw Sirius Black’s family tree in Harry Potter: Prisoner of Azkaban many years ago, I thought of creating my own. I started mapping and went two generations back — that was all that my family remembered. Mummy said, “People remember two generations up and two generations down. That’s it.” I was determined, but there was no obvious way.

Some pundits in our ancestral village had a record of our family tree that we could access after paying a nominal fee. I was excited, but my father was not. “Too much travel for too little information”, he said. I never expected he might be correct.

Around 30 million people have purchased DNA test kits to trace their ancestry. However, there are so many “fine print” details that it is almost impossible to know how accurate they are.

There are two ways to trace ancestry. First is genealogy, where you trace your family tree — like I tried. You build a chart of your parents, grandparents and so on. The graph would grow at an exponential rate in a normal situation: `\(2^n\)`. Currently, I am at `\(n = 0\)`. It’s only me. A generation before me would be two people, `\(2^1\)`; a generation before them would be four people, `\(2^2\)`, and so on.

The second method is to track the genome. My genome constitutes 47 stretches of DNA: 23 pairs of chromosomes from each parent and one mitochondrial DNA from the mother. There are 118 DNA fragments that I got from Papa. When I track my ancestry this way, I get 189 pieces from my grandparents, 260 from my great grandparents and so on.

These genome contributions look promising at first. One hundred eighteen stretches of DNA vs two genealogical parents; 189 stretches of DNA vs four genealogical parents. But what our human mind misses is that the first grows exponentially while the second grows linearly.

<div id="htmlwidget-1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"data":[{"x":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15],"y":[47,118,189,260,331,402,473,544,615,686,757,828,899,970,1041,1112],"text":["generation:  0<br />values:    47<br />type: dna","generation:  1<br />values:   118<br />type: dna","generation:  2<br />values:   189<br />type: dna","generation:  3<br />values:   260<br />type: dna","generation:  4<br />values:   331<br />type: dna","generation:  5<br />values:   402<br />type: dna","generation:  6<br />values:   473<br />type: dna","generation:  7<br />values:   544<br />type: dna","generation:  8<br />values:   615<br />type: dna","generation:  9<br />values:   686<br />type: dna","generation: 10<br />values:   757<br />type: dna","generation: 11<br />values:   828<br />type: dna","generation: 12<br />values:   899<br />type: dna","generation: 13<br />values:   970<br />type: dna","generation: 14<br />values:  1041<br />type: dna","generation: 15<br />values:  1112<br />type: dna"],"type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(248,118,109,1)","dash":"solid"},"hoveron":"points","name":"dna","legendgroup":"dna","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15],"y":[1,2,4,8,16,32,64,128,256,512,1024,2048,4096,8192,16384,32768],"text":["generation:  0<br />values:     1<br />type: geneology","generation:  1<br />values:     2<br />type: geneology","generation:  2<br />values:     4<br />type: geneology","generation:  3<br />values:     8<br />type: geneology","generation:  4<br />values:    16<br />type: geneology","generation:  5<br />values:    32<br />type: geneology","generation:  6<br />values:    64<br />type: geneology","generation:  7<br />values:   128<br />type: geneology","generation:  8<br />values:   256<br />type: geneology","generation:  9<br />values:   512<br />type: geneology","generation: 10<br />values:  1024<br />type: geneology","generation: 11<br />values:  2048<br />type: geneology","generation: 12<br />values:  4096<br />type: geneology","generation: 13<br />values:  8192<br />type: geneology","generation: 14<br />values: 16384<br />type: geneology","generation: 15<br />values: 32768<br />type: geneology"],"type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,191,196,1)","dash":"solid"},"hoveron":"points","name":"geneology","legendgroup":"geneology","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":29.0178497301785,"r":9.29846409298464,"b":46.4923204649232,"l":62.2997094229971},"plot_bgcolor":"rgba(255,255,255,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":18.5969281859693},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.75,15.75],"tickmode":"array","ticktext":["0","5","10","15"],"tickvals":[0,5,10,15],"categoryorder":"array","categoryarray":["0","5","10","15"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":4.64923204649232,"tickwidth":0.845314917544058,"showticklabels":true,"tickfont":{"color":"rgba(0,0,0,1)","family":"","size":13.0178497301785},"tickangle":-0,"showline":true,"linecolor":"rgba(0,0,0,1)","linewidth":0.845314917544058,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.845314917544058,"zeroline":false,"anchor":"y","title":{"text":"<b> Generations <\/b>","font":{"color":"rgba(0,0,0,1)","family":"","size":15.8073889580739}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-1637.35,34406.35],"tickmode":"array","ticktext":["0","10000","20000","30000"],"tickvals":[0,10000,20000,30000],"categoryorder":"array","categoryarray":["0","10000","20000","30000"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":4.64923204649232,"tickwidth":0.845314917544058,"showticklabels":true,"tickfont":{"color":"rgba(0,0,0,1)","family":"","size":13.0178497301785},"tickangle":-0,"showline":true,"linecolor":"rgba(0,0,0,1)","linewidth":0.845314917544058,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.845314917544058,"zeroline":false,"anchor":"x","title":{"text":"<b> Number of Ancestors <\/b>","font":{"color":"rgba(0,0,0,1)","family":"","size":15.8073889580739}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":true,"legend":{"bgcolor":"transparent","bordercolor":"transparent","borderwidth":2.40515390121689,"font":{"color":"rgba(0,0,0,1)","family":"","size":13.0178497301785},"title":{"text":"Ancestry","font":{"color":"rgba(0,0,0,1)","family":"","size":15.8073889580739}}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"11ad24127328f":{"x":{},"y":{},"colour":{},"type":"scatter"}},"cur_data":"11ad24127328f","visdat":{"11ad24127328f":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

We have more information from our genealogy around the tenth generation than our DNA. By the fourteenth generation, the ratio is 16 to 1, meaning many of my ancestors didn’t pass me any DNA at all! So tell me, what do we know from DNA?

Considering my ancestors lived for 60 years on average, that gives me about a thousand years of genetic information from my DNA. But not all of that is reliable. We are 50% certain about our DNA results at just four generations down the line. Using DNA for my ancestry is worse than a coin toss just three hundred years down the line.

With a little extra effort and emotional pleading to Papa, I can get at least five or six generations worth of information. Why bother with DNA ancestry at all?

It is common knowledge DNA can store more information than modern computers. A curious soul would naturally ask: where did we lose this ancestral information? Partly because of mathematics of how DNA transfers happen and how much is retained in the child. Not all info is ancestral, and not all information is copied. It is also presumptuous to assume most of the information in our DNA is about ancestry. Nature doesn’t care about our parents; it cares about survival.

But there is a more interesting answer too. Our DNA gains permanent and non-permanent changes during our lifetime due to our behaviour. We can control what information is passed on to future generations. This recent discovery about epigenetics has revolutionised many aspects of genetic study.

If our behaviours can change the encoding in the fundamental unit of life, imagine the potentialities for the future generation.

If most of DNA information is lost after just a few generations, we should concentrate our efforts on maintaining our own genealogy directory. In the long run, physical directories retains more ancestral information than DNA. We should also take results of genome DNA kits with a pinch of salt. So to answer the question, “how much can we know about ancestors?”. Well, probably not a lot.
