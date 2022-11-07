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

## Example (Last rendered on 2022-11-07 06:08)

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
## Reading (RDG) Station Board on 2022-11-07 06:08:22
## Time   From                                    Plat  Expected
## 06:16  London Paddington                       13    On time
## 06:18  London Paddington                       -     06:22
## 06:28  Cheltenham Spa                          -     On time
## 06:31  Basingstoke                             -     Delayed
## 06:34  Bristol Temple Meads                    -     On time
## 06:41  London Paddington                       14    On time
## 06:51  Gatwick Airport                         -     06:53
## 06:52  Basingstoke                             -     On time
## 06:53  London Paddington                       -     On time
## 07:03  London Paddington                       -     On time
## 07:06  London Paddington                       14    On time
## 07:11  Abbey Wood                              12    On time
## 07:12  Hereford                                -     On time
## 07:18  London Paddington                       -     On time
## 07:27  Abbey Wood                              13    On time
## 07:29  Basingstoke                             -     On time
## 07:30  London Paddington                       -     On time
## 07:31  Cheltenham Spa                          -     Delayed
## 07:34  Redhill                                 -     On time
## 07:41  Bristol Temple Meads                    -     On time
## 07:44  Abbey Wood                              14    On time
## 07:47  Basingstoke                             -     On time
## 07:53  London Paddington                       -     On time
## 07:56  Hereford                                -     On time
## 07:56  London Paddington                       9     On time
## 07:57  Abbey Wood                              13    On time
## 08:06  Basingstoke                             -     On time
## 08:07  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 06:08:26
## Time   To                                      Plat  Expected
## 06:00  Worcester Shrub Hill                    9     06:06
##        via Gloucester                          
## 06:18  Great Malvern                           -     06:22
## 06:19  Basingstoke                             -     On time
## 06:26  Gatwick Airport                         -     On time
##        via Guildford                           
## 06:28  London Paddington                       -     On time
## 06:30  Abbey Wood                              13    On time
## 06:34  London Paddington                       -     On time
## 06:40  Basingstoke                             -     On time
## 06:50  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 06:53  Cheltenham Spa                          -     On time
## 06:56  Abbey Wood                              14    On time
## 06:57  Basingstoke                             -     On time
## 07:03  Exeter St Davids                        -     On time
## 07:12  London Paddington                       -     On time
## 07:13  Abbey Wood                              14    On time
## 07:18  Great Malvern                           -     On time
## 07:20  Redhill                                 -     On time
## 07:26  Abbey Wood                              14    On time
## 07:30  Exeter St Davids                        -     On time
## 07:31  London Paddington                       -     Delayed
## 07:37  Basingstoke                             7     On time
## 07:38  Cardiff Central                         9     On time
## 07:40  Abbey Wood                              13    On time
## 07:41  London Paddington                       -     On time
## 07:49  Oxford                                  8     On time
## 07:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 07:51  London Paddington                       13    On time
## 07:52  Didcot Parkway                          15    On time
## 07:53  Cheltenham Spa                          -     On time
## 07:56  Abbey Wood                              14    On time
## 07:56  London Paddington                       -     On time
## 08:00  Bristol Temple Meads                    9     On time
```
