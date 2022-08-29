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

## Example (Last rendered on 2022-08-29 16:03)

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
## Reading (RDG) Station Board on 2022-08-29 16:03:59
## Time   From                                    Plat  Expected
## 16:43  Paignton                                11A   17:18
## 16:56  London Paddington                       9     17:05
## 17:01  Penzance                                10    17:48
## 17:03  Gatwick Airport                         5     17:13
## 17:04  Didcot Parkway                          15    17:01
## 17:06  Bournemouth                             8     17:08
## 17:09  Bristol Temple Meads                    11    17:14
## 17:11  London Paddington                       9     On time
## 17:12  London Waterloo                         4     Delayed
## 17:14  London Paddington                       14    17:16
## 17:17  Cardiff Central                         11    On time
## 17:19  London Paddington                       9B    On time
## 17:22  London Paddington                       12    On time
## 17:22  Newbury                                 11A   On time
## 17:24  Oxford                                  10A   On time
## 17:25  London Paddington                       8     On time
## 17:26  Basingstoke                             2     On time
## 17:27  London Paddington                       7     17:36
## 17:29  Cheltenham Spa                          10A   17:31
## 17:31  Didcot Parkway                          15    On time
## 17:34  Newbury                                 1     On time
## 17:35  London Paddington                       7B    On time
## 17:35  Redhill                                 5     On time
## 17:41  London Paddington                       9     On time
## 17:41  London Paddington                       14    On time
## 17:41  London Waterloo                         6     17:43
## 17:41  Manchester Piccadilly                   7     On time
## 17:42  Exeter St Davids                        11A   On time
## 17:43  Bristol Temple Meads                    10    On time
## 17:46  Basingstoke                             2     On time
## 17:47  Swansea                                 11    On time
## 17:50  London Paddington                       13    On time
## 17:53  London Paddington                       9B    On time
## 17:55  London Paddington                       7     On time
## 17:56  Hereford                                10A   On time
## 17:57  Plymouth                                11    18:23
## 17:58  London Paddington                       12    On time
## 18:02  Redhill                                 4     On time
## 18:03  Didcot Parkway                          15    On time
## 18:05  Bournemouth                             12B   On time
## 18:09  Bristol Temple Meads                    11    On time
## 18:11  London Paddington                       9     On time
## 18:11  London Paddington                       14    On time
## 18:11  London Waterloo                         5     On time
## 18:17  Cardiff Central                         11    On time
## 18:19  London Paddington                       9     On time
## 18:20  Basingstoke                             2     On time
## 18:25  Newbury                                 11A   On time
## 18:26  London Paddington                       12    On time
## 18:26  London Paddington                       8     On time
## 18:26  Oxford                                  10    On time
## 18:29  Didcot Parkway                          15    On time
## 18:30  Cheltenham Spa                          11A   On time
## 18:33  London Paddington                       7     On time
## 18:33  Redhill                                 4     On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:41  London Paddington                       14    On time
## 18:41  London Waterloo                         6     On time
## 18:42  London Paddington                       9     On time
## 18:43  Manchester Piccadilly                   8     On time
## 18:47  Swansea                                 10    On time
## 18:49  London Paddington                       9     On time
## 18:50  Basingstoke                             3     On time
## 18:53  London Paddington                       7     On time
## 18:57  Great Malvern                           10A   On time
## 18:57  London Paddington                       9     On time
## 18:57  London Paddington                       12    On time
## 18:57  Penzance                                11    On time
## 18:59  London Paddington                       7     On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-29 16:04:03
## Time   To                                      Plat  Expected
## 16:45  London Paddington                       11A   17:19
## 17:00  Taunton                                 9     17:06
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       15    On time
## 17:11  London Paddington                       11    17:15
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9     On time
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 17:18  London Paddington                       11    On time
## 17:20  Great Malvern                           9B    On time
## 17:20  Redhill                                 5     On time
## 17:24  London Paddington                       11A   On time
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       10A   On time
## 17:28  London Paddington                       14    On time
## 17:29  Penzance                                7     17:37
## 17:32  London Paddington                       10A   On time
## 17:38  Basingstoke                             2     On time
## 17:41  Newbury                                 7B    On time
## 17:42  London Paddington                       15    On time
## 17:42  London Waterloo                         4     On time
## 17:43  London Paddington                       11A   On time
## 17:43  Swansea                                 9     On time
## 17:46  London Paddington                       10    On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       11    On time
## 17:52  Bournemouth                             7     On time
## 17:55  Cheltenham Spa                          9B    On time
## 17:57  Basingstoke                             2     On time
## 17:57  Hereford                                13    On time
## 17:58  London Paddington                       14    On time
## 17:58  London Paddington                       11    18:24
## 18:00  Didcot Parkway                          12    On time
## 18:00  London Paddington                       10A   On time
## 18:00  Taunton                                 7     On time
## 18:07  Newbury                                 1     On time
## 18:08  London Paddington                       15    On time
## 18:12  London Paddington                       11    On time
## 18:12  London Waterloo                         6     On time
## 18:13  Carmarthen                              9     On time
## 18:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Wilmslow                 
## 18:20  London Paddington                       11    On time
## 18:20  Redhill                                 4     On time
## 18:21  Worcester Foregate Street               9     On time
## 18:26  London Paddington                       11A   On time
## 18:28  Bristol Temple Meads                    8     On time
## 18:28  London Paddington                       14    On time
## 18:28  London Paddington                       10    On time
## 18:29  Penzance                                7     On time
## 18:32  Basingstoke                             2     On time
## 18:32  Didcot Parkway                          12    On time
## 18:32  London Paddington                       11A   On time
## 18:37  London Paddington                       15    On time
## 18:38  Newbury                                 7     On time
## 18:42  London Waterloo                         5     On time
## 18:43  London Paddington                       10    On time
## 18:43  Swansea                                 9     On time
## 18:49  London Paddington                       10    On time
## 18:50  Banbury                                 9     On time
## 18:55  Cheltenham Spa                          7     On time
## 18:58  London Paddington                       14    On time
## 18:58  London Paddington                       11    On time
## 18:59  Didcot Parkway                          12    On time
## 19:00  London Paddington                       10A   On time
## 19:00  Weston-super-Mare                       9     On time
## 19:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:01  Plymouth                                7     On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
