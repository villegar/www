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

## Example (Last rendered on 2022-04-02 22:03)

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
## Reading (RDG) Station Board on 2022-04-02 22:03:58
## Time   From                                    Plat  Expected
## 22:44  London Paddington                       13    On time
## 22:54  London Paddington                       9     23:02
## 23:04  Hereford                                -     23:07
## 23:04  Redhill                                 14B   On time
## 23:11  Penzance                                13    23:50
## 23:12  London Waterloo                         4     23:15
## 23:14  London Paddington                       14    On time
## 23:17  London Paddington                       13    On time
## 23:17  Newbury                                 12B   On time
## 23:25  Basingstoke                             12B   On time
## 23:27  Didcot Parkway                          14    On time
## 23:29  London Paddington                       13    On time
## 23:42  London Waterloo                         6     On time
## 23:46  London Paddington                       12    On time
## 23:46  London Paddington                       13    On time
## 23:52  Basingstoke                             13B   On time
## 23:52  Taunton                                 15    00:02
## 00:01  London Paddington                       12    On time
## 00:03  Gatwick Airport                         13    On time
## 00:08  Basingstoke                             12B   On time
## 00:08  Didcot Parkway                          15    On time
## 00:10  Newbury                                 14B   On time
## 00:15  London Waterloo                         6     On time
## 00:22  London Paddington                       13    On time
## 00:29  London Paddington                       15    On time
## 00:41  London Waterloo                         4     On time
## 00:44  Gatwick Airport                         14    On time
## 23:15  Heathrow Central Bus Stn                BUS   On time
## 00:15  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-02 22:04:01
## Time   To                                      Plat  Expected
## 22:56  Bristol Temple Meads                    9     23:04
## 23:05  Basingstoke                             12B   On time
## 23:05  Didcot Parkway                          13    On time
## 23:06  London Paddington                       -     23:08
## 23:09  Newbury                                 14    On time
## 23:13  London Paddington                       13    23:51
## 23:15  London Waterloo                         6     On time
## 23:34  Gatwick Airport                         15A   On time
##        via Guildford                           
## 23:48  Didcot Parkway                          12    On time
## 23:52  Staines                                 6     On time
## 23:54  London Paddington                       15    00:03
## 00:02  Bristol Temple Meads                    12    On time
## 00:18  Newbury                                 12B   On time
## 00:19  Hayes & Harlington                      15    On time
```
