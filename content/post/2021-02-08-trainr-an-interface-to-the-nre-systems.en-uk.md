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

## Example (Last rendered on 2022-01-30 22:03)

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
## Reading (RDG) Station Board on 2022-01-30 22:03:54
## Time   From                                    Plat  Expected
## 22:02  London Waterloo                         6     22:05
## 22:05  Plymouth                                -     Cancelled
## 22:06  London Paddington                       7     On time
## 22:12  London Paddington                       8B    On time
## 22:12  London Paddington                       12    On time
## 22:13  Didcot Parkway                          13    On time
## 22:13  London Paddington                       14    On time
## 22:23  London Paddington                       7     22:31
## 22:24  Newbury                                 1     On time
## 22:27  Swansea                                 11    22:31
## 22:32  London Waterloo                         6     22:38
## 22:33  London Paddington                       14    On time
## 22:34  Basingstoke                             12    On time
## 22:36  Bristol Temple Meads                    11    22:38
## 22:39  Banbury                                 8     On time
## 22:46  Gatwick Airport                         15B   On time
## 22:52  Great Malvern                           15A   On time
## 22:55  Penzance                                13    On time
## 23:02  London Waterloo                         6     On time
## 23:03  London Paddington                       14    On time
## 23:08  Didcot Parkway                          15    On time
## 23:17  Bedwyn                                  15    On time
## 23:19  Banbury                                 12    On time
## 23:23  Carmarthen                              13    On time
## 23:32  London Waterloo                         6     On time
## 23:33  London Paddington                       13    On time
## 23:33  London Paddington                       14    On time
## 23:42  Gatwick Airport                         15    On time
## 23:46  Newbury                                 13    On time
## 23:59  Plymouth                                14    On time
## 00:02  London Waterloo                         5     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 22:05  Swindon                                 BUS   On time
## 22:35  Swindon                                 BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 23:13  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-30 22:03:57
## Time   To                                      Plat  Expected
## 22:10  Swansea                                 7     On time
## 22:13  Didcot Parkway                          12    On time
## 22:13  Worcester Shrub Hill                    8B    On time
## 22:18  London Paddington                       -     Cancelled
## 22:24  London Waterloo                         6     On time
## 22:25  Ealing Broadway                         14    On time
## 22:28  Bristol Temple Meads                    7     22:32
## 22:29  London Paddington                       11    22:32
## 22:42  London Paddington                       11    On time
## 22:44  Newbury                                 1     On time
## 22:52  London Paddington                       15A   On time
## 22:54  London Waterloo                         6     On time
## 22:55  London Paddington                       13    On time
## 22:59  Ealing Broadway                         14    On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:10  Ealing Broadway                         15    On time
## 23:20  Didcot Parkway                          13    On time
## 23:28  London Paddington                       13    On time
## 23:36  Bristol Temple Meads                    13    On time
## 00:01  London Paddington                       14    On time
## 22:20  Swindon                                 BUS   On time
## 22:37  Chippenham                              BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
## 23:45  Chippenham                              BUS   On time
```
