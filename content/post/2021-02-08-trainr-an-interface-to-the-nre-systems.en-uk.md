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

## Example (Last rendered on 2022-05-16 06:04)

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
## Reading (RDG) Station Board on 2022-05-16 06:04:42
## Time   From                                    Plat  Expected
## 07:00  London Paddington                       -     On time
## 07:06  London Paddington                       -     06:59
## 07:08  Bristol Temple Meads                    -     On time
## 07:09  Hereford                                -     On time
## 07:11  London Paddington                       -     07:15
## 07:11  London Paddington                       -     On time
## 07:11  London Waterloo                         -     On time
## 07:12  Didcot Parkway                          -     On time
## 07:16  London Paddington                       -     07:18
## 07:16  London Paddington                       -     On time
## 07:18  Swansea                                 -     On time
## 07:21  Newbury                                 -     On time
## 07:25  London Paddington                       -     On time
## 07:27  London Paddington                       -     On time
## 07:27  London Paddington                       -     On time
## 07:28  Cheltenham Spa                          -     On time
## 07:29  Basingstoke                             -     On time
## 07:31  Frome                                   -     On time
## 07:32  London Paddington                       -     07:35
## 07:33  Oxford                                  -     On time
## 07:34  Gatwick Airport                         -     On time
## 07:38  Bristol Temple Meads                    -     On time
## 07:38  London Paddington                       -     On time
## 07:43  Birmingham New Street                   -     On time
## 07:43  Didcot Parkway                          -     On time
## 07:44  London Paddington                       -     On time
## 07:46  London Paddington                       -     On time
## 07:46  London Waterloo                         -     On time
## 07:47  Basingstoke                             -     On time
## 07:48  London Paddington                       -     On time
## 07:49  Swansea                                 -     On time
## 07:51  London Paddington                       -     On time
## 07:51  Newbury                                 -     On time
## 07:54  Hereford                                -     On time
## 07:55  Shalford                                -     On time
## 07:56  London Paddington                       -     On time
## 07:57  London Paddington                       -     On time
## 08:01  Plymouth                                -     On time
## 08:06  Basingstoke                             -     On time
## 08:09  Bournemouth                             -     On time
## 08:09  Oxford                                  -     On time
## 08:10  Didcot Parkway                          -     On time
## 08:11  London Paddington                       -     On time
## 08:11  London Waterloo                         -     On time
## 08:13  London Paddington                       -     On time
## 08:14  Worcester Shrub Hill                    -     On time
## 08:16  London Paddington                       -     On time
## 08:16  London Paddington                       -     On time
## 08:16  Redhill                                 -     On time
## 08:18  Swansea                                 -     On time
## 08:22  Newbury                                 -     On time
## 08:25  London Paddington                       -     On time
## 08:26  Cheltenham Spa                          -     On time
## 08:27  London Paddington                       -     On time
## 08:29  London Paddington                       -     On time
## 08:30  Plymouth                                -     On time
## 08:34  Gatwick Airport                         -     On time
## 08:35  London Paddington                       -     On time
## 08:39  Weston-super-Mare                       -     On time
## 08:41  London Paddington                       -     On time
## 08:42  Basingstoke                             -     On time
## 08:42  London Waterloo                         -     On time
## 08:43  London Paddington                       -     On time
## 08:45  Didcot Parkway                          -     On time
## 08:45  London Paddington                       -     On time
## 08:46  Manchester Piccadilly                   -     On time
## 08:49  London Paddington                       -     On time
## 08:51  London Paddington                       -     On time
## 08:53  Plymouth                                -     On time
## 08:55  London Paddington                       -     On time
## 08:56  London Paddington                       -     On time
## 09:02  Basingstoke                             -     On time
## 07:24  Heathrow Central Bus Stn                -     On time
## 08:26  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-16 06:04:46
## Time   To                                      Plat  Expected
## 06:50  Gatwick Airport                         -     Delayed
##        via Guildford                           
## 07:10  London Paddington                       -     On time
## 07:10  Newbury                                 -     On time
## 07:11  London Waterloo                         -     On time
## 07:12  London Paddington                       -     On time
## 07:13  London Paddington                       -     On time
## 07:13  Swansea                                 -     On time
## 07:14  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 07:17  London Paddington                       -     On time
## 07:18  Great Malvern                           -     On time
## 07:20  London Paddington                       -     On time
## 07:20  Redhill                                 -     On time
## 07:24  London Paddington                       -     On time
## 07:25  Didcot Parkway                          -     On time
## 07:26  London Paddington                       -     On time
## 07:27  Bristol Temple Meads                    -     On time
## 07:30  Paignton                                -     On time
## 07:31  London Paddington                       -     On time
## 07:34  London Paddington                       -     On time
## 07:34  Newbury                                 -     07:36
## 07:37  Basingstoke                             -     On time
## 07:37  London Paddington                       -     On time
## 07:39  Cardiff Central                         -     On time
## 07:40  London Paddington                       -     On time
## 07:41  London Paddington                       -     On time
## 07:42  London Waterloo                         -     On time
## 07:46  London Paddington                       -     On time
## 07:49  Oxford                                  -     On time
## 07:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 07:51  Didcot Parkway                          -     On time
## 07:51  London Paddington                       -     On time
## 07:52  Bournemouth                             -     On time
## 07:53  Cheltenham Spa                          -     On time
## 07:56  London Paddington                       -     On time
## 07:56  London Paddington                       -     On time
## 08:00  Basingstoke                             -     On time
## 08:00  Bristol Temple Meads                    -     On time
## 08:03  Newbury                                 -     On time
## 08:10  London Paddington                       -     On time
## 08:10  London Paddington                       -     On time
## 08:11  London Waterloo                         -     On time
## 08:13  Swansea                                 -     On time
## 08:14  London Paddington                       -     On time
## 08:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       -     On time
## 08:17  London Paddington                       -     On time
## 08:19  Great Malvern                           -     On time
## 08:20  Guildford                               -     On time
## 08:20  London Paddington                       -     On time
## 08:23  Basingstoke                             -     On time
## 08:25  London Paddington                       -     On time
## 08:26  Didcot Parkway                          -     On time
## 08:27  Bristol Temple Meads                    -     On time
## 08:29  London Paddington                       -     On time
## 08:29  Penzance                                -     On time
## 08:31  London Paddington                       -     On time
## 08:32  London Paddington                       -     On time
## 08:36  Newbury                                 -     On time
## 08:36  Redhill                                 -     On time
## 08:41  London Paddington                       -     On time
## 08:42  London Paddington                       -     On time
## 08:42  London Waterloo                         -     On time
## 08:43  Cardiff Central                         -     On time
## 08:46  Newbury                                 -     On time
## 08:46  Oxford                                  -     On time
## 08:47  London Paddington                       -     On time
## 08:52  Bournemouth                             -     On time
## 08:53  Cheltenham Spa                          -     On time
## 08:53  Didcot Parkway                          -     On time
## 08:56  London Paddington                       -     On time
## 08:57  Bristol Temple Meads                    -     On time
## 08:57  London Paddington                       -     On time
## 08:59  Basingstoke                             -     On time
## 09:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 07:10  Heathrow Central Bus Stn                -     On time
## 07:45  Heathrow Central Bus Stn                -     On time
## 08:20  Heathrow Central Bus Stn                -     On time
## 08:55  Heathrow Central Bus Stn                -     On time
```
