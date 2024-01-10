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

## Example (Last rendered on 2024-01-10 13:05)

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
## Reading (RDG) Station Board on 2024-01-10 13:05:39.878569
## Time   From                                    Plat  Expected
## 12:57  Gatwick Airport                         5     13:03
## 12:58  Great Malvern                           10A   13:07
## 12:58  London Paddington                       7B    13:02
## 12:58  Penzance                                11    13:07
## 13:01  Didcot Parkway                          15A   On time
## 13:05  Weston-super-Mare                       10    13:11
## 13:06  Bournemouth                             8B    13:03
## 13:11  London Paddington                       9B    On time
## 13:11  London Waterloo                         4     13:13
## 13:12  Abbey Wood                              14    On time
## 13:12  York                                    3     13:35
## 13:16  London Paddington                       9     Delayed
## 13:18  Basingstoke                             2     On time
## 13:18  London Paddington                       13B   On time
## 13:19  Cardiff Central                         11    13:24
## 13:24  London Paddington                       9     13:26
## 13:24  Oxford                                  -     Cancelled
## 13:26  London Paddington                       7     On time
## 13:28  Gatwick Airport                         5     On time
## 13:31  Cheltenham Spa                          11A   On time
## 13:32  Didcot Parkway                          15A   On time
## 13:32  London Paddington                       7B    On time
## 13:36  Newbury                                 1     On time
## 13:38  London Paddington                       -     Cancelled
## 13:39  Bristol Temple Meads                    10    On time
## 13:41  Abbey Wood                              13    On time
## 13:41  Manchester Piccadilly                   7B    On time
## 13:43  London Waterloo                         6     On time
## 13:45  Swansea                                 10    On time
## 13:46  London Paddington                       9     On time
## 13:48  Paignton                                11A   On time
## 13:50  London Paddington                       14B   On time
## 13:53  London Paddington                       9     On time
## 13:55  Basingstoke                             2     On time
## 13:55  London Paddington                       8B    On time
## 13:57  Gatwick Airport                         5     On time
## 13:57  Great Malvern                           10A   On time
## 14:02  Penzance                                11    On time
## 14:07  Bournemouth                             8     On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:11  Abbey Wood                              14    On time
## 14:11  Didcot Parkway                          15A   On time
## 14:11  London Paddington                       9B    On time
## 14:13  London Waterloo                         4     On time
## 14:15  London Paddington                       12B   On time
## 14:16  Cardiff Central                         11    On time
## 14:16  London Paddington                       9     On time
## 14:20  Basingstoke                             2     On time
## 14:23  London Paddington                       9     On time
## 14:23  Newbury                                 11A   On time
## 14:24  Oxford                                  10A   On time
## 14:26  London Paddington                       7     On time
## 14:28  Gatwick Airport                         5     On time
## 14:30  Cheltenham Spa                          11A   On time
## 14:33  London Paddington                       7B    On time
## 14:38  Didcot Parkway                          15A   On time
## 14:38  London Paddington                       9     On time
## 14:40  Bristol Temple Meads                    10    On time
## 14:40  Custom House                            14    On time
## 14:40  Newbury                                 1     On time
## 14:42  Manchester Piccadilly                   12B   On time
## 14:43  London Waterloo                         6     On time
## 14:43  Newbury                                 11A   On time
## 14:45  Carmarthen                              10    14:48
## 14:45  London Paddington                       13B   On time
## 14:46  London Paddington                       9B    On time
## 14:48  Basingstoke                             2     On time
## 14:53  London Paddington                       9     On time
## 14:55  London Paddington                       8     On time
## 14:57  Gatwick Airport                         5     On time
## 14:58  Worcester Shrub Hill                    10A   On time
## 14:59  London Paddington                       7     On time
## 14:59  Penzance                                11    On time
## 13:15  Heathrow Airport T3 (Bus)               BUS   On time
## 13:45  Heathrow Airport T3 (Bus)               BUS   On time
## 14:15  Heathrow Airport T3 (Bus)               BUS   On time
## 14:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-10 13:05:42.701572
## Time   To                                      Plat  Expected
## 13:01  Exeter St Davids                        7B    13:04
## 13:01  London Paddington                       10A   13:08
## 13:04  London Paddington                       11    13:08
## 13:07  Basingstoke                             2     On time
## 13:07  London Paddington                       10    13:12
## 13:09  London Waterloo                         6     On time
## 13:12  London Paddington                       15A   On time
## 13:12  Newbury                                 1     On time
## 13:13  Swansea                                 9B    On time
## 13:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 13:18  Worcester Foregate Street               9     Delayed
## 13:21  London Paddington                       11    13:25
## 13:22  Didcot Parkway                          13B   On time
## 13:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:26  Bristol Temple Meads                    9     13:26
## 13:26  London Paddington                       -     Cancelled
## 13:29  Abbey Wood                              14    On time
## 13:29  Plymouth                                7     On time
## 13:32  Basingstoke                             2     On time
## 13:34  London Paddington                       11A   On time
## 13:37  Newbury                                 7B    On time
## 13:39  London Paddington                       15A   On time
## 13:39  London Waterloo                         4     On time
## 13:40  Cardiff Central                         -     Cancelled
## 13:41  London Paddington                       10    On time
## 13:48  London Paddington                       10    On time
## 13:48  Oxford                                  9     On time
## 13:51  London Paddington                       11A   On time
## 13:52  Bournemouth                             7B    On time
## 13:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:55  Bristol Temple Meads                    9     On time
## 13:55  Didcot Parkway                          14B   On time
## 13:58  Cheltenham Spa                          8B    On time
## 13:59  Abbey Wood                              13    On time
## 13:59  London Paddington                       10A   On time
## 14:04  London Paddington                       11    On time
## 14:07  Basingstoke                             2     On time
## 14:09  London Waterloo                         6     On time
## 14:11  London Paddington                       10    On time
## 14:12  London Paddington                       15A   On time
## 14:12  Newbury                                 1     On time
## 14:13  Carmarthen                              9B    On time
## 14:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Great Malvern                           9     On time
## 14:19  London Paddington                       11    On time
## 14:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:25  Bristol Temple Meads                    9     On time
## 14:25  Didcot Parkway                          12B   On time
## 14:26  London Paddington                       11A   On time
## 14:28  London Paddington                       10A   On time
## 14:29  Abbey Wood                              14    On time
## 14:29  Penzance                                7     On time
## 14:32  Basingstoke                             2     On time
## 14:35  London Paddington                       11A   On time
## 14:37  Newbury                                 7B    On time
## 14:39  London Waterloo                         4     On time
## 14:40  Cardiff Central                         9     On time
## 14:42  London Paddington                       15A   On time
## 14:43  London Paddington                       10    On time
## 14:45  London Paddington                       11A   On time
## 14:45  Newcastle                               3     On time
##        via Leeds                               
## 14:48  London Paddington                       10    On time
## 14:48  Oxford                                  9B    On time
## 14:50  Bournemouth                             12B   On time
## 14:50  Didcot Parkway                          13B   On time
## 14:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:55  Weston-super-Mare                       9     On time
## 14:58  Cheltenham Spa                          8     On time
## 14:59  Abbey Wood                              14    On time
## 15:00  London Paddington                       10A   On time
## 15:02  Paignton                                7     On time
## 15:04  London Paddington                       11    On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
