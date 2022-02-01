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

## Example (Last rendered on 2022-02-01 08:04)

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
## Reading (RDG) Station Board on 2022-02-01 08:04:29
## Time   From                                    Plat  Expected
## 07:11  London Paddington                       9     Delayed
## 07:17  Swansea                                 10A   07:42
## 07:28  Cheltenham Spa                          -     07:57
## 07:31  Frome                                   -     07:39
## 07:38  Bristol Temple Meads                    -     08:10
## 07:43  Didcot Parkway                          -     Delayed
## 07:44  London Paddington                       -     Delayed
## 07:46  London Paddington                       -     Delayed
## 07:49  Swansea                                 -     08:07
## 07:51  London Paddington                       -     Delayed
## 07:56  London Paddington                       -     Delayed
## 07:59  Maidenhead                              -     08:07
## 08:01  Plymouth                                -     08:22
## 08:06  Basingstoke                             -     On time
## 08:07  Slough                                  -     Cancelled
## 08:09  Bournemouth                             -     On time
## 08:10  Didcot Parkway                          -     08:28
## 08:10  London Waterloo                         -     On time
## 08:10  Oxford                                  -     Delayed
## 08:13  London Paddington                       -     Cancelled
## 08:14  London Paddington                       -     Delayed
## 08:14  Worcester Shrub Hill                    -     08:24
## 08:16  London Paddington                       -     Delayed
## 08:16  Redhill                                 -     On time
## 08:18  Swansea                                 -     08:47
## 08:19  Maidenhead                              -     08:23
## 08:22  Newbury                                 -     On time
## 08:25  London Paddington                       -     On time
## 08:26  Cheltenham Spa                          -     On time
## 08:27  London Paddington                       -     On time
## 08:28  London Paddington                       -     Cancelled
## 08:34  Gatwick Airport                         -     On time
## 08:37  London Paddington                       -     On time
## 08:39  Weston-super-Mare                       -     09:02
## 08:41  London Waterloo                         -     On time
## 08:42  Basingstoke                             -     On time
## 08:43  London Paddington                       -     On time
## 08:43  London Paddington                       -     Cancelled
## 08:44  Didcot Parkway                          -     On time
## 08:46  Manchester Piccadilly                   -     On time
## 08:50  London Paddington                       -     Delayed
## 08:51  London Paddington                       -     On time
## 08:53  Plymouth                                -     On time
## 08:55  London Paddington                       -     On time
## 08:58  London Paddington                       -     Cancelled
## 08:59  Maidenhead                              -     On time
## 09:01  Didcot Parkway                          -     On time
## 09:02  Basingstoke                             -     On time
## 09:04  Redhill                                 -     On time
## 09:04  Taunton                                 -     On time
## 09:05  Bournemouth                             -     On time
## 09:09  Bedwyn                                  -     On time
## 09:11  Hereford                                -     On time
## 09:11  London Paddington                       -     On time
## 09:13  London Paddington                       -     Cancelled
## 09:14  London Paddington                       -     On time
## 09:15  London Waterloo                         -     On time
## 09:16  London Paddington                       -     On time
## 09:19  Swansea                                 -     On time
## 09:24  Gatwick Airport                         -     Cancelled
## 09:24  Oxford                                  -     On time
## 09:25  London Paddington                       -     On time
## 09:28  London Paddington                       -     Cancelled
## 09:30  Penzance                                -     09:36
## 09:32  Worcester Shrub Hill                    -     On time
## 09:37  Didcot Parkway                          -     On time
## 09:39  Taunton                                 -     09:47
## 09:40  London Waterloo                         -     On time
## 09:40  Nottingham                              -     On time
## 09:43  London Paddington                       -     On time
## 09:44  London Paddington                       -     On time
## 09:45  Swansea                                 -     On time
## 09:46  Basingstoke                             -     On time
## 09:46  London Paddington                       -     On time
## 09:46  Shalford                                -     On time
## 09:52  London Paddington                       -     On time
## 09:53  Banbury                                 -     On time
## 09:54  Gatwick Airport                         -     On time
## 09:55  Newbury                                 -     On time
## 09:55  Worcester Shrub Hill                    -     On time
## 09:56  London Paddington                       -     On time
## 08:21  Heathrow Central Bus Stn                -     On time
## 09:21  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-01 08:04:35
## Time   To                                      Plat  Expected
## 07:13  Swansea                                 9     Delayed
## 07:20  London Paddington                       10A   Delayed
## 07:30  Ealing Broadway                         13    Delayed
## 07:31  London Paddington                       -     Delayed
## 07:34  London Paddington                       -     Delayed
## 07:41  London Paddington                       -     08:11
## 07:45  London Paddington                       -     Delayed
## 07:49  Oxford                                  -     Delayed
## 07:51  Didcot Parkway                          -     Delayed
## 07:51  London Paddington                       -     08:08
## 07:53  Cheltenham Spa                          -     Delayed
## 08:00  Bristol Temple Meads                    -     Delayed
## 08:00  Ealing Broadway                         -     Cancelled
## 08:03  Ealing Broadway                         -     Cancelled
## 08:03  Newbury                                 -     On time
## 08:12  London Waterloo                         -     On time
## 08:13  Swansea                                 -     Delayed
## 08:14  London Paddington                       -     Delayed
## 08:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       -     08:25
## 08:17  London Paddington                       -     08:29
## 08:19  Great Malvern                           -     Delayed
## 08:20  London Paddington                       -     08:48
## 08:20  Maidenhead                              -     On time
## 08:20  Redhill                                 -     On time
## 08:22  Ealing Broadway                         -     Cancelled
## 08:23  Basingstoke                             -     On time
## 08:26  Didcot Parkway                          -     Delayed
## 08:27  Bristol Temple Meads                    -     On time
## 08:29  London Paddington                       -     On time
## 08:29  Penzance                                -     On time
## 08:31  London Paddington                       -     On time
## 08:33  Ealing Broadway                         -     Cancelled
## 08:38  Newbury                                 -     On time
## 08:41  London Paddington                       -     09:03
## 08:42  London Waterloo                         -     On time
## 08:46  Oxford                                  -     On time
## 08:48  London Paddington                       -     On time
## 08:52  Bournemouth                             -     On time
## 08:52  Ealing Broadway                         -     On time
## 08:53  Cheltenham Spa                          -     On time
## 08:53  Didcot Parkway                          -     Delayed
## 08:56  London Paddington                       -     On time
## 08:57  Bristol Temple Meads                    -     On time
## 08:59  Basingstoke                             -     On time
## 09:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 09:03  Ealing Broadway                         -     09:13
## 09:06  London Paddington                       -     On time
## 09:08  Ealing Broadway                         -     On time
## 09:11  London Paddington                       -     On time
## 09:12  London Waterloo                         -     On time
## 09:13  London Paddington                       -     On time
## 09:13  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 -     On time
## 09:13  Swansea                                 -     On time
## 09:18  Great Malvern                           -     On time
## 09:20  London Paddington                       -     On time
## 09:20  Redhill                                 -     On time
## 09:22  Ealing Broadway                         -     On time
## 09:23  Didcot Parkway                          -     On time
## 09:26  London Paddington                       -     On time
## 09:27  Bristol Temple Meads                    -     On time
## 09:29  Plymouth                                -     On time
## 09:32  Basingstoke                             -     On time
## 09:32  London Paddington                       -     09:38
## 09:35  London Paddington                       -     On time
## 09:36  Bedwyn                                  -     On time
## 09:42  London Paddington                       -     09:48
## 09:42  London Waterloo                         -     On time
## 09:45  Ealing Broadway                         -     On time
## 09:47  London Paddington                       -     On time
## 09:48  Oxford                                  -     On time
## 09:52  Ealing Broadway                         -     On time
## 09:54  Cheltenham Spa                          -     On time
## 09:55  Didcot Parkway                          -     On time
## 09:57  London Paddington                       -     On time
## 09:58  Bristol Temple Meads                    -     On time
## 10:02  Paignton                                -     On time
## 09:00  Heathrow Central Bus Stn                -     On time
## 10:00  Heathrow Central Bus Stn                -     On time
```
