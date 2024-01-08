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

## Example (Last rendered on 2024-01-08 09:04)

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
## Reading (RDG) Station Board on 2024-01-08 09:04:58.307559
## Time   From                                    Plat  Expected
## 08:55  London Paddington                       8B    09:02
## 09:03  London Paddington                       7     09:00
## 09:07  Bournemouth                             8     On time
## 09:09  Newbury                                 11    Delayed
## 09:10  Taunton                                 10A   On time
## 09:11  Abbey Wood                              14    On time
## 09:11  London Paddington                       9B    On time
## 09:13  London Waterloo                         6     On time
## 09:14  Great Malvern                           10A   On time
## 09:16  London Paddington                       9B    On time
## 09:16  London Paddington                       -     Cancelled
## 09:19  Swansea                                 11    09:27
## 09:23  London Paddington                       9     On time
## 09:24  Oxford                                  10A   On time
## 09:26  Abbey Wood                              13    On time
## 09:27  London Paddington                       7     On time
## 09:30  Gatwick Airport                         5     On time
## 09:30  Penzance                                11A   Delayed
## 09:31  London Paddington                       -     Cancelled
## 09:32  Worcester Shrub Hill                    10A   On time
## 09:37  Didcot Parkway                          15    On time
## 09:38  Abbey Wood                              14    On time
## 09:39  Taunton                                 10    On time
## 09:40  Nottingham                              -     Cancelled
## 09:41  London Paddington                       9B    On time
## 09:41  Newbury                                 11    On time
## 09:43  London Waterloo                         6     09:47
## 09:45  Swansea                                 10A   On time
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       9     On time
## 09:46  London Paddington                       -     Cancelled
## 09:53  London Paddington                       9B    On time
## 09:55  London Paddington                       8     On time
## 09:55  Newbury Racecourse                      1     On time
## 09:55  Worcester Shrub Hill                    10    On time
## 10:01  London Paddington                       7     On time
## 10:02  Plymouth                                11    On time
## 10:03  Redhill                                 4     On time
## 10:06  Swansea                                 10    On time
## 10:10  Abbey Wood                              14    On time
## 10:10  Bournemouth                             7B    On time
## 10:10  Didcot Parkway                          15    On time
## 10:11  London Paddington                       9B    On time
## 10:12  London Waterloo                         5     On time
## 10:13  Newbury                                 11    On time
## 10:14  Bristol Temple Meads                    10    On time
## 10:14  London Paddington                       -     Cancelled
## 10:17  London Paddington                       9     On time
## 10:19  Basingstoke                             2     On time
## 10:20  Oxford                                  11    On time
## 10:23  London Paddington                       9     On time
## 10:27  London Paddington                       8     On time
## 10:29  Cheltenham Spa                          10A   On time
## 10:30  Gatwick Airport                         4     On time
## 10:31  London Paddington                       -     Cancelled
## 10:36  Didcot Parkway                          15    On time
## 10:38  London Paddington                       9     On time
## 10:38  Newbury Racecourse                      1     On time
## 10:40  Abbey Wood                              14    On time
## 10:40  Bristol Temple Meads                    10    On time
## 10:43  London Waterloo                         6     On time
## 10:45  Carmarthen                              10    On time
## 10:46  London Paddington                       8     On time
## 10:46  Manchester Piccadilly                   7     On time
## 10:49  London Paddington                       -     Cancelled
## 10:50  Newbury                                 11    On time
## 10:53  London Paddington                       8     On time
## 10:55  Basingstoke                             2     On time
## 10:55  London Paddington                       9     On time
## 10:56  Great Malvern                           10    On time
## 10:59  London Paddington                       7     On time
## 09:15  Heathrow Airport T3 (Bus)               BUS   On time
## 09:45  Heathrow Airport T3 (Bus)               BUS   On time
## 10:15  Heathrow Airport T3 (Bus)               BUS   On time
## 10:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-08 09:05:00.65511
## Time   To                                      Plat  Expected
## 08:58  Cheltenham Spa                          8B    09:04
## 09:05  Westbury                                7     On time
## 09:09  London Waterloo                         6     On time
## 09:11  London Paddington                       10A   On time
## 09:13  London Paddington                       -     Cancelled
## 09:13  Newbury Racecourse                      1     On time
## 09:13  Swansea                                 9B    On time
## 09:16  Abbey Wood                              -     Cancelled
## 09:16  London Paddington                       10A   On time
## 09:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Great Malvern                           9B    On time
## 09:19  Gatwick Airport                         5     On time
##        via Guildford                           
## 09:20  London Paddington                       11    09:28
## 09:22  Didcot Parkway                          12    On time
## 09:25  Bristol Temple Meads                    9     On time
## 09:28  Abbey Wood                              14    On time
## 09:28  London Paddington                       10A   On time
## 09:30  Plymouth                                7     On time
## 09:32  London Paddington                       11A   Delayed
## 09:33  Basingstoke                             2     On time
## 09:35  London Paddington                       10A   On time
## 09:39  London Waterloo                         6     On time
## 09:41  Newbury                                 -     Cancelled
## 09:42  London Paddington                       -     Cancelled
## 09:42  London Paddington                       10    On time
## 09:43  Cardiff Central                         9B    On time
## 09:44  London Paddington                       -     Cancelled
## 09:47  London Paddington                       10A   On time
## 09:48  Oxford                                  9     On time
## 09:52  Bournemouth                             -     Cancelled
## 09:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 09:55  Bristol Temple Meads                    9B    On time
## 09:55  Didcot Parkway                          13    On time
## 09:58  Cheltenham Spa                          8     On time
## 09:58  London Paddington                       10    On time
## 09:59  Abbey Wood                              14    On time
## 10:03  Paignton                                7     On time
## 10:04  London Paddington                       11    On time
## 10:07  Basingstoke                             2     On time
## 10:08  London Paddington                       10    On time
## 10:09  London Waterloo                         6     On time
## 10:12  London Paddington                       -     Cancelled
## 10:12  Newbury Racecourse                      1     On time
## 10:13  Carmarthen                              9B    On time
## 10:14  London Paddington                       11    On time
## 10:16  London Paddington                       10    On time
## 10:16  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9     On time
## 10:23  Didcot Parkway                          12    On time
## 10:24  Gatwick Airport                         4     On time
##        via Guildford                           
## 10:25  Bristol Temple Meads                    9     On time
## 10:26  London Paddington                       11    On time
## 10:29  Abbey Wood                              14    On time
## 10:29  Penzance                                8     On time
## 10:33  Basingstoke                             2     On time
## 10:34  London Paddington                       10A   On time
## 10:38  London Paddington                       15    On time
## 10:39  London Waterloo                         5     On time
## 10:39  Newbury                                 -     Cancelled
## 10:40  Cardiff Central                         9     On time
## 10:42  London Paddington                       10    On time
## 10:47  London Paddington                       10    On time
## 10:48  Oxford                                  8     On time
## 10:52  Bournemouth                             7     On time
## 10:53  Didcot Parkway                          15    On time
## 10:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 10:54  London Paddington                       11    On time
## 10:55  Weston-super-Mare                       8     On time
## 10:58  Cheltenham Spa                          9     On time
## 10:59  Abbey Wood                              14    On time
## 10:59  London Paddington                       10    On time
## 11:01  Exeter St Davids                        7     On time
## 11:04  London Paddington                       11    On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
