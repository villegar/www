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

## Example (Last rendered on 2021-12-11 08:03)

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
## Reading (RDG) Station Board on 2021-12-11 08:03:43
## Time   From                                    Plat  Expected
## 07:43  London Waterloo                         5     08:04
## 07:53  Swansea                                 11    08:26
## 08:02  Didcot Parkway                          15    On time
## 08:10  Weston-super-Mare                       10    Delayed
## 08:11  London Paddington                       9     08:17
## 08:13  London Paddington                       14    On time
## 08:14  London Waterloo                         4     On time
## 08:16  Newbury                                 11    On time
## 08:17  London Paddington                       9     On time
## 08:25  London Paddington                       9     On time
## 08:25  Oxford                                  11    On time
## 08:27  London Paddington                       7     On time
## 08:30  Cheltenham Spa                          10A   On time
## 08:33  London Paddington                       7     On time
## 08:33  Redhill                                 5     On time
## 08:39  Manchester Piccadilly                   8     On time
## 08:41  Bristol Temple Meads                    11    On time
## 08:42  Newbury                                 1     On time
## 08:43  London Paddington                       14    On time
## 08:44  London Paddington                       12    On time
## 08:44  London Waterloo                         6     On time
## 08:47  London Paddington                       9B    On time
## 08:51  Basingstoke                             2     On time
## 08:51  Gatwick Airport                         4     On time
## 08:52  London Paddington                       9B    On time
## 08:53  Hereford                                10    On time
## 08:55  London Paddington                       8     On time
## 08:56  Swansea                                 11    09:15
## 08:58  London Paddington                       -     Cancelled
## 09:02  Didcot Parkway                          15    On time
## 09:03  Plymouth                                11    On time
## 09:06  Bournemouth                             13    On time
## 09:10  Taunton                                 10    On time
## 09:11  London Paddington                       8     On time
## 09:13  London Paddington                       14    On time
## 09:14  London Waterloo                         4     On time
## 09:17  London Paddington                       9B    On time
## 09:23  Newbury                                 11    On time
## 09:25  London Paddington                       9     On time
## 09:25  Oxford                                  10A   On time
## 09:27  London Paddington                       7     On time
## 09:33  Cheltenham Spa                          11    On time
## 09:33  London Paddington                       7     On time
## 09:33  Redhill                                 5     On time
## 09:41  Bristol Temple Meads                    10    On time
## 09:41  Newbury                                 1     On time
## 09:43  London Paddington                       14    On time
## 09:43  Plymouth                                11    On time
## 09:44  London Paddington                       12    On time
## 09:44  London Waterloo                         6     On time
## 09:47  London Paddington                       9     On time
## 09:48  Basingstoke                             2     On time
## 09:51  Gatwick Airport                         4     On time
## 09:51  London Paddington                       8     On time
## 09:53  Swansea                                 10    10:10
## 09:55  London Paddington                       9     On time
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-11 08:03:47
## Time   To                                      Plat  Expected
## 07:54  London Paddington                       11    08:27
## 08:02  Newbury                                 1     On time
## 08:06  Redhill                                 6     Delayed
## 08:09  London Waterloo                         5     On time
## 08:12  London Paddington                       10    Delayed
## 08:13  Swansea                                 9     08:18
## 08:15  Ealing Broadway                         15    On time
## 08:20  London Paddington                       11    On time
## 08:20  Worcester Shrub Hill                    9     On time
## 08:22  Ealing Broadway                         14    On time
## 08:26  London Paddington                       11    On time
## 08:27  Bristol Temple Meads                    9     On time
## 08:30  Penzance                                7     On time
## 08:35  London Paddington                       10A   On time
## 08:35  Newbury                                 7     On time
## 08:38  Basingstoke                             2     On time
## 08:39  London Waterloo                         4     On time
## 08:43  London Paddington                       11    On time
## 08:49  Oxford                                  9B    On time
## 08:52  Bournemouth                             8     On time
## 08:52  Ealing Broadway                         14    On time
## 08:53  Didcot Parkway                          12    On time
## 08:54  Cheltenham Spa                          9B    On time
## 08:56  London Paddington                       11    09:15
## 08:57  Taunton                                 8     On time
## 08:58  London Paddington                       10    On time
## 09:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:02  Exeter St Davids                        -     Cancelled
## 09:05  London Paddington                       11    On time
## 09:06  Newbury                                 1     On time
## 09:09  London Waterloo                         6     On time
## 09:11  London Paddington                       10    On time
## 09:13  Swansea                                 8     On time
## 09:15  Ealing Broadway                         15    On time
## 09:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 09:20  Great Malvern                           9B    On time
## 09:20  Redhill                                 5     On time
## 09:22  Ealing Broadway                         14    On time
## 09:25  London Paddington                       11    On time
## 09:27  Bristol Temple Meads                    9     On time
## 09:27  London Paddington                       10A   On time
## 09:30  Plymouth                                7     On time
## 09:35  London Paddington                       11    On time
## 09:35  Newbury                                 7     On time
## 09:38  Basingstoke                             2     On time
## 09:39  London Waterloo                         4     On time
## 09:43  London Paddington                       10    On time
## 09:45  London Paddington                       11    On time
## 09:49  Oxford                                  9     On time
## 09:52  Ealing Broadway                         14    On time
## 09:53  Cheltenham Spa                          8     On time
## 09:53  Didcot Parkway                          12    On time
## 09:54  London Paddington                       10    10:11
## 09:58  Bristol Temple Meads                    9     On time
## 10:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
