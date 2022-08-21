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

## Example (Last rendered on 2022-08-21 10:04)

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
## Reading (RDG) Station Board on 2022-08-21 10:04:05
## Time   From                                    Plat  Expected
## 10:33  London Paddington                       14    11:43
## 10:57  Worcester Shrub Hill                    11    On time
## 10:59  London Paddington                       -     Cancelled
## 11:01  London Paddington                       8     11:23
## 11:05  Bournemouth                             7     11:21
## 11:08  London Paddington                       -     Cancelled
## 11:08  London Waterloo                         4     On time
## 11:08  Redhill                                 6     On time
## 11:10  Didcot Parkway                          15    On time
## 11:10  London Paddington                       9B    11:13
## 11:13  Bristol Temple Meads                    10    On time
## 11:16  London Paddington                       8     11:31
## 11:17  Swansea                                 11    On time
## 11:19  Bedwyn                                  1     11:22
## 11:25  Oxford                                  10A   11:27
## 11:26  London Paddington                       7     11:30
## 11:33  Basingstoke                             2     On time
## 11:34  London Waterloo                         4     On time
## 11:35  Plymouth                                11    11:42
## 11:38  Manchester Piccadilly                   7     On time
## 11:38  Redhill                                 5     On time
## 11:39  Ealing Broadway                         14    Delayed
## 11:43  London Paddington                       8     On time
## 11:44  Swansea                                 11    12:05
## 11:47  Salisbury                               1     11:49
## 11:53  London Paddington                       9     On time
## 11:56  Worcester Shrub Hill                    -     Cancelled
## 11:58  Plymouth                                11    12:00
## 12:01  London Paddington                       8     On time
## 12:07  London Waterloo                         4     On time
## 12:08  Redhill                                 -     Cancelled
## 12:08  West Drayton                            14    On time
## 12:10  London Paddington                       9     On time
## 12:13  Bristol Temple Meads                    10    On time
## 12:17  London Paddington                       8     On time
## 12:19  Newbury                                 1     On time
## 12:25  Oxford                                  10    On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10    On time
## 12:33  Basingstoke                             2     On time
## 12:34  London Waterloo                         4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:38  Manchester Piccadilly                   12    On time
## 12:39  London Paddington                       14    On time
## 12:43  London Paddington                       9     On time
## 12:44  Swansea                                 10    On time
## 12:47  Salisbury                               1     On time
## 12:53  London Paddington                       9     On time
## 12:55  Penzance                                11    12:59
## 12:56  Worcester Shrub Hill                    10    On time
## 12:59  London Paddington                       -     Cancelled
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-21 10:04:09
## Time   To                                      Plat  Expected
## 11:01  Ealing Broadway                         14    11:46
## 11:01  Paignton                                -     Cancelled
## 11:09  Swansea                                 8     11:24
## 11:12  Great Malvern                           9B    11:14
## 11:12  Salisbury                               1     On time
## 11:14  London Paddington                       15    On time
## 11:15  London Paddington                       10    On time
## 11:15  Manchester Piccadilly                   7     11:22
##        via Coventry & Stoke-on-Trent           
## 11:18  London Paddington                       11    On time
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:24  London Waterloo                         4     On time
## 11:27  London Paddington                       10A   11:27
## 11:28  Plymouth                                7     11:31
## 11:30  Didcot Parkway                          8     11:32
## 11:31  Ealing Broadway                         -     Cancelled
## 11:38  Basingstoke                             2     On time
## 11:40  London Paddington                       11    11:43
## 11:41  Redhill                                 6     On time
## 11:43  Bedwyn                                  1     On time
## 11:46  London Paddington                       11    12:06
## 11:50  Oxford                                  8     On time
## 11:52  Bournemouth                             7     On time
## 11:54  London Waterloo                         4     On time
## 11:55  Bristol Temple Meads                    9     On time
## 12:00  London Paddington                       11    12:00
## 12:01  Ealing Broadway                         14    On time
## 12:02  London Paddington                       -     Cancelled
## 12:09  Carmarthen                              8     On time
## 12:12  Hereford                                9     On time
## 12:12  Salisbury                               1     On time
## 12:14  London Paddington                       15    On time
## 12:15  London Paddington                       10    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:24  London Waterloo                         4     On time
## 12:27  London Paddington                       10    On time
## 12:28  Penzance                                7     On time
## 12:30  Didcot Parkway                          8     On time
## 12:31  Ealing Broadway                         14    On time
## 12:38  Basingstoke                             2     On time
## 12:40  London Paddington                       10    On time
## 12:41  Redhill                                 5     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:50  Oxford                                  9     On time
## 12:54  London Waterloo                         4     On time
## 12:55  Weston-super-Mare                       9     On time
## 13:00  London Paddington                       11    On time
## 13:01  Ealing Broadway                         14    On time
## 13:01  Paignton                                -     Cancelled
## 13:02  London Paddington                       10    On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
