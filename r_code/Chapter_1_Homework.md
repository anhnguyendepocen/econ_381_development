# Econ 381 Chapter 1 Homework
Student Name Here  
April 18, 2018  

Libraries needed for this assignment

```r
#Load needed libraries
library(readxl)
library(tidyverse)
```



## 3. Country Snapshots

Solutions: 

(a)

(b)

(c)

(d)


## 4. Making graphs (spreadsheet)

Use the snapshots.pdf file, together with its hyperlinks to the underlying data. Use the R Markdown to complete the following:

(a) Make a plot of per capita GDP (in dollars) for the years 1950 to 2014 for a country of your choice. Label the x-axis "year" and the y-axis "per capita GDP."


```r
#Read in the data

USA <- read_excel("C:/Users/Andrew/Documents/Econ 381 Course Development/Chapter 1/USA.xls", skip = 9)

Germany <- read_excel("C:/Users/Andrew/Documents/Econ 381 Course Development/Chapter 1/DEU.xls", skip = 9)

Italy <- read_excel("C:/Users/Andrew/Documents/Econ 381 Course Development/Chapter 1/ITA.xls", skip = 9)

Japan <- read_excel("C:/Users/Andrew/Documents/Econ 381 Course Development/Chapter 1/JPN.xls", skip = 9)


#Fiter out a row of NA's from each dataset

USA <- USA %>% 
  filter(Year != is.na(Year))

Germany <- Germany %>% 
  filter(Year != is.na(Year))

Italy <- Italy %>% 
  filter(Year != is.na(Year))

Japan <- Japan %>% 
  filter(Year != is.na(Year))

USA %>% 
  ggplot(aes(x = Year, y = `Y/Pop`)) + 
  geom_point() + 
  geom_line() + 
  labs(y = "per Capita GDP", title = "USA Per Capita GDP") + 
  theme_bw()
```

![](Chapter_1_Homework_files/figure-html/unnamed-chunk-2-1.png)<!-- -->



(b) Make a plot of per capita GDP relative to the United States (US = 100) for the years 1950 to 2014 that includes the United States and three other countries of your choice, all on the same graph. Be sure to label the lines on the graph in some informative way so that each line can be associated with its country.


```r
ggplot(USA) + 
  geom_point(data = Italy, aes(x = Year, y = `Y/Pop(us=100)`), col = "green") + 
  geom_line(data = Italy, aes(x = Year, y = `Y/Pop(us=100)`),  col = "green") +
  geom_point(data = Germany, aes(x = Year, y = `Y/Pop(us=100)`), col = "red") + 
  geom_line(data = Germany, aes(x = Year, y = `Y/Pop(us=100)`), col = "red") + 
  geom_point(data = Japan, aes(x = Year, y = `Y/Pop(us=100)`)) + 
  geom_line(data = Japan, aes(x = Year, y = `Y/Pop(us=100)`)) +
  geom_text(aes(label = "Italy", x = 2008, y = 60), col = "green") +
  geom_text(aes(label = "Japan", x = 2011, y = 65), col = "black") +
  geom_text(aes(label = "Germany", x = 2011, y = 77), col = "red") +
  labs(y = "per capita GDP", title = "Per Capita GDP Relative to USA", 
       subtitle = "Note USA = 100") + 
  theme_bw()
```

![](Chapter_1_Homework_files/figure-html/unnamed-chunk-3-1.png)<!-- -->


## 6. The Labor Market Model (II)

Solutions:

(a)

(b)

(c)

(d)