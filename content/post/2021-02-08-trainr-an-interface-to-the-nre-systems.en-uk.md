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

## Example (Last rendered on 2022-03-13 14:04)

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
## Reading (RDG) Station Board on 2022-03-13 14:04:06
## Time   From                                    Plat  Expected
## 13:59  London Paddington                       8     On time
## 14:01  London Paddington                       9     On time
## 14:06  London Waterloo                         4     14:02
## 14:08  London Paddington                       14    On time
## 14:09  Bristol Temple Meads                    10A   14:11
## 14:10  Guildford                               6     On time
## 14:11  Didcot Parkway                          13    On time
## 14:12  London Paddington                       9B    On time
## 14:19  Newbury                                 1     On time
## 14:22  Slough                                  13    On time
## 14:24  Truro                                   11A   On time
## 14:33  London Paddington                       9     On time
## 14:36  London Waterloo                         4     On time
## 14:38  London Paddington                       14    On time
## 14:41  Manchester Piccadilly                   13    14:43
## 14:45  Cardiff Central                         10    14:54
## 14:47  London Paddington                       9B    On time
## 14:53  London Paddington                       9     On time
## 14:56  Bournemouth                             13B   On time
## 14:56  Hereford                                -     Cancelled
## 14:59  London Paddington                       8     On time
## 15:01  London Paddington                       9     On time
## 15:07  London Waterloo                         4     On time
## 15:08  Guildford                               6     On time
## 15:08  London Paddington                       14    On time
## 15:09  Weston-super-Mare                       11    On time
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15    On time
## 15:14  Truro                                   10    On time
## 15:18  Newbury                                 2     On time
## 15:22  Slough                                  12    On time
## 15:23  London Paddington                       9     On time
## 15:28  Oxford                                  10A   On time
## 15:36  London Waterloo                         4     On time
## 15:38  London Paddington                       14    On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Bristol Temple Meads                    10A   On time
## 15:46  Cardiff Central                         11    On time
## 15:47  London Paddington                       9B    On time
## 15:53  London Paddington                       9     On time
## 15:56  Hereford                                10    On time
## 14:18  Basingstoke                             BUS   On time
## 14:45  Heathrow Central Bus Stn                BUS   On time
## 15:00  Basingstoke                             BUS   On time
## 15:18  Bramley (Hampshire)                     BUS   On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-13 14:04:09
## Time   To                                      Plat  Expected
## 14:05  Plymouth                                8     On time
## 14:09  Cardiff Central                         9     On time
## 14:14  Hereford                                9B    On time
## 14:14  Slough                                  13    On time
## 14:15  London Paddington                       10A   On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 14:21  London Waterloo                         4     On time
## 14:25  Ealing Broadway                         14    On time
## 14:25  London Paddington                       11A   On time
## 14:26  Didcot Parkway                          13    On time
## 14:38  Guildford                               6     On time
## 14:40  Cardiff Central                         9     On time
## 14:44  Newbury                                 1     On time
## 14:46  Bournemouth                             13    On time
## 14:49  Oxford                                  9B    On time
## 14:50  London Paddington                       10    14:55
## 14:51  London Waterloo                         4     On time
## 14:52  Ealing Broadway                         14    On time
## 14:54  Taunton                                 9     On time
## 15:02  London Paddington                       -     Cancelled
## 15:05  Plymouth                                8     On time
## 15:09  Cardiff Central                         9     On time
## 15:14  Great Malvern                           9B    On time
## 15:14  Slough                                  15    On time
## 15:15  London Paddington                       11    On time
## 15:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 15:20  London Paddington                       10    On time
## 15:21  London Waterloo                         4     On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:25  Ealing Broadway                         14    On time
## 15:26  Didcot Parkway                          12    On time
## 15:32  London Paddington                       10A   On time
## 15:41  Guildford                               6     On time
## 15:44  Newbury                                 2     On time
## 15:45  London Paddington                       10A   On time
## 15:49  Oxford                                  9B    On time
## 15:50  London Paddington                       11    On time
## 15:51  London Waterloo                         4     On time
## 15:55  Ealing Broadway                         14    On time
## 15:55  Taunton                                 9     On time
## 16:02  London Paddington                       10    On time
## 14:38  Basingstoke                             BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:38  Bramley (Hampshire)                     BUS   On time
## 15:52  Basingstoke                             BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
