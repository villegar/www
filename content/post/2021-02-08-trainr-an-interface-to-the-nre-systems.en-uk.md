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

## Example (Last rendered on 2023-02-18 16:03)

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
## Reading (RDG) Station Board on 2023-02-18 16:03:21
## Time   From                                    Plat  Expected
## 15:39  Manchester Piccadilly                   13    16:05
## 16:00  Didcot Parkway                          15A   On time
## 16:03  Abbey Wood                              -     Cancelled
## 16:10  Bristol Temple Meads                    10A   16:12
## 16:11  London Paddington                       9     On time
## 16:11  London Paddington                       12B   On time
## 16:11  London Waterloo                         5     On time
## 16:17  London Paddington                       -     Cancelled
## 16:19  Cardiff Central                         10A   On time
## 16:20  Basingstoke                             2     On time
## 16:25  London Paddington                       9     On time
## 16:25  Oxford                                  11    On time
## 16:28  Plymouth                                10    On time
## 16:31  Didcot Parkway                          15A   On time
## 16:31  Theale                                  11A   On time
## 16:33  Abbey Wood                              14    16:58
## 16:33  London Paddington                       7B    On time
## 16:33  Redhill                                 4     On time
## 16:40  Weston-super-Mare                       10    On time
## 16:41  London Paddington                       9     On time
## 16:41  Manchester Piccadilly                   7B    On time
## 16:43  London Paddington                       12B   On time
## 16:43  London Waterloo                         6     On time
## 16:46  Swansea                                 10    On time
## 16:47  London Paddington                       9B    On time
## 16:50  Basingstoke                             2     On time
## 16:51  Gatwick Airport                         5     On time
## 16:51  London Paddington                       8B    On time
## 16:54  Great Malvern                           -     Cancelled
## 16:54  London Paddington                       9     On time
## 17:01  Didcot Parkway                          15A   On time
## 17:03  Abbey Wood                              14    17:12
## 17:06  Eastleigh                               13B   On time
## 17:10  Bristol Temple Meads                    10    On time
## 17:10  London Paddington                       12B   On time
## 17:11  London Paddington                       8     On time
## 17:11  London Waterloo                         4     On time
## 17:15  Penzance                                11    On time
## 17:17  London Paddington                       -     Cancelled
## 17:20  Basingstoke                             2     On time
## 17:25  London Paddington                       9     On time
## 17:25  Oxford                                  10A   On time
## 17:31  Didcot Parkway                          15A   On time
## 17:31  Theale                                  11A   On time
## 17:33  Abbey Wood                              14    On time
## 17:33  Cheltenham Spa                          10A   On time
## 17:33  London Paddington                       7B    On time
## 17:33  Redhill                                 5     On time
## 17:40  Weston-super-Mare                       11A   On time
## 17:41  London Paddington                       9B    On time
## 17:41  Manchester Piccadilly                   7     On time
## 17:43  London Paddington                       12B   On time
## 17:43  London Waterloo                         6     On time
## 17:47  London Paddington                       8     On time
## 17:47  Swansea                                 10    On time
## 17:50  Basingstoke                             2     On time
## 17:51  Gatwick Airport                         4     On time
## 17:51  London Paddington                       9B    On time
## 17:54  Hereford                                -     Cancelled
## 17:55  London Paddington                       8     On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-18 16:03:28
## Time   To                                      Plat  Expected
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:09  Plymouth                                8     On time
## 16:12  London Paddington                       10A   16:13
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15A   On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     Cancelled
## 16:20  London Paddington                       10A   On time
## 16:20  Redhill                                 4     On time
## 16:23  Didcot Parkway                          12B   On time
## 16:24  Abbey Wood                              -     Cancelled
## 16:26  London Paddington                       11    On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:32  London Paddington                       10    On time
## 16:35  London Paddington                       11A   On time
## 16:35  Theale                                  7B    On time
## 16:38  Basingstoke                             2     On time
## 16:39  London Waterloo                         5     On time
## 16:42  London Paddington                       10    On time
## 16:43  Cardiff Central                         9     On time
## 16:45  Ealing Broadway                         15A   On time
## 16:48  London Paddington                       10    On time
## 16:49  Oxford                                  9B    On time
## 16:52  Eastleigh                               7B    On time
## 16:53  Didcot Parkway                          12B   On time
## 16:54  Abbey Wood                              14    17:01
## 16:54  Cheltenham Spa                          8B    On time
## 16:56  London Paddington                       -     Cancelled
## 16:58  Taunton                                 9     On time
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:07  Basingstoke                             2     On time
## 17:09  London Waterloo                         6     On time
## 17:09  Penzance                                9     On time
## 17:13  Swansea                                 8     On time
## 17:14  London Paddington                       10    On time
## 17:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 17:16  London Paddington                       11    On time
## 17:19  Hereford                                -     Cancelled
## 17:20  Ealing Broadway                         15A   On time
## 17:20  Redhill                                 5     On time
## 17:23  Didcot Parkway                          12B   On time
## 17:24  Abbey Wood                              14    On time
## 17:27  Bristol Temple Meads                    9     On time
## 17:27  London Paddington                       10A   On time
## 17:32  London Paddington                       11A   On time
## 17:35  London Paddington                       10A   On time
## 17:35  Theale                                  7B    On time
## 17:38  Basingstoke                             2     On time
## 17:39  London Waterloo                         4     On time
## 17:42  London Paddington                       11A   On time
## 17:43  Carmarthen                              9B    On time
## 17:45  Ealing Broadway                         15A   On time
## 17:48  London Paddington                       10    On time
## 17:50  Oxford                                  8     On time
## 17:54  Abbey Wood                              14    On time
## 17:54  Cheltenham Spa                          9B    On time
## 17:55  Didcot Parkway                          12B   On time
## 17:56  London Paddington                       -     Cancelled
## 18:00  Weston-super-Mare                       8     On time
## 18:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
