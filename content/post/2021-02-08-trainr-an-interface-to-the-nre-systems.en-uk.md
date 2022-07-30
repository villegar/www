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

## Example (Last rendered on 2022-07-30 12:03)

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
## Reading (RDG) Station Board on 2022-07-30 12:03:54
## Time   From                                    Plat  Expected
## 13:03  London Paddington                       14    On time
## 13:05  Bournemouth                             13B   13:10
## 13:20  Oxford                                  15    13:23
## 13:22  Basingstoke                             2     13:24
## 13:33  London Paddington                       14    On time
## 13:39  Bristol Temple Meads                    -     Cancelled
## 13:39  Manchester Piccadilly                   7     On time
## 13:55  London Paddington                       9     On time
## 14:06  London Paddington                       14    On time
## 14:20  Basingstoke                             2     On time
## 14:22  Oxford                                  15    On time
## 14:33  London Paddington                       14    On time
## 14:40  Bristol Temple Meads                    10    On time
## 14:40  Manchester Piccadilly                   7     On time
## 14:55  London Paddington                       -     Cancelled
## 13:03  Virginia Water                          -     Cancelled
## 13:24  Virginia Water                          BUS   On time
## 13:33  Virginia Water                          BUS   On time
## 13:54  Virginia Water                          BUS   On time
## 14:03  Virginia Water                          -     Cancelled
## 14:24  Virginia Water                          BUS   On time
## 14:33  Virginia Water                          BUS   On time
## 14:54  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-30 12:03:58
## Time   To                                      Plat  Expected
## 13:05  Basingstoke                             2     On time
## 13:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 13:24  London Paddington                       14    On time
## 13:42  London Paddington                       -     Cancelled
## 13:42  Oxford                                  15B   On time
## 13:54  London Paddington                       14    On time
## 13:56  Bristol Temple Meads                    9     On time
## 14:07  Basingstoke                             2     On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:24  London Paddington                       14    On time
## 14:42  Oxford                                  15B   On time
## 14:43  London Paddington                       10    On time
## 14:53  Bournemouth                             7     On time
## 14:54  London Paddington                       14    On time
## 14:57  Bristol Temple Meads                    -     Cancelled
## 13:11  Virginia Water                          -     Cancelled
## 13:20  Virginia Water                          BUS   On time
## 13:41  Virginia Water                          BUS   On time
## 13:50  Virginia Water                          BUS   On time
## 14:11  Virginia Water                          -     Cancelled
## 14:20  Virginia Water                          BUS   On time
## 14:41  Virginia Water                          BUS   On time
## 14:50  Virginia Water                          BUS   On time
```
