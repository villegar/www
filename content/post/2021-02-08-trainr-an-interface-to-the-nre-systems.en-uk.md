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

## Example (Last rendered on 2023-03-29 18:11)

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
## Reading (RDG) Station Board on 2023-03-29 18:11:04
## Time   From                                    Plat  Expected
## 18:53  London Paddington                       12B   19:08
## 18:57  Plymouth                                11    19:21
## 18:57  Worcester Shrub Hill                    11    19:09
## 18:59  London Paddington                       7     19:17
## 19:05  Didcot Parkway                          15    19:19
## 19:09  Abbey Wood                              13    19:15
## 19:10  Weston-super-Mare                       10    19:21
## 19:11  London Paddington                       -     Delayed
## 19:14  Abbey Wood                              14    Delayed
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         -     Cancelled
## 19:17  London Waterloo                         6     On time
## 19:23  Worcester Foregate Street               10    Delayed
## 19:26  London Paddington                       8     On time
## 19:28  Didcot Parkway                          15    On time
## 19:28  London Paddington                       7     19:30
## 19:31  Cheltenham Spa                          11    On time
## 19:33  Redhill                                 4     On time
## 19:34  London Paddington                       12    On time
## 19:35  Basingstoke                             2     On time
## 19:35  London Paddington                       -     Cancelled
## 19:39  Bristol Temple Meads                    -     Cancelled
## 19:40  Abbey Wood                              13    On time
## 19:41  London Paddington                       -     Delayed
## 19:41  Manchester Piccadilly                   7     On time
## 19:44  Abbey Wood                              14    On time
## 19:44  London Waterloo                         5     On time
## 19:46  Swansea                                 10    20:01
## 19:53  London Paddington                       -     Cancelled
## 19:54  Plymouth                                11    20:07
## 19:54  Worcester Foregate Street               10    19:59
## 19:55  London Paddington                       -     Cancelled
## 19:56  London Paddington                       -     Cancelled
## 19:58  Didcot Parkway                          -     On time
## 20:00  Basingstoke                             1     On time
## 20:04  Gatwick Airport                         4     On time
## 20:04  Newbury                                 -     On time
## 20:07  Bournemouth                             8     On time
## 20:10  Bristol Temple Meads                    10    On time
## 20:11  London Paddington                       -     Delayed
## 20:13  Abbey Wood                              14    On time
## 20:14  London Waterloo                         6     On time
## 20:17  London Paddington                       -     Delayed
## 20:17  London Paddington                       -     Delayed
## 20:24  London Paddington                       -     Delayed
## 20:26  London Paddington                       -     Delayed
## 20:28  Banbury                                 -     Cancelled
## 20:32  Cheltenham Spa                          -     Cancelled
## 20:33  Didcot Parkway                          -     On time
## 20:34  Basingstoke                             -     On time
## 20:35  Redhill                                 14A   On time
## 20:36  London Paddington                       -     Cancelled
## 20:42  London Waterloo                         4     On time
## 20:42  Manchester Piccadilly                   8     On time
## 20:43  Abbey Wood                              14    On time
## 20:44  Swansea                                 10    On time
## 20:45  Newbury                                 -     On time
## 20:46  London Paddington                       -     Delayed
## 20:47  London Paddington                       -     Cancelled
## 20:51  London Paddington                       -     On time
## 20:53  Gatwick Airport                         -     On time
## 20:53  Worcester Foregate Street               -     On time
## 20:55  London Paddington                       -     Cancelled
## 21:00  Plymouth                                10    On time
## 21:03  Didcot Parkway                          -     On time
## 21:04  Basingstoke                             -     On time
## 21:10  London Paddington                       -     On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-29 18:11:08
## Time   To                                      Plat  Expected
## 18:57  Didcot Parkway                          12B   19:10
## 18:58  London Paddington                       11    19:22
## 19:00  London Paddington                       11    19:11
## 19:00  Weston-super-Mare                       9     19:24
## 19:01  Plymouth                                7     19:18
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       -     Cancelled
## 19:13  London Paddington                       10    19:22
## 19:13  Swansea                                 -     Delayed
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       -     Cancelled
## 19:20  Redhill                                 4     On time
## 19:25  Basingstoke                             -     On time
## 19:27  Abbey Wood                              14    Delayed
## 19:27  Bristol Temple Meads                    8     On time
## 19:27  London Paddington                       10    Delayed
## 19:29  Plymouth                                7     19:31
## 19:34  Didcot Parkway                          12    On time
## 19:34  London Paddington                       11    On time
## 19:37  Bedwyn                                  -     On time
## 19:37  Ealing Broadway                         15    On time
## 19:39  London Waterloo                         6     On time
## 19:41  London Paddington                       -     Cancelled
## 19:42  Newbury                                 -     On time
## 19:43  Swansea                                 -     Delayed
## 19:49  London Paddington                       10    20:02
## 19:50  Bournemouth                             7     On time
## 19:55  London Paddington                       11    20:08
## 19:55  Oxford                                  -     Cancelled
## 19:57  Abbey Wood                              13    On time
## 19:57  Basingstoke                             -     On time
## 19:57  Didcot Parkway                          -     Cancelled
## 19:58  London Paddington                       10    20:00
## 19:58  Weston-super-Mare                       -     Cancelled
## 20:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:09  London Waterloo                         5     On time
## 20:10  Newbury                                 -     On time
## 20:12  London Paddington                       10    On time
## 20:13  Swansea                                 -     Delayed
## 20:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Hereford                                -     Delayed
## 20:20  Shalford                                -     On time
## 20:21  Basingstoke                             -     On time
## 20:23  Didcot Parkway                          -     Delayed
## 20:27  Abbey Wood                              14    On time
## 20:27  Bristol Temple Meads                    -     Delayed
## 20:29  Plymouth                                -     Delayed
## 20:31  London Paddington                       -     Cancelled
## 20:36  London Paddington                       -     Cancelled
## 20:36  Newbury                                 -     On time
## 20:39  London Waterloo                         6     On time
## 20:49  Oxford                                  -     Cancelled
## 20:51  Didcot Parkway                          -     Delayed
## 20:52  Basingstoke                             -     On time
## 20:53  Cheltenham Spa                          -     On time
## 20:54  London Paddington                       10    On time
## 20:56  London Paddington                       -     On time
## 20:57  Weston-super-Mare                       -     Cancelled
## 20:58  Abbey Wood                              14    On time
## 21:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 21:05  London Paddington                       10    On time
## 21:05  Newbury                                 -     On time
## 21:09  Ealing Broadway                         -     On time
## 21:09  London Waterloo                         4     On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
