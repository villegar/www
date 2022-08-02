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

## Example (Last rendered on 2022-08-02 14:04)

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
## Reading (RDG) Station Board on 2022-08-02 14:04:40
## Time   From                                    Plat  Expected
## 14:40  Bristol Temple Meads                    10    14:59
## 14:45  Swansea                                 10    15:10
## 14:55  Worcester Shrub Hill                    10    15:00
## 14:58  Penzance                                11    15:19
## 14:59  Didcot Parkway                          15    15:18
## 15:00  London Paddington                       7     15:02
## 15:05  Bournemouth                             8     15:10
## 15:09  Bristol Temple Meads                    10    Delayed
## 15:11  London Paddington                       9     15:13
## 15:11  London Waterloo                         4     15:14
## 15:13  London Paddington                       14    On time
## 15:15  Cardiff Central                         11    15:21
## 15:16  London Paddington                       9     On time
## 15:17  London Paddington                       12    On time
## 15:22  Newbury                                 11    On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10    On time
## 15:26  Basingstoke                             2     On time
## 15:30  Cheltenham Spa                          10    15:35
## 15:33  London Paddington                       7     On time
## 15:33  Redhill                                 5     On time
## 15:35  Didcot Parkway                          15    On time
## 15:36  Newbury                                 1     On time
## 15:39  Bristol Temple Meads                    11    Delayed
## 15:39  London Paddington                       14    On time
## 15:41  London Paddington                       9     On time
## 15:41  London Waterloo                         6     15:47
## 15:41  Manchester Piccadilly                   8     On time
## 15:44  Swansea                                 10    On time
## 15:46  London Paddington                       12    On time
## 15:46  London Paddington                       9     On time
## 15:47  Exeter St Davids                        11    15:49
## 15:51  Gatwick Airport                         4     On time
## 15:51  London Paddington                       9     On time
## 15:53  Basingstoke                             2     On time
## 15:53  Hereford                                10    On time
## 15:56  London Paddington                       9     16:04
## 15:57  Newquay                                 11    16:22
## 16:07  Didcot Parkway                          15    On time
## 16:09  Bristol Temple Meads                    10    Delayed
## 16:11  London Paddington                       9     On time
## 16:11  London Paddington                       14    On time
## 16:11  London Waterloo                         4     On time
## 16:16  Cardiff Central                         11    On time
## 16:18  Basingstoke                             2     On time
## 16:21  London Paddington                       12    On time
## 16:22  Newbury                                 11    On time
## 16:24  Oxford                                  10    On time
## 16:25  London Paddington                       -     On time
## 16:27  London Paddington                       -     On time
## 16:29  Cheltenham Spa                          -     On time
## 16:31  Didcot Parkway                          -     On time
## 16:32  Newbury                                 -     On time
## 16:33  London Paddington                       -     On time
## 16:33  Redhill                                 -     On time
## 16:39  Bristol Temple Meads                    -     On time
## 16:39  London Paddington                       -     On time
## 16:41  London Paddington                       -     On time
## 16:41  London Waterloo                         -     On time
## 16:41  Manchester Piccadilly                   -     On time
## 16:42  London Paddington                       -     On time
## 16:43  Paignton                                -     On time
## 16:45  Swansea                                 -     On time
## 16:46  London Paddington                       -     On time
## 16:50  Basingstoke                             -     On time
## 16:54  Worcester Foregate Street               -     On time
## 16:55  Newbury                                 -     On time
## 16:56  London Paddington                       -     On time
## 16:56  London Paddington                       -     On time
## 16:59  London Paddington                       -     On time
## 17:03  Gatwick Airport                         -     On time
## 15:31  Heathrow Central Bus Stn                BUS   On time
## 16:06  Heathrow Central Bus Stn                BUS   On time
## 16:41  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-02 14:04:45
## Time   To                                      Plat  Expected
## 14:43  London Paddington                       10    Delayed
## 14:48  London Paddington                       10    15:11
## 14:57  London Paddington                       10    15:04
## 15:02  Paignton                                7     15:04
## 15:04  London Paddington                       11    15:20
## 15:05  Basingstoke                             2     On time
## 15:10  Newbury                                 1     On time
## 15:12  Ealing Broadway                         15    15:19
## 15:12  London Waterloo                         6     On time
## 15:13  London Paddington                       10    Delayed
## 15:13  Swansea                                 9     15:14
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:18  London Paddington                       11    15:22
## 15:18  Redhill                                 5     On time
## 15:18  Worcester Foregate Street               9     On time
## 15:23  Didcot Parkway                          12    On time
## 15:24  London Paddington                       11    On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  Ealing Broadway                         14    On time
## 15:27  London Paddington                       10    On time
## 15:29  Penzance                                7     On time
## 15:32  Basingstoke                             2     On time
## 15:34  London Paddington                       10    15:36
## 15:37  Newbury                                 7     On time
## 15:42  Ealing Broadway                         15    On time
## 15:42  London Waterloo                         4     On time
## 15:43  Cardiff Central                         9     On time
## 15:43  London Paddington                       11    Delayed
## 15:45  London Paddington                       10    On time
## 15:48  Worcester Foregate Street               9     On time
## 15:50  London Paddington                       11    On time
## 15:50  Newbury                                 3     On time
## 15:51  Didcot Parkway                          12    On time
## 15:53  Cheltenham Spa                          9     On time
## 15:56  London Paddington                       10    On time
## 15:58  Ealing Broadway                         14    On time
## 15:58  Weston-super-Mare                       9     16:05
## 16:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:04  London Paddington                       11    16:23
## 16:07  Basingstoke                             2     On time
## 16:12  London Paddington                       10    Delayed
## 16:12  London Waterloo                         6     On time
## 16:12  Newbury                                 1     On time
## 16:13  Swansea                                 9     On time
## 16:14  Ealing Broadway                         15    On time
## 16:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Ealing Broadway                         13    On time
## 16:18  London Paddington                       11    On time
## 16:19  Great Malvern                           9     On time
## 16:20  Redhill                                 5     On time
## 16:24  London Paddington                       11    On time
## 16:25  Didcot Parkway                          12    On time
## 16:27  Bristol Temple Meads                    -     On time
## 16:27  London Paddington                       10    On time
## 16:28  Ealing Broadway                         -     On time
## 16:29  Penzance                                -     On time
## 16:32  London Paddington                       -     On time
## 16:33  Basingstoke                             -     On time
## 16:37  Newbury                                 -     On time
## 16:38  Ealing Broadway                         -     On time
## 16:41  London Waterloo                         -     On time
## 16:42  London Paddington                       -     On time
## 16:43  Swansea                                 -     On time
## 16:45  London Paddington                       -     On time
## 16:47  London Paddington                       -     On time
## 16:48  Ealing Broadway                         -     On time
## 16:48  Oxford                                  -     On time
## 16:50  Didcot Parkway                          -     On time
## 16:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 16:52  Bournemouth                             -     On time
## 16:57  London Paddington                       -     On time
## 16:58  Ealing Broadway                         -     On time
## 16:58  Taunton                                 -     On time
## 17:02  Plymouth                                -     On time
## 15:20  Heathrow Central Bus Stn                BUS   On time
## 15:55  Heathrow Central Bus Stn                BUS   On time
## 16:30  Heathrow Central Bus Stn                -     On time
```
