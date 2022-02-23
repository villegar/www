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

## Example (Last rendered on 2022-02-23 00:08)

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
## Reading (RDG) Station Board on 2022-02-23 00:08:36
## Time   From                                    Plat  Expected
## 23:27  London Paddington                       12B   23:29
## 23:35  Oxford                                  15A   00:19
## 23:41  London Waterloo                         5     Delayed
## 23:46  Didcot Parkway                          15    00:28
## 23:49  Basingstoke                             13B   00:27
## 23:50  Manchester Piccadilly                   3     00:14
## 23:57  London Paddington                       12B   00:16
## 00:03  London Paddington                       13    00:13
## 00:06  Bedwyn                                  2     00:32
## 00:11  London Waterloo                         5     On time
## 00:17  Gatwick Airport                         15B   On time
## 00:23  London Paddington                       13    00:26
## 00:31  Basingstoke                             13B   01:00
## 00:40  Henley-on-Thames                        14    On time
## 00:41  London Waterloo                         6     On time
## 00:45  Gatwick Airport                         15    On time
## 00:48  London Paddington                       13    On time
## 01:04  Oxford                                  15    On time
## 01:11  London Paddington                       12B   On time
## 01:28  Oxford                                  -     Cancelled
## 01:31  London Paddington                       13    On time
## 01:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-23 00:08:40
## Time   To                                      Plat  Expected
## 23:28  Oxford                                  12B   00:07
## 23:33  Redhill                                 13A   00:08
## 23:34  Basingstoke                             2     00:07
## 23:38  London Paddington                       15A   00:22
## 23:52  Ascot                                   5     Delayed
## 00:05  Bristol Temple Meads                    13    00:14
## 00:08  Oxford                                  12B   00:17
## 00:17  Newbury                                 2     On time
## 00:18  London Paddington                       14    On time
## 00:26  Didcot Parkway                          13    00:26
## 01:06  London Paddington                       15    On time
## 01:13  Oxford                                  12B   On time
## 01:15  London Paddington                       13A   On time
## 00:16  Chippenham                              BUS   On time
```
