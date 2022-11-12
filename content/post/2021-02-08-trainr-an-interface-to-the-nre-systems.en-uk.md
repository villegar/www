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

## Example (Last rendered on 2022-11-12 22:03)

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
## Reading (RDG) Station Board on 2022-11-12 22:03:48
## Time   From                                    Plat  Expected
## 20:03  Abbey Wood                              14    Delayed
## 21:39  Manchester Piccadilly                   7     22:01
## 21:53  Swansea                                 10    22:01
## 22:04  Abbey Wood                              14    22:31
## 22:09  Taunton                                 10    22:14
## 22:13  London Paddington                       12B   On time
## 22:16  London Waterloo                         4     22:22
## 22:17  London Paddington                       8     On time
## 22:19  Basingstoke                             2     On time
## 22:22  Newbury                                 1     On time
## 22:25  London Paddington                       9     On time
## 22:26  Gatwick Airport                         13    22:33
## 22:27  Didcot Parkway                          15    On time
## 22:29  Oxford                                  11    On time
## 22:33  Abbey Wood                              14    22:39
## 22:36  Cheltenham Spa                          10    On time
## 22:41  Manchester Piccadilly                   -     Cancelled
## 22:43  London Paddington                       12B   On time
## 22:46  London Waterloo                         6     On time
## 22:50  Basingstoke                             2     On time
## 22:51  London Paddington                       10    On time
## 22:53  London Paddington                       9     On time
## 23:03  Abbey Wood                              14    On time
## 23:04  Hereford                                13    On time
## 23:04  Redhill                                 15    On time
## 23:10  Newbury                                 12B   On time
## 23:11  St Austell                              15    On time
## 23:14  London Waterloo                         4     On time
## 23:17  London Paddington                       13    On time
## 23:24  Basingstoke                             12    On time
## 23:26  Didcot Parkway                          14    On time
## 23:28  London Paddington                       13    On time
## 23:35  Abbey Wood                              14    On time
## 23:44  London Waterloo                         6     On time
## 23:46  London Paddington                       12B   On time
## 23:52  Taunton                                 15    On time
## 23:55  Basingstoke                             14B   On time
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
## Reading (RDG) Station Board on 2022-11-12 22:03:52
## Time   To                                      Plat  Expected
## 21:52  Southampton Central                     7     22:03
## 21:54  London Paddington                       10    22:03
## 22:05  Basingstoke                             2     On time
## 22:07  Ealing Broadway                         13    On time
## 22:09  London Waterloo                         5     On time
## 22:10  Newbury                                 1     On time
## 22:15  London Paddington                       10    On time
## 22:19  Worcester Shrub Hill                    8     On time
## 22:22  Abbey Wood                              14    22:34
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          12B   On time
## 22:34  London Paddington                       11    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10    On time
## 22:39  London Waterloo                         4     On time
## 22:52  Abbey Wood                              14    On time
## 22:52  Southampton Central                     -     Cancelled
## 22:55  Bristol Temple Meads                    9     On time
## 23:00  Didcot Parkway                          12B   On time
## 23:05  Basingstoke                             2     On time
## 23:06  London Paddington                       13    On time
## 23:10  Newbury                                 1     On time
## 23:13  London Paddington                       15    On time
## 23:15  London Waterloo                         6     On time
## 23:17  Ealing Broadway                         15A   On time
## 23:21  Ealing Broadway                         14    On time
## 23:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:48  Didcot Parkway                          12B   On time
## 23:52  Staines                                 6     On time
## 23:56  London Paddington                       15    On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
