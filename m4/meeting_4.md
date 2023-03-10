<div class="header" style="margin-top:0 px;font-size:60%;">სმდაRგ: მესამე შეხვედრა</div>

სტატისტიკურ მონაცემთა დამუშავება და ანალიზი R-ის გარემოში
========================================================
author: დავით სიჭინავა
date: 23 თებერვალი, 2023 წ.
autosize: true
transition: none
css: css/style.css
font-family: 'BPG_upper'




დღევანდელი გეგმა:
========================================================
* (მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში;
* ვიზუალიზაციის ,,ფენოვანი" გრამატიკა;
* `ggplot2` ბიბლიოთეკა;
* პრაქტიკული სამუშაოები;

სანამ დავიწყებდეთ:
========================================================
* დავრწმუნდეთ, რომ ყველა თქვენგანს ჩამოტვირთული აქვს `ggplot2` და `dplyr` ბიბლიოთეკა
* მიუთითეთ სამუშაო დირექტორია (კარგი პრაქტიკა)

სანამ დავიწყებდეთ:
========================================================

```r
library(ggplot2) #ვიზუალიზაცია
library(gapminder) #სავარჯიშო მონაცემები Gapminder-იდან
library(scales) #ბიბლიოთეკა მასშტაბის სწორად მისათითებლად
```

რა არის მონაცემთა კარგი ვიზუალიზაცია?
========================================================
<img src="img/ch-01-minard.png" alt="Drawing" style="width: 1000px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>

რა არის მონაცემთა _ცუდი_ ვიზუალიზაცია?: გემოვნებაზე დაობენ
========================================================
<img src="img/vdqi_clarity.PNG" alt="Drawing" style="width: 1000px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>

რა არის მონაცემთა _ცუდი_ ვიზუალიზაცია?: გემოვნებაზე დაობენ
========================================================
<img src="img/imedi_2.png" alt="Drawing" style="width: 1000px; display: block; margin-left: auto; margin-right: auto;"/>

რა არის მონაცემთა _ცუდი_ ვიზუალიზაცია?: გემოვნებაზე დაობენ
========================================================
<img src="img/cb_1.png" alt="Drawing" style="width: 1000px; display: block; margin-left: auto; margin-right: auto;"/>

რა არის მონაცემთა _ცუდი_ ვიზუალიზაცია?: ცუდი მონაცემები
========================================================
<img src="img/ch-01-democracy-nyt-version.png" alt="Drawing" style="width: 1000px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>

რა არის მონაცემთა _ცუდი_ ვიზუალიზაცია?: ცუდი მონაცემები
========================================================
<img src="img/ch-01-democracy-voeten-version-2.png" alt="Drawing" style="width: 1000px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>


(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში
========================================================
* აჩვენეთ მონაცემები,
* ,,აიძულეთ" მაყურებელი, იფიქროს მონაცემებზე,
* ნუ დაამახინჯებთ იმას, თუ რას ამბობს მონაცემები,
* წარმოადგინეთ ბევრი მონაცემი მცირე სივრცეში
* იყავით თანმიმდევრული
* წაახალისეთ მაყურებლის თვალი, ერთმანეთს სხვადასხვა კატეგორია შეადაროს
* წარმოადგინეთ მონაცემთა დეტალების სხვადასხვა დონე
* იფიქრეთ, თუ რა არის დიაგრამის მიზანი: აღწერა, აღმოჩენა, ტაბულაცია თუ - დეკორაცია
* დიაგრამა ტექსტთან ინტეგრირებული უნდა იყოს


(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: 
========================================================
* მონაცემების მიერ დიაგრამაზე დაკავებული ფართობი მათი რაოდენობრივი პროპორციების შესატყვისი უნდა იყოს
* მოიშველიეთ წარწერები, რათა დიაგრამაზე არსებული გაურკვევლობები ახსნათ

(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: 
========================================================
* აჩვენეთ მონაცემთა ვარიაცია და არა - დიზაინის ვარიაცია


(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: 
========================================================
<img src="img/rubakin-population-farmers-1912.jpg" alt="Drawing" style="width: 700px; display: block; margin-left: auto; margin-right: auto;"/>

(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: ტაფტის ხუთი მცნება
========================================================
* აჩვენეთ მონაცემები,
* გაზარდეთ მონაცემთა და ,,მელნის" შეფარდება,
* წაშალეთ ის ,,მელანი", რომელიც მონაცემებიდან არ მომდინარეობს,
* წაშალეთ უსარგებლო ,,მელანი", რომელიც მონაცემებიდან მომდინარეობს,
* გაუკეთეთ რედაქტირება თქვენს ნამუშევარს


(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: გეშტალტის პრინციპები
========================================================
<img src="img/ch-01-poisson-process-1.png" alt="Drawing" style="width: 500px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>

(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: გეშტალტის პრინციპები
========================================================
ადამიანის თვალი მიდრეკილია, მონაცემებში გარკვეული კანონზომიერებები ,,დაინახოს'' იმის მიუხედავად, არსებობს თუ არა ეს კანონზომიერება
<img src="img/ch-01-gestalt-inferences-horizontal.png" alt="Drawing" style="width: 500px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>

(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: გეშტალტის პრინციპები
========================================================
* სიახლოვე: ერთმანეთთან ახლოს მდებარე მონაცემები ერთმანეთთან დაკავშირებულად გვეჩვენება 
* მსგავსება: გარეგნულად შესადარი მონაცემები მსგავსად მიგვაჩნია
* კავშირი: მონაცემები, რომლებიც ვიზუალურად ერთმანეთთან დაკავშირებულია, მსგავსი გვგონია
* შევსება: ადამიანის თვალი ცდილობს, ნაწილობრივ დაფარული ფიგურები შეავსოს მისთვის ნაცნობი ფორმებით
* ,,საერთო ბედი'' - ელემენტები, რომლებიც თანმიმდევრული ტრაექტორიით ხასიათდებიან, ერთი ელემენტის ნაწილად მოიაზრებიან


(მოკლე) შესავალი მონაცემთა ვიზუალიზაციაში: თუმცა, ტაფტიც ცდება...
========================================================
<img src="img/ch-01-anderson-boxplots-cognitive.png" alt="Drawing" style="width: 500px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>


მონაცემთა ,,ფენოვანი" გრამატიკა
========================================================
<img src="img/phenowanny.jpeg" alt="Drawing" style="width: 500px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [menu.ge](https://www.menu.ge/restaurant/baraka/fenovani-khachapuri_24049.html)</span>


მონაცემთა ,,ფენოვანი" გრამატიკა (Wilkinson, 2005; Wickham, 2008)
========================================================
* მონაცემები და ,,ესთეტიკა'';
* ობიექტები (,,გეომები'');
* სტატისტიკური ტრანსფორმაცია (,,სტატები'');
* მასშტაბი;
* წახნაგები (,,ფაცეტები'')

მონაცემთა ,,ფენოვანი" გრამატიკა (Wilkinson, 2005; Wickham, 2008)
========================================================
<img src="img/ch-03-ggplot-flow-vertical.png" alt="Drawing" style="width: 500px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: [socviz.co](https://socviz.co)</span>


მონაცემთა ,,ფენოვანი" გრამატიკა: `ggplot2`
========================================================

```r
data(gapminder)

p <- ggplot(gapminder)

p
```

მონაცემთა ,,ფენოვანი" გრამატიკა: `ggplot2`
========================================================
* რა თქმა უნდა, როგორც ყველაფერი, ისე დიაგრამა `ggplot2` გარემოში ობიექტს წარმოადგენს
* ,,ესთეტიკის'' კარტირება ხდება `aes()` ფუნქციის მეშვეობით.
* ,,ესთეტიკა'' აჩვენებს, თუ რა __ცვლადები__ უნდა იქნას გამოყენებული დიაგრამაში


მონაცემთა ,,ფენოვანი" გრამატიკა: `ggplot2`
========================================================

```r
p <- ggplot(data = gapminder,
            mapping = aes(x = gdpPercap,
                          y = lifeExp))

p + geom_point()
```

მონაცემთა ,,ფენოვანი" გრამატიკა: `ggplot2`
========================================================
* მივუთითოთ, თუ რას ვყენებთ მონაცემებად,
* მივუთითოთ, მონაცემთა შორის კავშირი,
* მივუთითოთ, თუ რა ფორმით გვსურს ამ კავშირის გამოსახვა
* ეს ყველაფერი _ფენების_ სახით დავამატოთ დიაგრამას,
* გამოვიყენოთ დამატებითი ფუნქციები მასშტაბის, წარწერების, ღერძების და ა.შ. მანიპულირებისთვის

მონაცემთა ,,ფენოვანი" გრამატიკა: `tidy` მონაცემები (Codd, 1990; Wickham, 2010)
========================================================
* თითოეული ცვლადი მოცემულია ცალკე სვეტში,
* თითოეული ჩანაწერი მოცემულია ცალკე რიგში,
* ჩანაწერის თითოეული ტიპი ქმნის ცხრილს,

<img src="img/untidy_pew.png" alt="Drawing" style="width: 700px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: Wickham, 2010</span>

მონაცემთა ,,ფენოვანი" გრამატიკა: `tidy` მონაცემები (Codd, 1990; Wickham, 2010)
========================================================
<img src="img/tidy_pew.png" alt="Drawing" style="width: 700px; display: block; margin-left: auto; margin-right: auto;"/>
<span style="width: 100%;text-align: center; font-size:10px">წყარო: Wickham, 2010</span>

მონაცემთა ,,ფენოვანი" გრამატიკა: ,,ესთეტიკა''
========================================================
* `position`: პოზიცია,
* `color`: ,,გარეთა ფერი",
* `fill`: ,,შიდა ფერი",
* `shape`: მარკერების ფორმა,
* `linetype`: წრფის ტიპი,
* `size`: ზომა

მონაცემთა ,,ფენოვანი" გრამატიკა: ,,სტატები""
========================================================
* გამომდინარე იქიდან, რომ ჩვენ ქვეცნობიერად ვცდილობთ, მონაცემებში (არ)არსებული დამოკიდებულებები დავინახოთ, საჭიროა, რეალურად არსებული მოდელები ვაჩვენოთ


```r
p <- ggplot(data = gapminder,
            mapping = aes(x = gdpPercap,
                          y=lifeExp))
p + geom_point()+
    geom_smooth()
```

მონაცემთა ,,ფენოვანი" გრამატიკა: ,,სკალები""
========================================================


```r
p <- ggplot(data = gapminder,
            mapping = aes(x = gdpPercap,
                          y=lifeExp))
p + geom_point()+
    geom_smooth()+
    scale_x_log10()
```

მონაცემთა ,,ფენოვანი" გრამატიკა: ,,ესთეტიკა""
========================================================

```r
ggplot(gapminder,
          aes(x = gdpPercap,
          y=lifeExp))+
      geom_point(aes(color=continent))+
      geom_smooth()+
      scale_x_log10()
```


მონაცემთა ,,ფენოვანი" გრამატიკა: ,,ესთეტიკა""
========================================================

```r
ggplot(gapminder,
          aes(x = gdpPercap,
          y=lifeExp))+
      geom_point(aes(color=pop))+
      geom_smooth()+
      scale_x_log10()

ggsave("gapminder_plot.png", device="png", height=5)
```

მონაცემთა ,,ფენოვანი" გრამატიკა: ,,ჯგუფები და წახნაგები"
========================================================

```r
p <- ggplot(data = gapminder, mapping = aes(x = year, y = gdpPercap))
p + geom_line(color="gray70", aes(group = country)) +
    geom_smooth(size = 1.1, method = "loess", se = FALSE) +
    scale_y_log10(labels=scales::dollar) +
    facet_wrap(~ continent, ncol = 5) +
    labs(x = "წელი",
         y = "მშპ. ერთ სულ მოსახლეზე",
         title = "მშპ. ერთ სულ მოსახლეზე, ხუთი კონტინენტის მიხედვით")
```

მონაცემთა ,,ფენოვანი" გრამატიკა: Small multiples
========================================================
* თუკი მონაცემებში არსებობს _ლოგიკური კატეგორიები_, მნიშვნელოვანია მათი ჩვენება
* ჩვენს შემთხვევაში, მონაცემთა კონტინენტების მიხედვით წარმოდგენა გაცილებით საინტერესო და მდიდარ ისტორიას გვიყვება
* ,,წახნაგები'' სწორედ ამაში გვეხმარება


სასარგებლო რესურსები:
========================================================
* კირან ჰილის (დიუკის უნივერსიტეტი, ჩრდილო კაროლინა, აშშ) შესანიშნავი წიგნი: Data visualization - a practical introduction (https://socviz.co/index.html). წინამდებარე პრეზენტაცია სწორედ ამ წიგნიდან აღებულ მასალებს ეფუძნება
* `ggplot2` [,,შპარგალკა''](https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf)
* [ggplot2: Elegant Graphics for Data Analysis](https://www.amazon.com/ggplot2-Elegant-Graphics-Data-Analysis/dp/331924275X/ref=sr_1_1?s=books&ie=UTF8&qid=1506225102&sr=1-1&keywords=ggplot2)
* [ოფიციალური გვერდი](http://ggplot2.tidyverse.org/index.html)
* რა თქმა უნდა, [Stack Overflow](https://stackoverflow.com/questions/tagged/ggplot2)


გამოყენებული რესურსები:
========================================================
Kieran Healy: [Data Visualization - A practical introduction](https://socviz.co/index.html)
Selva Prabhakaran: [How to make any plot in ggplot2?](http://r-statistics.co/ggplot2-Tutorial-With-R.html)
Ista Zahn: [R graphics workshop @ Harvard](http://tutorials.iq.harvard.edu/R/Rgraphics/Rgraphics.html)

