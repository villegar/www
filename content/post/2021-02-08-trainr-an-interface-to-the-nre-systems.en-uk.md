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

## Example (Last rendered on 2022-09-25 20:04)

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
## Reading (RDG) Station Board on 2022-09-25 20:04:30
## Time   From                                    Plat  Expected
## 20:58  Penzance                                11    21:01
## 21:00  Didcot Parkway                          10    On time
## 21:00  London Paddington                       9     21:02
## 21:02  London Waterloo                         4     21:04
## 21:05  Bournemouth                             8     21:07
## 21:08  London Paddington                       14    On time
## 21:13  Didcot Parkway                          15    On time
## 21:13  Taunton                                 10    On time
## 21:17  London Paddington                       9     On time
## 21:19  Bedwyn                                  1     On time
## 21:26  London Paddington                       7B    On time
## 21:32  London Waterloo                         6     On time
## 21:33  Basingstoke                             2     21:57
## 21:38  London Paddington                       14    On time
## 21:39  Didcot Parkway                          8     On time
## 21:48  Swansea                                 11    On time
## 21:54  London Paddington                       9     On time
## 21:59  Didcot Parkway                          10    On time
## 22:02  London Waterloo                         6     On time
## 22:05  Plymouth                                11    On time
## 22:08  London Paddington                       14    On time
## 22:09  Weston-super-Mare                       10    On time
## 22:13  Didcot Parkway                          13    On time
## 22:15  London Paddington                       7     On time
## 22:22  London Paddington                       9     On time
## 22:24  Newbury                                 13    On time
## 22:28  London Paddington                       -     Cancelled
## 22:32  London Waterloo                         6     On time
## 22:33  Basingstoke                             13    On time
## 22:39  Didcot Parkway                          8     On time
## 22:40  London Paddington                       14    On time
## 22:49  Carmarthen                              10A   On time
## 22:50  Penzance                                11    On time
## 23:02  London Waterloo                         6     On time
## 21:18  Guildford                               -     Cancelled
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:00  Guildford                               -     Cancelled
## 22:15  Heathrow Central Bus Stn                BUS   On time
## 22:38  Guildford                               -     Cancelled
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-25 20:04:34
## Time   To                                      Plat  Expected
## 20:38  Basingstoke                             2     21:03
## 21:00  London Paddington                       11    21:02
## 21:02  London Paddington                       10    21:04
## 21:04  Ealing Broadway                         14    On time
## 21:09  Swansea                                 9     On time
## 21:12  Didcot Parkway                          8     On time
## 21:15  Didcot Parkway                          13    On time
## 21:15  London Paddington                       10    On time
## 21:20  Didcot Parkway                          9     On time
## 21:24  London Waterloo                         4     On time
## 21:28  Exeter St Davids                        7B    On time
## 21:34  Ealing Broadway                         14    On time
## 21:38  Basingstoke                             2     On time
## 21:43  Bedwyn                                  1     On time
## 21:50  London Paddington                       11    On time
## 21:52  Southampton Central                     8     On time
## 21:54  London Waterloo                         6     On time
## 21:56  Bristol Temple Meads                    9     On time
## 22:01  Ealing Broadway                         14    On time
## 22:02  London Paddington                       10    On time
## 22:12  London Paddington                       11    On time
## 22:14  Didcot Parkway                          15    On time
## 22:15  Didcot Parkway                          7     On time
## 22:16  London Paddington                       10    On time
## 22:24  London Waterloo                         6     On time
## 22:25  Swansea                                 9     On time
## 22:28  Ealing Broadway                         14    On time
## 22:30  Bristol Temple Meads                    -     Cancelled
## 22:43  Newbury                                 15B   On time
## 22:54  London Waterloo                         6     On time
## 22:55  London Paddington                       10A   On time
## 22:57  London Paddington                       11    On time
## 22:58  Ealing Broadway                         14    On time
## 21:30  Guildford                               -     Cancelled
## 21:58  Guildford                               -     Cancelled
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 22:25  Guildford                               -     Cancelled
## 23:00  Heathrow Central Bus Stn                BUS   On time
## 23:03  Gatwick Airport                         -     Cancelled
##        via Guildford
```
