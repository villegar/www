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

## Example (Last rendered on 2022-07-16 22:10)

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
## Reading (RDG) Station Board on 2022-07-16 22:10:58
## Time   From                                    Plat  Expected
## 21:15  Penzance                                11    23:11
## 22:09  Taunton                                 10    23:25
## 22:41  Manchester Piccadilly                   7     23:39
## 23:04  Charlbury                               10A   On time
## 23:10  Newbury                                 12B   On time
## 23:11  Penzance                                11    23:50
## 23:17  London Paddington                       13    On time
## 23:24  Basingstoke                             13    On time
## 23:26  Didcot Parkway                          14    On time
## 23:28  London Paddington                       7     On time
## 23:35  London Paddington                       14    On time
## 23:35  Oxford                                  11    On time
## 23:46  London Paddington                       12    On time
## 23:52  Taunton                                 10    00:00
## 23:55  Basingstoke                             13B   On time
## 23:58  London Paddington                       7     On time
## 00:03  Gatwick Airport                         13B   On time
## 00:08  Basingstoke                             1     On time
## 00:10  Didcot Parkway                          15    On time
## 00:10  London Paddington                       7B    On time
## 00:12  Charlbury                               10    On time
## 00:13  Newbury                                 13B   On time
## 00:23  London Paddington                       13    On time
## 00:44  Gatwick Airport                         5     On time
## 23:15  Heathrow Central Bus Stn                BUS   On time
## 23:32  Staines                                 BUS   On time
## 23:37  Staines                                 BUS   On time
## 00:05  Staines                                 BUS   On time
## 00:07  Staines                                 BUS   On time
## 00:15  Heathrow Central Bus Stn                BUS   On time
## 00:33  Staines                                 BUS   On time
## 00:35  Staines                                 BUS   On time
## 01:02  Staines                                 BUS   On time
## 01:03  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-16 22:11:00
## Time   To                                      Plat  Expected
## 21:16  London Paddington                       11    23:12
## 22:15  London Paddington                       10    23:26
## 22:52  Southampton Central                     7     23:40
## 23:06  London Paddington                       10A   Delayed
## 23:10  Newbury                                 1     On time
## 23:15  London Paddington                       11    23:51
## 23:17  Ealing Broadway                         15    On time
## 23:21  Ealing Broadway                         14    On time
## 23:32  Oxford                                  7     On time
## 23:34  Gatwick Airport                         6     On time
##        via Guildford                           
## 23:38  London Paddington                       11    On time
## 23:48  Didcot Parkway                          12    On time
## 23:56  London Paddington                       10    00:01
## 00:05  Bristol Temple Meads                    7     On time
## 00:12  Oxford                                  7B    On time
## 00:15  London Paddington                       10    On time
## 00:18  Newbury                                 1     On time
## 00:19  Ealing Broadway                         15    On time
## 23:12  Staines                                 -     Cancelled
## 23:15  Staines                                 BUS   On time
## 23:42  Staines                                 -     Cancelled
## 23:52  Staines                                 BUS   On time
```
