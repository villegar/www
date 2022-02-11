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

## Example (Last rendered on 2022-02-11 22:04)

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
## Reading (RDG) Station Board on 2022-02-11 22:04:02
## Time   From                                    Plat  Expected
## 22:00  Paignton                                11    22:03
## 22:06  Didcot Parkway                          15A   22:01
## 22:07  London Paddington                       13    On time
## 22:08  Exeter St Davids                        10A   22:25
## 22:10  London Waterloo                         4     On time
## 22:11  London Paddington                       9     22:13
## 22:13  London Paddington                       14    On time
## 22:14  London Paddington                       12B   On time
## 22:16  London Paddington                       9     22:18
## 22:16  Newbury                                 15    On time
## 22:20  Newbury                                 11A   On time
## 22:25  Oxford                                  13A   On time
## 22:26  London Paddington                       9B    On time
## 22:32  Cheltenham Spa                          10    On time
## 22:34  Shalford                                13    On time
## 22:40  Basingstoke                             2     On time
## 22:40  London Waterloo                         6     On time
## 22:41  Birmingham New Street                   7B    On time
## 22:43  London Paddington                       9B    On time
## 22:43  London Paddington                       14    On time
## 22:43  Swansea                                 10    On time
## 22:44  London Paddington                       12B   On time
## 22:45  Didcot Parkway                          15    On time
## 22:52  Salisbury                               3     On time
## 22:59  Worcester Foregate Street               15    On time
## 23:03  Basingstoke                             2     On time
## 23:13  London Paddington                       13    On time
## 23:14  Newbury                                 3     On time
## 23:15  Didcot Parkway                          15A   On time
## 23:15  London Paddington                       12    On time
## 23:15  London Waterloo                         6     On time
## 23:16  Gatwick Airport                         4     On time
## 23:17  London Paddington                       8     On time
## 23:17  Penzance                                14    On time
## 23:27  Basingstoke                             15B   On time
## 23:27  London Paddington                       8B    On time
## 23:35  Oxford                                  15A   On time
## 23:43  London Paddington                       14    On time
## 23:46  Didcot Parkway                          15    On time
## 23:49  Basingstoke                             13B   On time
## 23:50  Birmingham New Street                   3     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 00:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-11 22:04:05
## Time   To                                      Plat  Expected
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       11    On time
## 22:10  London Paddington                       10A   22:26
## 22:10  Newbury                                 1     On time
## 22:12  Ealing Broadway                         15A   On time
## 22:12  London Waterloo                         4     On time
## 22:12  London Waterloo                         6     On time
## 22:13  Swansea                                 9     22:14
## 22:18  Didcot Parkway                          12B   On time
## 22:18  Worcester Shrub Hill                    9     22:18
## 22:20  London Paddington                       11A   On time
## 22:22  Ealing Broadway                         14    On time
## 22:26  London Paddington                       13A   On time
## 22:27  Plymouth                                9B    On time
##        via Bristol                             
## 22:29  Basingstoke                             2     On time
## 22:35  London Paddington                       10    On time
## 22:45  Oxford                                  9B    On time
## 22:46  Didcot Parkway                          12B   On time
## 22:46  London Paddington                       10    On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Basingstoke                             2     On time
## 22:52  Ealing Broadway                         14    On time
## 23:01  London Paddington                       15    On time
## 23:01  Newbury                                 13B   On time
## 23:12  Ascot                                   6     On time
## 23:18  Swansea                                 8     On time
## 23:20  London Paddington                       14    On time
## 23:22  Ealing Broadway                         15A   On time
## 23:28  Oxford                                  8B    On time
## 23:32  Didcot Parkway                          12B   On time
## 23:33  Gatwick Airport                         13A   On time
##        via Guildford                           
## 23:34  Basingstoke                             2     On time
## 23:38  London Paddington                       15A   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
