---
title: "R introduction"
author: "Florent Chuffart"
date: "`r Sys.Date()`"
output: 
  rmarkdown::html_document:
    toc: true
    toc_float: true
    toc_depth: 3
    number_sections: true
---



## R CLI

R could be compared as an electronic calculator. It provides not only basic operations but also advanced features allowing to manipulate distributions.

```{r}
1+1
pi
rnorm(100)
plot(density(rnorm(100)))
```


## R GUI (RStudio)

https://www.rstudio.com

### working directory
```{r}
?getwd()
?setwd()
```

### scripts

```{r}
source("intro_r.R")
```

### data 

#### common types
    - numeric
    - factor
    - character
    - boolean
    
#### set of data

|	Homogeneous |	Heterogeneous |
|  vector     | matrix        |
|  list       | data.frame    |



### functions
  - signature (parameter)
  - return
  - scope and global variables
  

  

algorithm

An algorithm is a self-contained sequence of actions to be performed. 
An algorithm is an effective method that can be expressed within a finite amount of space and time.

 
affectation

control structure
  A control structure is a block of programming that analyzes variables and chooses a direction in which to go based on given parameters.
  





Examples 

apply

foo = data.frame(lapply(data.frame(foo, stringsAsFactors=FALSE), unlist), stringsAsFactors=FALSE)



```{r}
nb_serve = 100000
dices = as.factor(ceiling(runif(nb_serve*5)*6))
barplot(table(dices))

serves = matrix(dices,5)
score = function(s, DEBUG=FALSE) {
  if (DEBUG) print("_________________________________________")
  s = sort(s)
  if (DEBUG) print(s)
  if (sum(s == 1:5)==5 | sum(s==2:6)==5)  {
    return(500)
  }
  ts = table(s)
  sum = 0
  if (max(ts)>=3) {
    idx = names(which(ts == max(ts)))
    ts[idx] = ts[idx] - 3
    if (idx == 1) {
      sum = sum + 1000
    } else {
      sum = sum + as.numeric(idx) * 100      
    }
  }
  if ("1" %in% names(ts)) {
    sum = sum + 100 * ts["1"]      
  }
  if ("5" %in% names(ts)) {
    sum = sum + 50 * ts["5"]      
  }
  if (DEBUG) print(sum)
  return(sum)
}

foo = epimedtools::monitored_apply(serves, 2, score)

barplot(table(foo))













nb_serve = 1000000
dices = ceiling(runif(nb_serve*5)*6)
td = table(dices)
td
barplot(td)

serves = matrix(dices,5)
foo = epimedtools::monitored_apply(serves, 2, sum)

barplot(prop.table(table(foo)))

table(foo) / nb_serve * 7776


Refrences


http://adv-r.had.co.nz

http://r-pkgs.had.co.nz

```

