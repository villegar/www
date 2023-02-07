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

## Example (Last rendered on 2023-02-07 22:04)

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
## Reading (RDG) Station Board on 2023-02-07 22:04:11
## Time   From                                    Plat  Expected
## 21:41  Manchester Piccadilly                   7     22:01
## 22:00  Paignton                                11    On time
## 22:05  Didcot Parkway                          15A   On time
## 22:07  London Paddington                       13A   On time
## 22:08  Exeter St Davids                        10A   22:12
## 22:11  Abbey Wood                              14    On time
## 22:11  London Paddington                       9     On time
## 22:14  Newbury                                 13    On time
## 22:15  London Paddington                       12B   On time
## 22:16  London Paddington                       9B    On time
## 22:20  Newbury                                 11A   On time
## 22:25  Oxford                                  12B   On time
## 22:26  London Paddington                       9     On time
## 22:32  Cheltenham Spa                          10A   On time
## 22:34  Shalford                                14A   On time
## 22:39  Manchester Piccadilly                   7B    On time
## 22:40  Abbey Wood                              14    On time
## 22:40  Basingstoke                             2     On time
## 22:42  London Waterloo                         6     On time
## 22:43  London Paddington                       9B    On time
## 22:43  Swansea                                 10    On time
## 22:45  London Paddington                       12B   On time
## 22:47  Didcot Parkway                          15    On time
## 22:52  Salisbury                               -     Cancelled
## 22:55  London Paddington                       13    On time
## 22:58  London Paddington                       12B   On time
## 22:59  Worcester Foregate Street               15    On time
## 23:03  Basingstoke                             14    On time
## 23:09  Abbey Wood                              13    On time
## 23:10  Penzance                                12    On time
## 23:13  London Paddington                       14    On time
## 23:14  Newbury                                 15    On time
## 23:17  London Paddington                       12    On time
## 23:21  Didcot Parkway                          13    On time
## 23:21  Gatwick Airport                         15A   On time
## 23:27  Basingstoke                             15B   On time
## 23:27  London Paddington                       12    On time
## 23:35  Oxford                                  14A   On time
## 23:38  Abbey Wood                              13    On time
## 23:41  London Waterloo                         5     On time
## 23:46  Didcot Parkway                          15    On time
## 23:49  Basingstoke                             13B   On time
## 23:49  Manchester Piccadilly                   14B   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-07 22:04:14
## Time   To                                      Plat  Expected
## 21:52  Bournemouth                             7     22:04
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       11    On time
## 22:08  Ealing Broadway                         15A   On time
## 22:09  London Waterloo                         4     On time
## 22:10  London Paddington                       10A   22:13
## 22:10  Newbury                                 1     On time
## 22:13  Swansea                                 9     On time
## 22:18  Didcot Parkway                          12B   On time
## 22:18  Worcester Shrub Hill                    9B    On time
## 22:20  London Paddington                       11A   On time
## 22:26  London Paddington                       12B   On time
## 22:27  Abbey Wood                              14    On time
## 22:27  Plymouth                                9     On time
##        via Bristol                             
## 22:29  Basingstoke                             2     On time
## 22:35  London Paddington                       10A   On time
## 22:45  Oxford                                  9B    On time
## 22:46  London Paddington                       10    On time
## 22:47  Didcot Parkway                          12B   On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Basingstoke                             2     On time
## 22:57  Abbey Wood                              14    On time
## 22:59  Bristol Temple Meads                    13    On time
## 23:01  Bedwyn                                  12B   On time
## 23:01  London Paddington                       15    On time
## 23:09  London Waterloo                         6     On time
## 23:13  London Paddington                       12    On time
## 23:16  Ealing Broadway                         13    On time
## 23:18  Swansea                                 12    On time
## 23:22  Ealing Broadway                         13    On time
## 23:28  Oxford                                  12    On time
## 23:32  Didcot Parkway                          14B   On time
## 23:33  Gatwick Airport                         13A   On time
##        via Guildford                           
## 23:34  Basingstoke                             12B   On time
## 23:38  London Paddington                       14A   On time
## 23:52  Ascot                                   5     On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
