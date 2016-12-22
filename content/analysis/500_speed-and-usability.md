Pagespeed
==============================================

Här kommer jag att mäta hur stor en hemsida är, hur lång tid det tar att ladda, hur användbarheten är och använda mig utav [Google PageSpeed](https://developers.google.com/speed/pagespeed/).  
Mätningarna lokalt gjordes på en ny installation utav Mozilla Firefox version 50.1.0 utan tillägg, på Windows 10 och 100 Mbit neråt som hastighet.  


2016-12-21: När jag kör Google PageSpeed så finns ingen "User experience" längre. 

All rådata finns att läsa här: [Google Sheets](https://docs.google.com/spreadsheets/d/1CYvQOTZzD8SjnxfZP0xJsXJ2FYki45tDI1qDrogMoRQ/)

*Klicka på bilden för att komma till hemsidan.*  

***

#Github
[![Screenshot of Github][github]](https://github.com/)

**Lokala mätningar** | **PageSpeed**
| Sida           | Loadspeed | Pagesize  | Requests | PS Mobile Score | PS Desktop Score |
| :------------- |:---------:| :-------: | :------: | :--------------:| :---------------:|
| Github         | 1.76 sec  |1 579.33 kB|    18    |       66        |         78       |
| Github Pricing | 1.77 sec  |1 384.12 kB|    14    |       66        |         85       |
| Github Explore | 2.00 sec  |1 518.84 kB|    10    |       71        |         80       |

Gemensamt på alla tre sidorna är att PageSpeed rekommenderar att återgärda följande:   
>Eliminate render-blocking JavaScript and CSS in above-the-fold content  
>Optimize images  

På [Github Explore](https://github.com/explore) rekommenderar den också:
>Reduce server response time

Github använder oftast bara en bild till alla skärmstorlekar vilket att kan ta lite onödig bandbredd.   
Här hade det varit smidigare med olika bilder för olika skärmstorlekar istället.  
Google tipsar dock om att komprimera bilderna.



***
#Teamviewer
[![Screenshot of Teamviewer][teamviewer]](https://www.teamviewer.com/en/)

**Lokala mätningar** | **PageSpeed**
| Sida                      | Loadspeed | Pagesize  | Requests | PS Mobile Score | PS Desktop Score |
| :-------------------------|:---------:| :-------: | :------: | :--------------:| :---------------:|
| Teamviewer                | 2.40 sec  |2 752.68 kB|    70    |       44        |         54       |
| Teamviewer Latest Version | 2.95 sec  |3 729.52 kB|    84    |       53        |         61       |
| Teamviewer Security       | 2.73 sec  |2 096.96 kB|    77    |       54        |         70       |

PageSpeed säger:  
>Optimize images  
>Eliminate render-blocking JavaScript and CSS in above-the-fold content  
>Leverage browser caching

På [Teamviewer Latest Version](https://www.teamviewer.com/en/latest-version/) rekommenderar den också:
>Minify JavaScript

Teamviewer har många små bilder men de är dock skalade med CSS när man går över till mobilt.   
Den stora bakgrundsbilden som är på Latest Version hjälper heller inte, då den är 1920x4880 pixlar.  
Jag hade sett att de skulle skalat om bilderna så det passar till skärmstorleken istället för att ladda stora bilder.


***
#Nikon
[![Screenshot of Nikon][nikon]](http://www.nikon.se/sv_SE/)

**Lokala mätningar** | **PageSpeed**
| Sida                 | Loadspeed | Pagesize  | Requests | PS Mobile Score | PS Desktop Score |
| :--------------------|:---------:| :-------: | :------: | :--------------:| :---------------:|
| Nikon                | 6.96 sec  |8 822.46 kB|    123   |       56        |         30       |
| Nikon News and Press | 3.65 sec  |4 338.74 kB|    85    |       59        |         74       |
| Nikon Produkter      | 3.43 sec  |4 052.88 kB|    73    |       62        |         44       |

PageSpeed säger:  
>Optimize images  
>Eliminate render-blocking JavaScript and CSS in above-the-fold content  
>Leverage browser caching

PageSpeed rekommenderar också:
>Prioritize visible content  
>Enable compression  
>Minify JavaScript  
>Minify CSS

Det är bra att de flesta bilderna är små men Nikon har väldigt många bilder, vilket tar på storleken och laddningstiden.
Är ett par banners som skalas med hjälp av CSS.  
Skulle vilja se att Nikon slopar många av bilderna för att göra sidan snabbare och skalar bilderna rätt. Även att de slår på komprimering och minifierar sina scripter.

***
#Nginx
[![Screenshot of Nginx][Nginx]](https://www.nginx.com/)

**Lokala mätningar** | **PageSpeed**
| Sida          | Loadspeed | Pagesize  | Requests | PS Mobile Score | PS Desktop Score |
| :-------------|:---------:| :-------: | :------: | :--------------:| :---------------:|
| Nginx         | 6.08 sec  |7 233.28 kB|    174   |       44        |         57       |
| Nginx Blog    | 4.41 sec  |4 065.74 kB|    146   |       48        |         57       |
| Nginx Company | 4.45 sec  |2 990.96 kB|    144   |       49        |         67       |

PageSpeed säger:  
>Eliminate render-blocking JavaScript and CSS in above-the-fold content  
>Optimize images  
>Enable compression

PageSpeed rekommenderar också:
>Leverage browser caching  
>Prioritize visible content  
>Minify HTML  
>Minify JavaScript  
>Minify CSS

Även om Nginx är en välkänd webbserver, så har de själva inte använt funktionerna som finns. De kan slå igång komprimering och cachning.  
Sen skulle också kunna optimera bilderna samt använda lite minifiering. De har även en support chatt direkt på sidan som ligger och laddar hela tiden, den är lite onödig tycker jag.

***

Vanligaste förbättringsåtgärderna för sidorna jag har valt är att man ska optimera bilderna, minifiera koden, hur länge cachning ska leva och att ladda viktigt javascript först istället föra hela filen. Då man måste vänta tills hela filen är nere innan man kan fortsätta ladda andra saker.

**Hastighets rankning**

* Github
* Teamviewer
* Nikon
* Nginx

Konstigt nog så ligger de redan rankade från snabbast till långsammats. Man märker skillnaden på laddningstiderna beroende på hur många bilder, scripter och hur många CDNs man använder. Saker måste vänta innan man kan fortsätta ladda resten av sidan.

Jag tycker att max tre (3) sekunder är toppgränsen för min del, annars är det märkbart att det känns långsamt. Dock har jag en del tillägg till webbläsarna, så det kanske inte märks så mycket. 
Sidorna jag har testat klarar sig bra för min del, dock beror det på vilken webbläsare man kör. Men som tur så laddar man inte alltid om en sida "rent", man har cache som snabbar upp saker.


***
**Analyserna har jag gjort ensam, har inte medverkat i en grupp.**

[github]: img/analysis/github.png
[teamviewer]: img/analysis/teamviewer.png
[nikon]: img/analysis/nikon.png
[nginx]: img/analysis/nginx.png