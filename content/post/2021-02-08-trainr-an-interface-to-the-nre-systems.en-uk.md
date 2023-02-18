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

## Example (Last rendered on 2023-02-18 14:03)

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
## Reading (RDG) Station Board on 2023-02-18 14:03:11
## Time   From                                    Plat  Expected
## 13:55  London Paddington                       9     14:02
## 14:02  Didcot Parkway                          15A   On time
## 14:05  Abbey Wood                              14    On time
## 14:10  Bristol Temple Meads                    10    14:13
## 14:11  London Paddington                       9     On time
## 14:11  London Paddington                       12B   On time
## 14:11  London Waterloo                         5     On time
## 14:17  London Paddington                       -     Cancelled
## 14:20  Basingstoke                             2     On time
## 14:25  London Paddington                       9     On time
## 14:25  Oxford                                  11A   On time
## 14:28  Penzance                                10    On time
## 14:30  Theale                                  11A   On time
## 14:31  Didcot Parkway                          15    On time
## 14:33  Abbey Wood                              14    On time
## 14:33  London Paddington                       7B    On time
## 14:33  Redhill                                 4     On time
## 14:35  Cheltenham Spa                          10A   On time
## 14:39  Manchester Piccadilly                   7     On time
## 14:40  Weston-super-Mare                       11    On time
## 14:43  London Paddington                       12B   On time
## 14:43  London Waterloo                         6     On time
## 14:46  Swansea                                 10    On time
## 14:47  London Paddington                       9     On time
## 14:50  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         5     On time
## 14:51  London Paddington                       8     On time
## 14:53  Worcester Foregate Street               -     Cancelled
## 14:55  London Paddington                       9B    On time
## 15:01  Didcot Parkway                          15A   On time
## 15:03  Abbey Wood                              14    On time
## 15:06  Eastleigh                               7B    On time
## 15:10  Bristol Temple Meads                    10    On time
## 15:11  London Paddington                       8     On time
## 15:11  London Paddington                       12B   On time
## 15:11  London Waterloo                         4     On time
## 15:15  Penzance                                11    On time
## 15:17  London Paddington                       -     Cancelled
## 15:20  Basingstoke                             2     On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10A   On time
## 15:31  Didcot Parkway                          15A   On time
## 15:31  Theale                                  11    On time
## 15:33  Abbey Wood                              14    On time
## 15:33  Cheltenham Spa                          10A   On time
## 15:33  London Paddington                       7B    On time
## 15:33  Redhill                                 5     On time
## 15:38  London Paddington                       9B    On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Weston-super-Mare                       11    On time
## 15:43  London Paddington                       12B   On time
## 15:43  London Waterloo                         6     On time
## 15:47  London Paddington                       9     On time
## 15:47  Swansea                                 10    On time
## 15:51  Basingstoke                             2     On time
## 15:51  Gatwick Airport                         4     On time
## 15:53  Hereford                                -     Cancelled
## 15:55  London Paddington                       9     On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-18 14:03:17
## Time   To                                      Plat  Expected
## 13:57  Weston-super-Mare                       9     14:03
## 14:07  Basingstoke                             2     On time
## 14:09  London Waterloo                         6     On time
## 14:09  Penzance                                8     On time
## 14:12  London Paddington                       10    14:14
## 14:13  Swansea                                 9     On time
## 14:15  Ealing Broadway                         15A   On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Great Malvern                           -     Cancelled
## 14:20  Redhill                                 4     On time
## 14:24  Abbey Wood                              14    On time
## 14:24  Didcot Parkway                          12B   On time
## 14:27  Bristol Temple Meads                    9     On time
## 14:27  London Paddington                       11A   On time
## 14:32  London Paddington                       10    On time
## 14:35  London Paddington                       11A   On time
## 14:35  Theale                                  7B    On time
## 14:38  Basingstoke                             2     On time
## 14:38  London Paddington                       10A   On time
## 14:39  London Waterloo                         5     On time
## 14:42  London Paddington                       11    On time
## 14:45  Ealing Broadway                         15    On time
## 14:48  London Paddington                       10    On time
## 14:49  Oxford                                  9     On time
## 14:52  Eastleigh                               7     On time
## 14:53  Cheltenham Spa                          8     On time
## 14:53  Didcot Parkway                          12B   On time
## 14:54  Abbey Wood                              14    On time
## 14:56  London Paddington                       -     Cancelled
## 14:57  Weston-super-Mare                       9B    On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:07  Basingstoke                             2     On time
## 15:09  London Waterloo                         6     On time
## 15:09  Penzance                                9     On time
## 15:12  London Paddington                       10    On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15A   On time
## 15:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 15:16  London Paddington                       11    On time
## 15:19  Great Malvern                           -     Cancelled
## 15:20  Redhill                                 5     On time
## 15:24  Abbey Wood                              14    On time
## 15:24  Didcot Parkway                          12B   On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       10A   On time
## 15:32  London Paddington                       11    On time
## 15:35  London Paddington                       10A   On time
## 15:35  Theale                                  7B    On time
## 15:38  Basingstoke                             2     On time
## 15:39  London Waterloo                         4     On time
## 15:40  Bristol Parkway                         9B    On time
## 15:43  London Paddington                       11    On time
## 15:45  Ealing Broadway                         15A   On time
## 15:49  Oxford                                  9     On time
## 15:50  London Paddington                       10    On time
## 15:53  Didcot Parkway                          12B   On time
## 15:54  Abbey Wood                              14    On time
## 15:57  Weston-super-Mare                       9     On time
## 15:58  London Paddington                       -     Cancelled
## 16:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
