---
title: 'trainR: An Interface to the National Rail Enquiries Systems'
author: Roberto Villegas-Diaz
date: '2021-02-08'
slug: trainR-an-interface-to-the-nre-systems
tags:
  - uk-railway
  - nre
Categories:
  - Development
  - R
Description: ''
Tags:
  - Development
  - R
---

<img src="https://raw.githubusercontent.com/villegar/trainR/main/inst/images/logo.png" alt="logo" align="right" height=200px/>

The goal of `trainR` is to provide a simple interface to the 
National Rail Enquiries (NRE) systems. There are few data feeds 
available, the simplest of them is Darwin, which provides real-time 
arrival and departure predictions, platform numbers, delay estimates, 
schedule changes and cancellations. Other data feeds provide historical 
data, Historic Service Performance (HSP), and much more. `trainR` 
simplifies the data retrieval, so that the users can focus on their 
analyses. For more details visit 
https://www.nationalrail.co.uk/46391.aspx.

## Installation

You can install the released version of trainR from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("trainR")
```

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("villegar/trainR", "dev")
```

## Setup
Before starting to retrieve data from the NRE data feeds, you must obtain an access token. 
Visit the following website for details: http://realtime.nationalrail.co.uk/OpenLDBWSRegistration/

Once you have received your access token, you have to store it in the `.Renviron` file; this can be 
done by executing the following command:


```r
trainR::set_token()
```

This will open a text file, `.Renviron`, add a new line at the end (as follows):

```bash
NRE="<token>"
```

`<token>` should be replaced by the access token obtained from the NRE. Save the changes and restart 
your R session.

You only need to perform this configuration once.

## Example (Last rendered on 2023-02-03 18:03)

Load `trainR` to your working environment:

```r
library(trainR)
```

### Arrivals board at Reading Station (RDG)


```r
rdg_arr <- trainR::GetArrBoardRequest("RDG")
print(rdg_arr)
```

```
## Reading (RDG) Station Board on 2023-02-03 18:03:27
## Time   From                                    Plat  Expected
## 17:58  Abbey Wood                              13    18:05
## 18:10  Abbey Wood                              14    On time
## 18:12  London Waterloo                         -     Cancelled
## 18:19  Oxford                                  12    18:21
## 18:23  Basingstoke                             15    On time
## 18:25  Abbey Wood                              13    On time
## 18:40  Abbey Wood                              14    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:44  London Waterloo                         -     Cancelled
## 18:57  Abbey Wood                              13    On time
## 19:09  Abbey Wood                              13    On time
## 19:14  Abbey Wood                              14    19:17
## 19:17  London Waterloo                         6     On time
## 19:19  Basingstoke                             2     On time
## 19:27  Oxford                                  15    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:40  Abbey Wood                              13    On time
## 19:44  Abbey Wood                              14    On time
## 19:44  London Waterloo                         5     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-03 18:03:30
## Time   To                                      Plat  Expected
## 18:12  Basingstoke                             2     On time
## 18:12  London Waterloo                         4     On time
## 18:17  Abbey Wood                              13    On time
## 18:28  Abbey Wood                              14    On time
## 18:42  London Paddington                       11    On time
## 18:42  London Waterloo                         -     Cancelled
## 18:42  Oxford                                  12B   On time
## 18:47  Abbey Wood                              13    On time
## 18:57  Cardiff Central                         9     On time
## 18:58  Abbey Wood                              14    On time
## 19:12  London Waterloo                         -     Cancelled
## 19:27  Abbey Wood                              14    On time
## 19:41  London Paddington                       10    On time
## 19:42  London Waterloo                         6     On time
## 19:42  Oxford                                  15B   On time
## 19:57  Abbey Wood                              13    On time
## 19:57  Bristol Temple Meads                    8     On time
```
