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

## Example (Last rendered on 2022-09-19 18:05)

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
## Reading (RDG) Station Board on 2022-09-19 18:05:11
## Time   From                                    Plat  Expected
## 18:41  West Drayton                            -     Delayed
## 18:47  Swansea                                 15    18:59
## 18:57  Great Malvern                           10    19:05
## 18:57  Penzance                                11    19:06
## 19:04  Basingstoke                             2     On time
## 19:05  Didcot Parkway                          -     Cancelled
## 19:05  Redhill                                 4     On time
## 19:10  West Drayton                            13    19:14
## 19:10  Weston-super-Mare                       10    Delayed
## 19:14  London Waterloo                         5     On time
## 19:15  London Paddington                       -     Cancelled
## 19:15  Newbury                                 1     19:19
## 19:16  Cardiff Central                         -     Cancelled
## 19:19  Newbury                                 -     Cancelled
## 19:25  Worcester Foregate Street               10    On time
## 19:26  London Waterloo                         -     On time
## 19:28  Didcot Parkway                          -     On time
## 19:29  London Paddington                       -     On time
## 19:31  Cheltenham Spa                          -     Cancelled
## 19:33  Redhill                                 4     On time
## 19:34  Basingstoke                             2     On time
## 19:34  London Paddington                       -     Cancelled
## 19:35  London Paddington                       -     Cancelled
## 19:39  Bristol Temple Meads                    -     Cancelled
## 19:41  Manchester Piccadilly                   7     On time
## 19:41  West Drayton                            13    On time
## 19:43  London Waterloo                         6     On time
## 19:45  London Paddington                       -     Cancelled
## 19:46  Swansea                                 10    19:54
## 19:53  London Paddington                       -     Cancelled
## 19:54  Plymouth                                11    On time
## 19:54  Worcester Foregate Street               -     Cancelled
## 19:55  Slough                                  -     On time
## 19:56  London Paddington                       -     On time
## 19:58  Didcot Parkway                          -     On time
## 19:58  London Waterloo                         -     On time
## 20:03  Newbury                                 -     On time
## 20:04  Gatwick Airport                         4     On time
## 20:07  Bournemouth                             8     On time
## 20:10  Weston-super-Mare                       10    On time
## 20:11  London Paddington                       -     On time
## 20:13  London Waterloo                         6     On time
## 20:14  London Paddington                       -     Cancelled
## 20:17  Slough                                  -     On time
## 20:24  London Paddington                       -     On time
## 20:26  London Paddington                       -     On time
## 20:28  Banbury                                 -     Cancelled
## 20:28  London Waterloo                         -     On time
## 20:32  Cheltenham Spa                          -     Cancelled
## 20:34  Basingstoke                             -     On time
## 20:34  Didcot Parkway                          -     On time
## 20:35  Redhill                                 14A   On time
## 20:36  London Paddington                       -     Cancelled
## 20:41  London Waterloo                         4     On time
## 20:43  Birmingham New Street                   7     On time
## 20:43  London Paddington                       -     Cancelled
## 20:44  Newbury                                 -     On time
## 20:44  Swansea                                 10    On time
## 20:46  Slough                                  -     On time
## 20:47  London Paddington                       -     Cancelled
## 20:51  London Paddington                       -     Cancelled
## 20:53  Gatwick Airport                         -     On time
## 20:53  Great Malvern                           11    On time
## 21:00  Penzance                                10    On time
## 21:04  Basingstoke                             -     On time
## 19:34  Heathrow Central Bus Stn                BUS   On time
## 20:05  Heathrow Central Bus Stn                BUS   On time
## 20:38  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-19 18:05:15
## Time   To                                      Plat  Expected
## 18:28  Bristol Temple Meads                    14    Delayed
## 18:43  Swansea                                 -     Delayed
## 18:59  Weston-super-Mare                       -     Delayed
## 19:01  Plymouth                                -     Delayed
## 19:10  Newbury                                 -     On time
## 19:12  Ealing Broadway                         -     Cancelled
## 19:12  London Waterloo                         6     On time
## 19:13  Swansea                                 -     On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       -     Cancelled
## 19:20  Redhill                                 -     On time
## 19:24  London Paddington                       -     Cancelled
## 19:24  London Waterloo                         -     On time
## 19:25  Basingstoke                             -     On time
## 19:27  Bristol Temple Meads                    -     On time
## 19:27  Ealing Broadway                         -     Cancelled
## 19:31  Plymouth                                -     On time
## 19:34  Didcot Parkway                          -     Cancelled
## 19:34  London Paddington                       -     Cancelled
## 19:36  Bedwyn                                  -     Cancelled
## 19:37  Ealing Broadway                         -     On time
## 19:41  London Paddington                       -     Cancelled
## 19:42  London Waterloo                         5     On time
## 19:42  Newbury                                 -     On time
## 19:43  Swansea                                 -     On time
## 19:50  Bournemouth                             7     On time
## 19:54  London Waterloo                         -     On time
## 19:55  Oxford                                  -     Cancelled
## 19:57  Basingstoke                             -     On time
## 19:57  Didcot Parkway                          -     On time
## 19:57  Ealing Broadway                         -     Cancelled
## 19:58  London Paddington                       -     Cancelled
## 19:58  Weston-super-Mare                       -     On time
## 20:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:09  London Waterloo                         6     On time
## 20:10  Newbury                                 -     On time
## 20:13  Ealing Broadway                         -     On time
## 20:13  Swansea                                 -     On time
## 20:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Hereford                                -     On time
## 20:20  Shalford                                -     On time
## 20:23  Didcot Parkway                          -     On time
## 20:24  London Waterloo                         -     On time
## 20:27  Bristol Temple Meads                    -     On time
## 20:27  Ealing Broadway                         -     Cancelled
## 20:29  Penzance                                -     On time
## 20:31  London Paddington                       -     Cancelled
## 20:36  London Paddington                       -     Cancelled
## 20:36  Newbury                                 -     Cancelled
## 20:42  London Waterloo                         6     On time
## 20:45  Ealing Broadway                         -     On time
## 20:47  London Paddington                       10    On time
## 20:49  Oxford                                  -     Cancelled
## 20:51  Didcot Parkway                          -     On time
## 20:52  Basingstoke                             -     On time
## 20:53  Cheltenham Spa                          -     Cancelled
## 20:56  London Paddington                       11    On time
## 20:57  Ealing Broadway                         -     Cancelled
## 20:57  Weston-super-Mare                       -     On time
## 21:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 21:03  London Paddington                       10    On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
