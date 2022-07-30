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

## Example (Last rendered on 2022-07-30 16:03)

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
## Reading (RDG) Station Board on 2022-07-30 16:04:00
## Time   From                                    Plat  Expected
## 17:03  London Paddington                       14    On time
## 17:05  Bournemouth                             13B   17:12
## 17:20  Basingstoke                             2     17:25
## 17:20  Oxford                                  15    17:24
## 17:33  London Paddington                       14    On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:40  Manchester Piccadilly                   7     17:42
## 17:55  London Paddington                       8     On time
## 18:03  London Paddington                       14    On time
## 18:19  Oxford                                  15    On time
## 18:21  Basingstoke                             13    On time
## 18:33  London Paddington                       14    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:55  London Paddington                       9     On time
## 17:03  Virginia Water                          -     Cancelled
## 17:24  Virginia Water                          BUS   On time
## 17:33  Virginia Water                          BUS   On time
## 17:54  Virginia Water                          BUS   On time
## 18:03  Virginia Water                          BUS   On time
## 18:24  Virginia Water                          BUS   On time
## 18:38  Virginia Water                          -     Cancelled
## 18:59  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-30 16:04:02
## Time   To                                      Plat  Expected
## 17:07  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 17:24  London Paddington                       14    On time
## 17:41  London Paddington                       10    On time
## 17:42  Oxford                                  15B   On time
## 17:54  London Paddington                       14    On time
## 18:00  Bristol Temple Meads                    8     On time
## 18:12  Basingstoke                             2     On time
## 18:15  Birmingham New Street                   7     On time
##        via Coventry                            
## 18:24  London Paddington                       14    On time
## 18:42  London Paddington                       11    On time
## 18:42  Oxford                                  15B   On time
## 18:52  Bournemouth                             7     On time
## 18:54  London Paddington                       14    On time
## 18:57  Bristol Temple Meads                    9     On time
## 17:11  Virginia Water                          -     Cancelled
## 17:20  Virginia Water                          BUS   On time
## 17:41  Virginia Water                          BUS   On time
## 17:50  Virginia Water                          BUS   On time
## 18:11  Virginia Water                          BUS   On time
## 18:20  Virginia Water                          BUS   On time
## 18:41  Virginia Water                          -     Cancelled
## 18:50  Virginia Water                          BUS   On time
```
