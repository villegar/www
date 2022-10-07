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

## Example (Last rendered on 2022-10-07 16:06)

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
## Reading (RDG) Station Board on 2022-10-07 16:06:17
## Time   From                                    Plat  Expected
## 17:06  Bournemouth                             8     On time
## 17:11  London Paddington                       9     On time
## 17:14  London Paddington                       14    On time
## 17:16  London Waterloo                         6     On time
## 17:21  Cardiff Central                         11    17:32
## 17:22  London Paddington                       12    On time
## 17:24  Oxford                                  10    On time
## 17:27  London Paddington                       13    On time
## 17:35  London Paddington                       7     On time
## 17:38  Plymouth                                10    On time
## 17:41  London Paddington                       9     On time
## 17:41  London Paddington                       12    On time
## 17:41  Manchester Piccadilly                   8     17:45
## 17:42  London Waterloo                         4     On time
## 17:46  Basingstoke                             2     On time
## 17:47  Swansea                                 10    On time
## 17:55  London Paddington                       8     On time
## 17:58  London Paddington                       9     On time
## 17:59  London Paddington                       13    On time
## 18:00  London Paddington                       8     On time
## 18:03  Didcot Parkway                          15    On time
## 18:05  Bournemouth                             12    On time
## 18:11  London Paddington                       14    On time
## 18:11  London Paddington                       9     On time
## 18:12  London Waterloo                         5     On time
## 18:17  Cardiff Central                         11    On time
## 18:26  London Paddington                       13    On time
## 18:26  Oxford                                  10    On time
## 18:30  Basingstoke                             3     On time
## 18:41  London Paddington                       14    On time
## 18:41  Plymouth                                10    On time
## 18:42  London Waterloo                         6     On time
## 18:43  London Paddington                       9     On time
## 18:43  Manchester Piccadilly                   8     On time
## 18:47  Swansea                                 10    On time
## 18:54  London Paddington                       12B   On time
## 18:57  London Paddington                       9     On time
## 18:58  London Paddington                       13    On time
## 18:59  London Paddington                       7     On time
## 19:05  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-07 16:06:21
## Time   To                                      Plat  Expected
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  London Paddington                       13    On time
## 17:22  London Paddington                       11    17:33
## 17:24  London Paddington                       7     On time
## 17:27  London Paddington                       10    On time
## 17:28  London Paddington                       14    On time
## 17:31  Basingstoke                             2     On time
## 17:41  London Paddington                       10    On time
## 17:42  London Paddington                       14    On time
## 17:42  London Waterloo                         6     On time
## 17:43  Swansea                                 9     On time
## 17:48  London Paddington                       13    On time
## 17:50  London Paddington                       10    On time
## 17:52  Bournemouth                             8     On time
## 17:57  Bristol Temple Meads                    8     On time
## 17:58  Didcot Parkway                          15A   On time
## 17:58  London Paddington                       12    On time
## 18:01  Oxford                                  9     On time
## 18:04  Plymouth                                8     On time
## 18:12  London Waterloo                         4     On time
## 18:13  Carmarthen                              9     On time
## 18:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 18:17  London Paddington                       13    On time
## 18:20  London Paddington                       11    On time
## 18:25  London Paddington                       7     On time
## 18:28  London Paddington                       10    On time
## 18:28  London Paddington                       14    On time
## 18:32  Basingstoke                             2     On time
## 18:42  London Waterloo                         5     On time
## 18:43  London Paddington                       10    On time
## 18:47  London Paddington                       13    On time
## 18:49  London Paddington                       10    On time
## 18:50  Oxford                                  9     On time
## 18:57  Didcot Parkway                          15    On time
## 18:58  London Paddington                       14    On time
## 18:59  Bristol Temple Meads                    9     On time
## 19:03  Plymouth                                7     On time
```
