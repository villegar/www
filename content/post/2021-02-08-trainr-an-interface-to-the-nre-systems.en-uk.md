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

## Example (Last rendered on 2021-12-29 22:03)

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
## Reading (RDG) Station Board on 2021-12-29 22:03:18
## Time   From                                    Plat  Expected
## 21:58  London Paddington                       9     22:29
## 22:05  Didcot Parkway                          15    22:02
## 22:08  Exeter St Davids                        10A   22:20
## 22:13  London Paddington                       14    On time
## 22:14  London Paddington                       12B   On time
## 22:14  Newbury                                 13    On time
## 22:15  Swansea                                 10    On time
## 22:16  London Paddington                       9     On time
## 22:20  Newbury                                 11    On time
## 22:25  Oxford                                  13A   On time
## 22:26  London Paddington                       9     On time
## 22:32  Cheltenham Spa                          10    On time
## 22:34  Shalford                                14A   On time
## 22:40  Basingstoke                             2     On time
## 22:41  Birmingham New Street                   7B    On time
## 22:41  London Waterloo                         6     On time
## 22:43  London Paddington                       14    On time
## 22:44  London Paddington                       12B   Delayed
## 22:45  Didcot Parkway                          15    On time
## 22:56  London Paddington                       12    On time
## 23:00  London Paddington                       13A   On time
## 23:03  Basingstoke                             2     On time
## 23:13  London Paddington                       13    On time
## 23:15  Didcot Parkway                          15    On time
## 23:15  Gatwick Airport                         6     On time
## 23:15  London Paddington                       14    On time
## 23:17  London Paddington                       8     On time
## 23:18  Penzance                                12    On time
## 23:23  London Waterloo                         5     On time
## 23:25  Swansea                                 7     On time
## 23:27  Basingstoke                             15B   On time
## 23:35  Oxford                                  13A   On time
## 23:43  London Paddington                       14    On time
## 23:46  Didcot Parkway                          15    On time
## 23:46  London Waterloo                         5     On time
## 23:49  Basingstoke                             13B   On time
## 23:51  Birmingham New Street                   14    On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-29 22:03:21
## Time   To                                      Plat  Expected
## 22:00  Swansea                                 9     22:30
## 22:05  Basingstoke                             3     On time
## 22:10  London Paddington                       10A   22:21
## 22:12  London Waterloo                         4     On time
## 22:14  Ealing Broadway                         15    On time
## 22:17  London Paddington                       10    On time
## 22:18  Didcot Parkway                          12B   On time
## 22:18  Worcester Shrub Hill                    9     On time
## 22:20  London Paddington                       11    On time
## 22:22  Ealing Broadway                         14    On time
## 22:26  London Paddington                       13A   On time
## 22:27  Plymouth                                9     On time
##        via Bristol                             
## 22:29  Basingstoke                             2     On time
## 22:35  London Paddington                       10    On time
## 22:46  Didcot Parkway                          12B   Delayed
## 22:49  Southampton Central                     7B    On time
## 22:52  Basingstoke                             2     On time
## 22:52  Ealing Broadway                         14    On time
## 22:59  Bristol Temple Meads                    12    On time
## 23:02  London Waterloo                         6     On time
## 23:05  Oxford                                  13A   On time
## 23:18  Swansea                                 8     On time
## 23:21  London Paddington                       12    On time
## 23:24  Ealing Broadway                         15    On time
## 23:32  Didcot Parkway                          14    On time
## 23:33  Gatwick Airport                         -     On time
##        via Guildford                           
## 23:34  Basingstoke                             2     On time
## 23:41  London Paddington                       7     On time
## 23:44  London Paddington                       13A   On time
## 23:52  Ascot                                   5     On time
## 22:10  Bedwyn                                  BUS   On time
## 22:10  Newbury                                 BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
## 23:13  Bedwyn                                  BUS   On time
```
