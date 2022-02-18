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

## Example (Last rendered on 2022-02-18 14:03)

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
## Reading (RDG) Station Board on 2022-02-18 14:03:51
## Time   From                                    Plat  Expected
## 13:09  Bristol Temple Meads                    10    Delayed
## 13:45  Bristol Parkway                         -     Delayed
## 13:56  London Paddington                       -     Delayed
## 14:02  Penzance                                -     Cancelled
## 14:03  Didcot Parkway                          -     Cancelled
## 14:04  Exeter St Davids                        -     Cancelled
## 14:09  Bristol Temple Meads                    -     Cancelled
## 14:10  London Waterloo                         -     Cancelled
## 14:11  London Paddington                       -     Delayed
## 14:13  London Paddington                       -     Cancelled
## 14:16  Cardiff Central                         -     Cancelled
## 14:16  London Paddington                       -     Cancelled
## 14:19  Basingstoke                             -     Cancelled
## 14:22  Bedwyn                                  -     Cancelled
## 14:24  Oxford                                  -     Cancelled
## 14:25  London Paddington                       -     Cancelled
## 14:29  Cheltenham Spa                          -     Cancelled
## 14:31  Didcot Parkway                          -     Cancelled
## 14:33  Redhill                                 -     Cancelled
## 14:34  London Paddington                       -     Cancelled
## 14:40  Bedwyn                                  -     Cancelled
## 14:40  Bristol Temple Meads                    -     Cancelled
## 14:40  London Waterloo                         -     Cancelled
## 14:40  Newbury                                 -     Cancelled
## 14:43  London Paddington                       -     Cancelled
## 14:45  Bristol Parkway                         -     On time
## 14:46  London Paddington                       -     Cancelled
## 14:49  Basingstoke                             -     Cancelled
## 14:51  Gatwick Airport                         -     Cancelled
## 14:51  London Paddington                       -     Cancelled
## 14:55  London Paddington                       -     On time
## 14:55  Worcester Shrub Hill                    -     Cancelled
## 14:59  Didcot Parkway                          -     On time
## 14:59  Penzance                                -     Cancelled
## 15:00  London Paddington                       -     Cancelled
## 15:04  Exeter St Davids                        -     Cancelled
## 15:09  Bristol Temple Meads                    -     Delayed
## 15:10  London Waterloo                         -     Cancelled
## 15:11  London Paddington                       -     Delayed
## 15:13  London Paddington                       -     Cancelled
## 15:15  Cardiff Central                         -     Cancelled
## 15:16  London Paddington                       -     Cancelled
## 15:22  Newbury                                 -     Cancelled
## 15:25  London Paddington                       -     Cancelled
## 15:25  Oxford                                  -     Cancelled
## 15:26  Basingstoke                             -     Cancelled
## 15:30  Cheltenham Spa                          -     Cancelled
## 15:32  Didcot Parkway                          -     On time
## 15:32  London Paddington                       -     Cancelled
## 15:33  Redhill                                 -     Cancelled
## 15:36  Bedwyn                                  -     Cancelled
## 15:36  Newbury                                 -     Cancelled
## 15:39  Bristol Temple Meads                    -     Cancelled
## 15:40  London Waterloo                         -     Cancelled
## 15:41  Birmingham New Street                   -     Cancelled
## 15:41  London Paddington                       -     Cancelled
## 15:43  London Paddington                       -     Cancelled
## 15:44  Bristol Parkway                         -     On time
## 15:46  London Paddington                       -     Cancelled
## 15:47  Exeter St Davids                        -     Cancelled
## 15:50  Exeter St Davids                        -     Cancelled
## 15:51  Gatwick Airport                         -     Cancelled
## 15:51  London Paddington                       -     Cancelled
## 15:53  Basingstoke                             -     Cancelled
## 15:53  Hereford                                -     Cancelled
## 15:56  London Paddington                       -     On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-18 14:03:54
## Time   To                                      Plat  Expected
## 13:14  London Paddington                       10    Delayed
## 13:48  London Paddington                       -     Delayed
## 13:58  Bristol Temple Meads                    -     Delayed
## 14:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 14:04  London Paddington                       -     Cancelled
## 14:04  London Paddington                       -     Cancelled
## 14:07  Basingstoke                             -     Cancelled
## 14:11  London Paddington                       -     Cancelled
## 14:12  Bedwyn                                  -     Cancelled
## 14:12  London Waterloo                         -     Cancelled
## 14:12  Newbury                                 -     Cancelled
## 14:13  Bristol Parkway                         -     Delayed
## 14:18  Great Malvern                           -     Cancelled
## 14:19  London Paddington                       -     Cancelled
## 14:20  Redhill                                 -     Cancelled
## 14:22  Ealing Broadway                         -     Cancelled
## 14:24  London Paddington                       -     Cancelled
## 14:25  Didcot Parkway                          -     Cancelled
## 14:27  Bristol Temple Meads                    -     Cancelled
## 14:27  London Paddington                       -     Cancelled
## 14:29  Penzance                                -     Cancelled
## 14:32  Basingstoke                             -     Cancelled
## 14:35  London Paddington                       -     Cancelled
## 14:37  Newbury                                 -     Cancelled
## 14:42  London Waterloo                         -     Cancelled
## 14:43  London Paddington                       -     Cancelled
## 14:48  London Paddington                       -     On time
## 14:49  Oxford                                  -     Cancelled
## 14:52  Ealing Broadway                         -     Cancelled
## 14:53  Cheltenham Spa                          -     Cancelled
## 14:55  Didcot Parkway                          -     On time
## 14:57  London Paddington                       -     Cancelled
## 14:57  Weston-super-Mare                       -     On time
## 15:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 15:02  Paignton                                -     Cancelled
## 15:04  London Paddington                       -     Cancelled
## 15:04  London Paddington                       -     Cancelled
## 15:05  Basingstoke                             -     Cancelled
## 15:12  Bedwyn                                  -     Cancelled
## 15:12  London Waterloo                         -     Cancelled
## 15:13  Bristol Parkway                         -     Delayed
## 15:13  London Paddington                       -     Delayed
## 15:15  Birmingham New Street                   -     Cancelled
##        via Coventry                            
## 15:18  London Paddington                       -     Cancelled
## 15:18  Redhill                                 -     Cancelled
## 15:18  Worcester Foregate Street               -     Cancelled
## 15:22  Ealing Broadway                         -     Cancelled
## 15:23  Didcot Parkway                          -     On time
## 15:24  London Paddington                       -     Cancelled
## 15:27  Bristol Temple Meads                    -     Cancelled
## 15:27  London Paddington                       -     Cancelled
## 15:29  Penzance                                -     Cancelled
## 15:32  Basingstoke                             -     Cancelled
## 15:34  London Paddington                       -     Cancelled
## 15:35  Bedwyn                                  -     Cancelled
## 15:42  London Waterloo                         -     Cancelled
## 15:43  Cardiff Central                         -     Cancelled
## 15:43  London Paddington                       -     Cancelled
## 15:45  London Paddington                       -     On time
## 15:48  Worcester Foregate Street               -     Cancelled
## 15:50  London Paddington                       -     Cancelled
## 15:50  London Paddington                       -     Cancelled
## 15:51  Didcot Parkway                          12    On time
## 15:52  Ealing Broadway                         -     Cancelled
## 15:53  Cheltenham Spa                          -     Cancelled
## 15:56  London Paddington                       -     Cancelled
## 15:58  Weston-super-Mare                       -     On time
## 16:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
