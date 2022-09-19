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

## Example (Last rendered on 2022-09-19 20:03)

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
## Reading (RDG) Station Board on 2022-09-19 20:03:29
## Time   From                                    Plat  Expected
## 19:05  Didcot Parkway                          -     Delayed
## 19:29  London Paddington                       7     21:05
## 19:46  Swansea                                 -     20:42
## 19:56  London Paddington                       -     21:12
## 20:10  Weston-super-Mare                       10    21:03
## 20:41  London Waterloo                         4     Delayed
## 20:43  Birmingham New Street                   7     21:03
## 20:44  Swansea                                 10    21:12
## 20:53  Great Malvern                           11    Delayed
## 21:00  Penzance                                10    21:28
## 21:03  Didcot Parkway                          15    21:16
## 21:04  Basingstoke                             2     21:01
## 21:06  London Waterloo                         -     On time
## 21:07  Bournemouth                             14    On time
## 21:09  Bristol Temple Meads                    10    21:36
## 21:10  London Paddington                       -     Cancelled
## 21:12  London Waterloo                         6     Delayed
## 21:13  West Drayton                            13    On time
## 21:20  London Paddington                       -     Cancelled
## 21:21  Bedwyn                                  -     Cancelled
## 21:24  Oxford                                  -     Cancelled
## 21:29  Didcot Parkway                          -     On time
## 21:29  Redhill                                 5     On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:36  Newbury                                 -     On time
## 21:41  London Waterloo                         4     21:49
## 21:41  Manchester Piccadilly                   7     On time
## 21:42  London Paddington                       -     Cancelled
## 21:44  Swansea                                 -     Cancelled
## 21:45  Slough                                  -     On time
## 21:46  London Paddington                       -     Cancelled
## 21:53  Great Malvern                           10    21:59
## 21:56  Gatwick Airport                         15B   On time
## 21:57  Basingstoke                             3     On time
## 22:00  Plymouth                                11    On time
## 22:05  Didcot Parkway                          -     On time
## 22:07  London Paddington                       -     Cancelled
## 22:08  Exeter St Davids                        10    On time
## 22:11  London Paddington                       -     Cancelled
## 22:14  Newbury                                 -     On time
## 22:16  Slough                                  -     On time
## 22:20  Newbury                                 -     Cancelled
## 22:25  Oxford                                  -     Cancelled
## 22:32  Cheltenham Spa                          -     Cancelled
## 22:34  Shalford                                14A   On time
## 22:40  Basingstoke                             -     On time
## 22:41  London Waterloo                         6     23:02
## 22:41  Manchester Piccadilly                   7     On time
## 22:42  London Paddington                       -     Cancelled
## 22:43  Swansea                                 11    22:47
## 22:45  Didcot Parkway                          -     On time
## 22:45  Slough                                  -     On time
## 22:52  Salisbury                               3     On time
## 22:58  London Waterloo                         -     On time
## 22:59  Worcester Foregate Street               -     Cancelled
## 21:20  Heathrow Central Bus Stn                BUS   On time
## 22:30  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-19 20:03:32
## Time   To                                      Plat  Expected
## 19:12  Ealing Broadway                         -     Delayed
## 19:31  Plymouth                                7     21:06
## 19:58  Bristol Temple Meads                    -     21:13
## 20:54  Staines                                 -     Delayed
## 20:57  West Drayton                            8     Delayed
## 20:57  Weston-super-Mare                       -     Delayed
## 21:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 21:10  Newbury                                 -     On time
## 21:12  London Waterloo                         6     Delayed
## 21:13  Birmingham New Street                   14    On time
##        via Coventry                            
## 21:13  Swansea                                 -     On time
## 21:18  Great Malvern                           -     On time
## 21:22  Basingstoke                             -     On time
## 21:23  Didcot Parkway                          -     Cancelled
## 21:23  London Paddington                       -     Cancelled
## 21:26  London Paddington                       -     Cancelled
## 21:27  Bristol Temple Meads                    -     On time
## 21:27  Ealing Broadway                         -     Cancelled
## 21:29  Plymouth                                8     On time
## 21:34  Gatwick Airport                         -     On time
##        via Guildford                           
## 21:42  London Waterloo                         6     Delayed
## 21:43  London Paddington                       -     Cancelled
## 21:48  Oxford                                  -     Cancelled
## 21:49  Didcot Parkway                          -     On time
## 21:52  Bournemouth                             7     On time
## 21:53  Cheltenham Spa                          -     Cancelled
## 21:57  Ealing Broadway                         -     Cancelled
## 22:05  Basingstoke                             -     On time
## 22:10  London Paddington                       10    On time
## 22:10  Newbury                                 -     On time
## 22:12  London Waterloo                         4     On time
## 22:13  Swansea                                 -     On time
## 22:18  Didcot Parkway                          -     On time
## 22:18  Worcester Shrub Hill                    -     On time
## 22:20  London Paddington                       -     Cancelled
## 22:27  Ealing Broadway                         -     Cancelled
## 22:27  Plymouth                                -     On time
##        via Bristol                             
## 22:35  London Paddington                       -     Cancelled
## 22:39  Plymouth                                -     On time
## 22:45  Oxford                                  -     Cancelled
## 22:46  Didcot Parkway                          -     On time
## 22:49  Southampton Central                     7     On time
## 22:52  Basingstoke                             -     On time
## 22:54  London Waterloo                         -     On time
## 22:57  Ealing Broadway                         -     Cancelled
## 22:59  Bristol Temple Meads                    -     On time
## 23:01  Bedwyn                                  -     Cancelled
## 23:01  London Paddington                       -     Cancelled
## 23:02  London Waterloo                         6     23:05
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
