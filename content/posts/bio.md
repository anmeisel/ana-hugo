---
title: "Bio"
date: 2023-08-12T13:25:44+01:00
draft: false
cover:
  image: imgs/PXL_20260613_063520889.jpg
  alt: "full moon at night, view from street with parked cars and street lights"
  caption: "full moon at night, view from street with parked cars and street lights"
disableAnchoredHeadings: true
---

Ana Meisel is a Polish-German web developer based in London, UK, who runs internet art gallery [External Pages](https://externalpages.org/) and is one-third of the research group [Superkilogirls](https://superkilogirls.com/). Interests include Luddism, low-tech, permaculture, and -computing. They recently co-founded a low-resource, sustainability-focused web design, development and consultation studio with Stéphane Lambion called [Subslime](https://subslime.studio/).

#####

#### Currently

###### &nbsp; &nbsp; working with

&nbsp; &nbsp; &nbsp; &nbsp; php, kotlin

#####

###### &nbsp; &nbsp; working on

&nbsp; &nbsp; &nbsp; &nbsp; Researching diy tech cultures during the comecon.. hmu if you have experiences to share ~

#####

###### &nbsp; &nbsp; reading

&nbsp; &nbsp; &nbsp;&nbsp; [Cybernetic Circulation Complex](https://www.versobooks.com/en-gb/products/3109-cybernetic-circulation-complex) by Nick Dyer-Witheford and Alessandra Mularoni
&nbsp; &nbsp; &nbsp;&nbsp; [Dune](https://www.waterstones.com/book/dune/frank-herbert/9780340960196) by Frank Herbert

#####

#####

#####

<div id='londonpermacomputring'>
    <table>
        <tr>
            <td class='webring-prev'><a id='permaPrev'>←</a></td>
            <td class='webring-info'>
                <img src='https://www.iso-bel.computer/static/webring/flower.png'><img src='https://www.iso-bel.computer/static/webring/flower.png'><img src='https://www.iso-bel.computer/static/webring/flower.png'>
                <br>I'm in the <a href='https://london.permacomputing.net/posts/index.html'>London Permacomputing</a> Club!
                <br>We meet on Mondays at 6:30, @ <a href='https://www.openstreetmap.org/way/72032052'>SET Social, Peckham</a><br>
                <span class='webring-links'>
                    <a href='https://garlic.garden/onionring/'>what is this?</a> |
                    <a href='https://permacomputing.net'>wiki</a> |
                    <a href='#' id='permaRandom'>random</a> |
                    <a href='https://www.iso-bel.computer/permacomputingwebring'>index / join</a>
                </span>
            </td>
            <td class='webring-next'><a id='permaNext'>→</a></td>
        </tr>
    </table>

</div>

<script type='module'>
const widget = document.getElementById('londonpermacomputring')
async function getSites() {return await fetch('https://www.iso-bel.computer/static/webring/sites.json');}

const thisSite = window.location.href; //get the url of the site we're currently on
const response = await getSites()
if (!response.ok) {throw new Error(`Response status: ${response.status}`);}
const json = await response.json();
const sites = json.sites
let thisIndex = null;

// go through the site list to see if this site is on it and find its position
for (let i = 0; i < sites.length; i++) {
    if (thisSite.startsWith(sites[i])) { //we use startswith so this will match any subdirectory, users can put the widget on multiple pages
        thisIndex = i;
        break; //when we've found the site, we don't need to search any more, so stop the loop
    }
}

function randomSite() {
    const randomIndex = Math.floor(Math.random() * sites.length);
    widget.querySelector('#permaRandom').href = sites[randomIndex]
}

if (thisIndex == null) {
    widget.innerHTML = `<table><tr><td>This site isn't part of the London Permacomputing webring - yet...</td></tr></table>`;
} else {
    const previousIndex = (thisIndex-1 < 0) ? sites.length-1 : thisIndex-1;
    const nextIndex = (thisIndex+1 >= sites.length) ? 0 : thisIndex+1;
    widget.querySelector('#permaPrev').href = sites[previousIndex]
    widget.querySelector('#permaNext').href = sites[nextIndex]
    widget.querySelector('#permaRandom').addEventListener('click', randomSite)
    randomSite()
}
</script>
<style>
#londonpermacomputring {
    margin: 0 auto;
    padding: 8px;
}

#londonpermacomputring table {
    margin: 0 auto;
    background-color: #ffffff70;
    border: 1px solid #00AA00;
    float: left;
}

#londonpermacomputring img {
    height: 1.5em;
    width: auto;
    display: inline-block;
}

#londonpermacomputring table tr td {
    padding: 10px;
}

#londonpermacomputring.webring-prev {
    text-align: right;
}

#londonpermacomputring.webring-info {
    text-align: center;
}

#londonpermacomputring.webring-next {
    text-align: left;
}

#londonpermacomputring.webring-links {
    font-size: small;
}

table:not(#londonpermacomputring table):not(.post-content #londonpermacomputring table),
.post-content table:not(#londonpermacomputring table) {
  all: initial !important;
  display: table !important;
}
</style>
