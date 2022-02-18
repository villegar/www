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

## Example (Last rendered on 2022-02-18 22:03)

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
## Reading (RDG) Station Board on 2022-02-18 22:03:49
## Time   From                                    Plat  Expected
## 22:00  Paignton                                -     Cancelled
## 22:04  Didcot Parkway                          -     Cancelled
## 22:07  London Paddington                       -     Cancelled
## 22:08  Exeter St Davids                        -     Cancelled
## 22:10  London Waterloo                         -     Cancelled
## 22:11  London Paddington                       -     Cancelled
## 22:13  London Paddington                       -     Cancelled
## 22:14  Newbury                                 -     Delayed
## 22:16  London Paddington                       -     Cancelled
## 22:20  Newbury                                 -     Cancelled
## 22:25  Oxford                                  -     Cancelled
## 22:26  London Paddington                       -     Cancelled
## 22:32  Cheltenham Spa                          -     Cancelled
## 22:33  Bedwyn                                  -     Cancelled
## 22:34  Shalford                                -     Cancelled
## 22:40  Basingstoke                             -     Cancelled
## 22:40  London Waterloo                         -     Cancelled
## 22:43  London Paddington                       -     Cancelled
## 22:43  London Paddington                       -     Cancelled
## 22:43  Swansea                                 -     Cancelled
## 22:45  Didcot Parkway                          -     Cancelled
## 22:52  Salisbury                               -     Cancelled
## 22:59  Worcester Foregate Street               -     Cancelled
## 23:03  Basingstoke                             -     Cancelled
## 23:10  Penzance                                -     Cancelled
## 23:13  London Paddington                       13    On time
## 23:14  Newbury                                 -     On time
## 23:15  London Paddington                       -     Cancelled
## 23:15  London Waterloo                         -     Cancelled
## 23:16  Gatwick Airport                         -     Cancelled
## 23:17  London Paddington                       -     Cancelled
## 23:21  Didcot Parkway                          -     Cancelled
## 23:27  Basingstoke                             -     Cancelled
## 23:27  London Paddington                       -     Cancelled
## 23:32  Bedwyn                                  -     Cancelled
## 23:35  Oxford                                  -     Cancelled
## 23:43  London Paddington                       -     Cancelled
## 23:46  Didcot Parkway                          -     Cancelled
## 23:49  Basingstoke                             -     Cancelled
## 23:50  Birmingham New Street                   -     Cancelled
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-18 22:03:52
## Time   To                                      Plat  Expected
## 22:05  Basingstoke                             -     Cancelled
## 22:05  London Paddington                       -     Cancelled
## 22:10  London Paddington                       -     Cancelled
## 22:10  Newbury                                 -     Cancelled
## 22:12  Bedwyn                                  -     Cancelled
## 22:12  London Waterloo                         -     Cancelled
## 22:13  Swansea                                 -     Cancelled
## 22:18  Didcot Parkway                          -     Cancelled
## 22:18  Worcester Shrub Hill                    -     Cancelled
## 22:20  London Paddington                       -     Cancelled
## 22:22  Ealing Broadway                         -     Cancelled
## 22:26  London Paddington                       -     Cancelled
## 22:27  Plymouth                                -     Cancelled
##        via Bristol                             
## 22:29  Basingstoke                             -     Cancelled
## 22:35  London Paddington                       -     Cancelled
## 22:45  Oxford                                  -     Cancelled
## 22:46  Didcot Parkway                          -     Cancelled
## 22:46  London Paddington                       -     Cancelled
## 22:52  Basingstoke                             -     Cancelled
## 22:52  Ealing Broadway                         -     Cancelled
## 23:01  Bedwyn                                  -     Cancelled
## 23:01  London Paddington                       -     Cancelled
## 23:12  Ascot                                   -     Cancelled
## 23:12  Bedwyn                                  -     Cancelled
## 23:18  Swansea                                 -     Cancelled
## 23:19  London Paddington                       -     Cancelled
## 23:28  Oxford                                  -     Cancelled
## 23:32  Didcot Parkway                          -     Cancelled
## 23:33  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 23:34  Basingstoke                             -     Cancelled
## 23:38  London Paddington                       -     Cancelled
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
