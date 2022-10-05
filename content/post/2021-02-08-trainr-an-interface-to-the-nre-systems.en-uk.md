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

## Example (Last rendered on 2022-10-05 14:30)

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
## Reading (RDG) Station Board on 2022-10-05 14:30:49
## Time   From                                    Plat  Expected
## 15:39  Bristol Temple Meads                    11    15:44
## 15:39  London Paddington                       14    On time
## 15:41  London Waterloo                         6     On time
## 15:56  London Paddington                       9     On time
## 16:11  London Paddington                       14    On time
## 16:11  London Waterloo                         4     On time
## 16:20  Basingstoke                             2     On time
## 16:20  Oxford                                  15    On time
## 16:39  Bristol Temple Meads                    10    On time
## 16:39  London Paddington                       14    On time
## 16:41  London Waterloo                         6     On time
## 16:56  London Paddington                       -     Cancelled
## 16:56  London Paddington                       13    On time
## 17:14  London Paddington                       14    On time
## 17:16  London Waterloo                         6     On time
## 17:20  Oxford                                  15    On time
## 17:27  Basingstoke                             2     On time
## 17:27  London Paddington                       13    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-05 14:30:52
## Time   To                                      Plat  Expected
## 15:42  London Waterloo                         4     On time
## 15:42  Oxford                                  15B   On time
## 15:43  London Paddington                       11    15:45
## 15:58  London Paddington                       14    On time
## 15:58  Swindon                                 9     On time
## 16:07  Basingstoke                             2     On time
## 16:12  London Waterloo                         6     On time
## 16:18  London Paddington                       13    On time
## 16:28  London Paddington                       14    On time
## 16:41  London Waterloo                         4     On time
## 16:42  London Paddington                       10    On time
## 16:42  Oxford                                  15B   On time
## 16:48  London Paddington                       13    On time
## 16:58  Bristol Temple Meads                    -     Cancelled
## 16:58  London Paddington                       14    On time
## 17:07  Basingstoke                             2     On time
## 17:12  London Waterloo                         6     On time
## 17:18  London Paddington                       13    On time
## 17:28  London Paddington                       14    On time
```
