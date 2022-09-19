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

## Example (Last rendered on 2022-09-19 22:03)

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
## Reading (RDG) Station Board on 2022-09-19 22:03:51
## Time   From                                    Plat  Expected
## 22:00  Plymouth                                -     22:35
## 22:43  Swansea                                 -     23:01
## 22:55  London Paddington                       15    On time
## 22:59  Worcester Foregate Street               -     Cancelled
## 23:03  Basingstoke                             2     On time
## 23:09  London Paddington                       -     Cancelled
## 23:10  Penzance                                10    23:14
## 23:12  London Waterloo                         5     On time
## 23:13  London Paddington                       -     Cancelled
## 23:13  Newbury                                 3     On time
## 23:16  Gatwick Airport                         15A   On time
## 23:19  Didcot Parkway                          13    Delayed
## 23:35  Oxford                                  -     Cancelled
## 23:39  West Drayton                            14    On time
## 23:44  London Waterloo                         5     On time
## 23:46  Didcot Parkway                          15    On time
## 23:49  Basingstoke                             13B   On time
## 23:50  Manchester Piccadilly                   14B   On time
## 00:06  Bedwyn                                  -     Cancelled
## 00:11  London Waterloo                         6     00:13
## 00:17  Gatwick Airport                         15B   On time
## 00:31  Basingstoke                             13B   On time
## 00:40  Henley-on-Thames                        13    Delayed
## 00:41  Hereford                                -     Cancelled
## 00:41  London Waterloo                         5     On time
## 00:44  Gatwick Airport                         4     On time
## 00:48  London Paddington                       -     Cancelled
## 23:35  Heathrow Central Bus Stn                BUS   On time
## 00:35  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-19 22:03:54
## Time   To                                      Plat  Expected
## 22:05  London Paddington                       -     Delayed
## 22:46  London Paddington                       -     23:03
## 22:59  Bristol Temple Meads                    15    23:02
## 23:01  Bedwyn                                  -     Cancelled
## 23:01  London Paddington                       -     Cancelled
## 23:02  London Waterloo                         6     On time
## 23:16  Ealing Broadway                         -     Cancelled
## 23:18  Swansea                                 8     On time
## 23:28  Worcestershire Parkway                  13    On time
## 23:32  Didcot Parkway                          14    On time
## 23:33  Gatwick Airport                         13A   On time
##        via Guildford                           
## 23:34  Basingstoke                             2     On time
## 23:52  Ascot                                   5     On time
## 00:01  London Paddington                       -     Cancelled
## 00:05  Bristol Temple Meads                    13    On time
## 00:05  Plymouth                                7     On time
## 00:08  Oxford                                  -     Cancelled
## 00:17  Newbury                                 -     Cancelled
## 00:18  London Paddington                       -     Cancelled
## 00:26  Didcot Parkway                          13    On time
## 00:45  London Paddington                       -     Cancelled
## 00:49  Penzance                                -     Cancelled
## 00:50  London Paddington                       -     Cancelled
## 00:51  Bristol Temple Meads                    12    On time
```
