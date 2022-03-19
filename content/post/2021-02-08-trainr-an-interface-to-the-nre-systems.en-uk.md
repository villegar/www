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

## Example (Last rendered on 2022-03-19 16:04)

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
## Reading (RDG) Station Board on 2022-03-19 16:04:06
## Time   From                                    Plat  Expected
## 15:53  Hereford                                10A   16:03
## 16:00  Didcot Parkway                          15    16:04
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12    On time
## 16:17  London Paddington                       9B    On time
## 16:20  Basingstoke                             2     On time
## 16:23  Ascot                                   5     On time
## 16:25  London Paddington                       9     On time
## 16:26  Theale                                  11A   On time
## 16:27  Oxford                                  10A   On time
## 16:31  Didcot Parkway                          15A   On time
## 16:33  London Paddington                       7B    On time
## 16:33  Redhill                                 4     On time
## 16:39  Manchester Piccadilly                   7B    On time
## 16:39  Plymouth                                11    On time
## 16:43  London Paddington                       14    On time
## 16:44  London Paddington                       12    On time
## 16:47  Ascot                                   6     On time
## 16:47  London Paddington                       9B    On time
## 16:47  Weston-super-Mare                       10    On time
## 16:50  Basingstoke                             2     On time
## 16:50  Swansea                                 11    On time
## 16:51  Gatwick Airport                         5     On time
## 16:51  London Paddington                       -     Cancelled
## 16:54  Great Malvern                           10A   On time
## 16:55  London Paddington                       9     On time
## 17:01  Didcot Parkway                          15A   On time
## 17:05  Bournemouth                             13B   On time
## 17:11  London Paddington                       9     On time
## 17:13  London Paddington                       14    On time
## 17:14  London Paddington                       12    On time
## 17:17  London Paddington                       9B    On time
## 17:18  Penzance                                10    On time
## 17:20  Basingstoke                             2     On time
## 17:23  Ascot                                   4     On time
## 17:25  Oxford                                  10A   On time
## 17:26  Theale                                  11A   On time
## 17:31  Didcot Parkway                          15    On time
## 17:33  Cheltenham Spa                          -     Cancelled
## 17:33  London Paddington                       7B    On time
## 17:33  Redhill                                 5     On time
## 17:40  Weston-super-Mare                       10    On time
## 17:41  London Paddington                       9B    On time
## 17:43  London Paddington                       14    On time
## 17:44  London Paddington                       12    On time
## 17:47  Ascot                                   6     On time
## 17:47  London Paddington                       9B    On time
## 17:47  Swansea                                 10    On time
## 17:51  Gatwick Airport                         4     On time
## 17:51  London Paddington                       8B    On time
## 17:54  Basingstoke                             2     On time
## 17:54  Worcester Shrub Hill                    10    17:58
## 17:55  London Paddington                       -     Cancelled
## 16:45  Heathrow Central Bus Stn                BUS   On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-19 16:04:11
## Time   To                                      Plat  Expected
## 15:58  London Paddington                       10A   16:04
## 16:07  Basingstoke                             2     On time
## 16:12  Ascot                                   6     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15    On time
## 16:19  Great Malvern                           9B    On time
## 16:20  Redhill                                 4     On time
## 16:22  Ealing Broadway                         14    On time
## 16:23  Didcot Parkway                          12    On time
## 16:23  Plymouth                                8     On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:27  London Paddington                       11A   On time
## 16:29  London Paddington                       10A   On time
## 16:35  Theale                                  7B    On time
## 16:38  Basingstoke                             2     On time
## 16:41  London Paddington                       11    On time
## 16:42  Ascot                                   5     On time
## 16:45  Ealing Broadway                         15A   On time
## 16:49  London Paddington                       10    On time
## 16:49  Oxford                                  9B    On time
## 16:52  Bournemouth                             7B    On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  Cheltenham Spa                          -     Cancelled
## 16:53  Didcot Parkway                          12    On time
## 16:54  London Paddington                       11    On time
## 16:56  London Paddington                       10A   On time
## 16:57  Taunton                                 9     On time
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:07  Basingstoke                             2     On time
## 17:10  Penzance                                8     On time
## 17:12  Ascot                                   6     On time
## 17:14  Swansea                                 9     On time
## 17:15  Ealing Broadway                         15A   On time
## 17:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                9B    On time
## 17:20  London Paddington                       10    On time
## 17:20  Redhill                                 5     On time
## 17:22  Ealing Broadway                         14    On time
## 17:23  Didcot Parkway                          12    On time
## 17:27  London Paddington                       11A   On time
## 17:29  London Paddington                       10A   On time
## 17:35  London Paddington                       -     Cancelled
## 17:35  Theale                                  7B    On time
## 17:38  Basingstoke                             2     On time
## 17:42  Ascot                                   4     On time
## 17:42  London Paddington                       10    On time
## 17:43  Carmarthen                              9B    On time
## 17:45  Ealing Broadway                         15    On time
## 17:48  London Paddington                       10    On time
## 17:49  Oxford                                  9B    On time
## 17:52  Ealing Broadway                         14    On time
## 17:53  Cheltenham Spa                          8B    On time
## 17:55  Didcot Parkway                          12    On time
## 17:56  London Paddington                       10    17:59
## 17:57  Weston-super-Mare                       -     Cancelled
## 18:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
