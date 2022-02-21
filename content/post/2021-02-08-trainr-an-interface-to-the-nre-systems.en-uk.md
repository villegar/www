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

## Example (Last rendered on 2022-02-21 12:05)

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
## Reading (RDG) Station Board on 2022-02-21 12:05:46
## Time   From                                    Plat  Expected
## 11:22  Exeter St Davids                        8     12:19
## 11:45  Swansea                                 11    12:27
## 11:55  London Paddington                       9     12:11
## 11:59  Didcot Parkway                          15    12:15
## 12:01  Plymouth                                11    Delayed
## 12:04  Exeter St Davids                        -     Cancelled
## 12:04  Exeter St Davids                        -     12:54
## 12:09  Bristol Temple Meads                    10A   12:31
## 12:11  London Paddington                       9     12:18
## 12:11  London Waterloo                         4     Delayed
## 12:13  London Paddington                       14    12:18
## 12:16  London Paddington                       -     Cancelled
## 12:18  Basingstoke                             2     On time
## 12:22  Bedwyn                                  -     Cancelled
## 12:24  Oxford                                  -     Cancelled
## 12:25  London Paddington                       -     Cancelled
## 12:27  London Paddington                       7     On time
## 12:29  Cheltenham Spa                          -     Cancelled
## 12:33  Didcot Parkway                          15    On time
## 12:33  London Paddington                       -     Cancelled
## 12:33  Redhill                                 5     On time
## 12:35  Bedwyn                                  -     12:47
## 12:40  Bristol Temple Meads                    -     Cancelled
## 12:41  London Paddington                       -     Cancelled
## 12:41  London Waterloo                         6     13:01
## 12:42  Manchester Piccadilly                   7     On time
## 12:42  Newbury                                 -     Cancelled
## 12:43  London Paddington                       14    On time
## 12:45  Swansea                                 10    13:04
## 12:46  London Paddington                       -     Cancelled
## 12:49  Basingstoke                             2     On time
## 12:51  Gatwick Airport                         -     Cancelled
## 12:51  London Paddington                       -     Cancelled
## 12:54  Great Malvern                           -     Cancelled
## 12:54  London Paddington                       9     On time
## 12:57  London Paddington                       -     Cancelled
## 12:58  Penzance                                -     Cancelled
## 13:01  Didcot Parkway                          15    On time
## 13:04  Exeter St Davids                        -     13:24
## 13:05  Bournemouth                             8     On time
## 13:09  Bristol Temple Meads                    10    On time
## 13:11  London Paddington                       9     On time
## 13:11  London Waterloo                         4     13:13
## 13:13  London Paddington                       14    On time
## 13:16  London Paddington                       -     Cancelled
## 13:18  Basingstoke                             2     On time
## 13:24  Newbury                                 -     Cancelled
## 13:24  Oxford                                  -     Cancelled
## 13:25  London Paddington                       -     Cancelled
## 13:27  London Paddington                       8     On time
## 13:30  Cheltenham Spa                          -     Cancelled
## 13:31  Didcot Parkway                          13    On time
## 13:33  London Paddington                       -     Cancelled
## 13:33  Redhill                                 5     On time
## 13:35  Bedwyn                                  -     On time
## 13:36  Newbury                                 -     Cancelled
## 13:39  Bristol Temple Meads                    -     Cancelled
## 13:41  Manchester Piccadilly                   8     On time
## 13:42  London Waterloo                         6     Delayed
## 13:42  Paignton                                -     Cancelled
## 13:43  London Paddington                       14    On time
## 13:45  Swansea                                 10    On time
## 13:46  London Paddington                       -     Cancelled
## 13:51  Gatwick Airport                         -     Cancelled
## 13:51  London Paddington                       -     Cancelled
## 13:54  Great Malvern                           -     Cancelled
## 13:55  Basingstoke                             2     On time
## 13:56  London Paddington                       9     On time
## 14:02  Penzance                                -     Cancelled
## 14:03  Didcot Parkway                          15    On time
## 14:04  Exeter St Davids                        -     On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-21 12:05:51
## Time   To                                      Plat  Expected
## 11:22  London Paddington                       8     12:19
## 11:48  London Paddington                       11    12:28
## 11:57  Bristol Temple Meads                    9     12:12
## 12:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 12:04  London Paddington                       -     Cancelled
## 12:04  London Paddington                       11    Delayed
## 12:04  London Paddington                       -     12:54
## 12:07  Basingstoke                             2     On time
## 12:12  Bedwyn                                  3     On time
## 12:12  London Paddington                       10A   12:32
## 12:12  London Waterloo                         6     On time
## 12:12  Newbury                                 -     Cancelled
## 12:13  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 12:13  Swansea                                 9     12:19
## 12:18  Hereford                                -     Cancelled
## 12:20  Redhill                                 5     On time
## 12:22  Ealing Broadway                         14    On time
## 12:23  Didcot Parkway                          12    On time
## 12:24  London Paddington                       -     Cancelled
## 12:26  London Paddington                       -     Cancelled
## 12:27  Bristol Temple Meads                    -     Cancelled
## 12:29  Exeter St Davids                        7     On time
## 12:32  Basingstoke                             2     On time
## 12:34  London Paddington                       -     Cancelled
## 12:37  Bedwyn                                  -     Cancelled
## 12:42  London Paddington                       -     Cancelled
## 12:42  London Waterloo                         4     On time
## 12:43  Cardiff Central                         -     Cancelled
## 12:47  London Paddington                       10    13:05
## 12:49  Oxford                                  -     Cancelled
## 12:52  Bournemouth                             7     On time
## 12:52  Ealing Broadway                         14    On time
## 12:53  Cheltenham Spa                          -     Cancelled
## 12:53  Didcot Parkway                          12    On time
## 12:57  Bristol Temple Meads                    9     On time
## 12:57  London Paddington                       -     Cancelled
## 13:01  Exeter St Davids                        -     Cancelled
## 13:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 13:04  London Paddington                       -     Cancelled
## 13:04  London Paddington                       -     13:24
## 13:07  Basingstoke                             2     On time
## 13:12  Bedwyn                                  -     On time
## 13:12  London Waterloo                         6     On time
## 13:12  Newbury                                 -     Cancelled
## 13:13  Swansea                                 9     On time
## 13:14  London Paddington                       10    On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Stoke-on-Trent                      
## 13:18  Worcester Foregate Street               -     Cancelled
## 13:20  Ealing Broadway                         14    On time
## 13:20  Redhill                                 5     On time
## 13:23  Didcot Parkway                          12    On time
## 13:26  London Paddington                       -     Cancelled
## 13:27  Bristol Temple Meads                    -     Cancelled
## 13:29  Exeter St Davids                        8     On time
## 13:31  London Paddington                       -     Cancelled
## 13:32  Basingstoke                             2     On time
## 13:34  London Paddington                       -     Cancelled
## 13:37  Newbury                                 -     Cancelled
## 13:41  London Paddington                       -     Cancelled
## 13:42  London Paddington                       -     Cancelled
## 13:42  London Waterloo                         4     On time
## 13:48  London Paddington                       10    On time
## 13:48  Oxford                                  -     Cancelled
## 13:52  Ealing Broadway                         14    On time
## 13:53  Cheltenham Spa                          -     Cancelled
## 13:55  Didcot Parkway                          13    On time
## 13:57  London Paddington                       -     Cancelled
## 13:58  Bristol Temple Meads                    9     On time
## 14:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 14:04  London Paddington                       -     On time
## 14:04  London Paddington                       -     Cancelled
## 13:00  Heathrow Central Bus Stn                BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
```
