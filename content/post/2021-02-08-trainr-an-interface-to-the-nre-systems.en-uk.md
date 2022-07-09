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

## Example (Last rendered on 2022-07-09 22:04)

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
## Reading (RDG) Station Board on 2022-07-09 22:04:18
## Time   From                                    Plat  Expected
## 22:41  Manchester Piccadilly                   12    23:23
## 23:03  London Paddington                       14    23:06
## 23:04  Hereford                                13A   On time
## 23:04  Redhill                                 15    23:07
## 23:10  London Paddington                       -     On time
## 23:11  London Waterloo                         4     23:15
## 23:11  Penzance                                15    On time
## 23:17  London Paddington                       13    On time
## 23:18  Newbury                                 12B   On time
## 23:25  Basingstoke                             13    On time
## 23:26  Didcot Parkway                          14    On time
## 23:28  London Paddington                       12    23:32
## 23:35  London Paddington                       14    On time
## 23:35  Oxford                                  15    On time
## 23:41  London Waterloo                         6     On time
## 23:46  London Paddington                       12    On time
## 23:52  Taunton                                 15    On time
## 23:55  Basingstoke                             14B   On time
## 00:03  Gatwick Airport                         13B   On time
## 00:04  London Paddington                       12    On time
## 00:09  Basingstoke                             13B   On time
## 00:10  Didcot Parkway                          15    On time
## 00:10  London Paddington                       14A   On time
## 00:11  London Waterloo                         6     On time
## 00:12  Newbury                                 12B   On time
## 00:15  London Paddington                       -     On time
## 00:22  London Paddington                       13    On time
## 00:41  London Waterloo                         4     On time
## 00:44  Gatwick Airport                         5     00:54
## 23:15  Heathrow Central Bus Stn                BUS   On time
## 00:15  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-09 22:04:20
## Time   To                                      Plat  Expected
## 22:52  Southampton Central                     12    23:24
## 23:05  Basingstoke                             15B   On time
## 23:06  London Paddington                       13A   On time
## 23:10  Newbury                                 12B   On time
## 23:13  London Paddington                       15    On time
## 23:15  London Waterloo                         6     On time
## 23:17  Ealing Broadway                         15    On time
## 23:21  Ealing Broadway                         14    On time
## 23:32  Oxford                                  12    On time
## 23:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:38  London Paddington                       15    On time
## 23:48  Didcot Parkway                          12    On time
## 23:52  Staines                                 6     On time
## 23:56  London Paddington                       15    On time
## 00:05  Bristol Temple Meads                    12    On time
## 00:12  Oxford                                  14A   On time
## 00:18  Newbury                                 13B   On time
## 00:19  Ealing Broadway                         15    On time
```
