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

## Example (Last rendered on 2021-08-21 20:05)

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
## Reading (RDG) Station Board on 2021-08-21 20:06:01
## Time   From                                    Plat  Expected
## 21:01  Didcot Parkway                          15A   21:03
## 21:05  Bournemouth                             13    On time
## 21:10  Bristol Temple Meads                    -     Cancelled
## 21:11  London Paddington                       9     On time
## 21:11  London Waterloo                         6     21:16
## 21:13  London Paddington                       14    On time
## 21:15  Penzance                                -     Cancelled
## 21:17  London Paddington                       8B    On time
## 21:25  London Paddington                       9     On time
## 21:25  Oxford                                  10    On time
## 21:26  Newbury                                 11    On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:39  Manchester Piccadilly                   7     On time
## 21:40  Newbury                                 1     On time
## 21:41  London Waterloo                         5     On time
## 21:43  London Paddington                       14    On time
## 21:43  Penzance                                11    22:08
## 21:44  London Paddington                       12B   On time
## 21:50  Basingstoke                             2     On time
## 21:50  Swansea                                 10    21:55
## 21:52  Redhill                                 15B   On time
## 21:54  Worcester Foregate Street               11A   On time
## 21:57  Gatwick Airport                         15B   On time
## 22:10  Taunton                                 10    Delayed
## 22:11  London Waterloo                         4     On time
## 22:13  London Paddington                       14    On time
## 22:17  London Paddington                       8     On time
## 22:23  Newbury                                 12A   On time
## 22:25  Gatwick Airport                         15B   On time
## 22:25  London Paddington                       9B    On time
## 22:32  Oxford                                  14A   On time
## 22:36  Cheltenham Spa                          10    On time
## 22:41  London Waterloo                         6     On time
## 22:41  Manchester Piccadilly                   8     On time
## 22:43  London Paddington                       14    On time
## 22:51  Basingstoke                             12B   On time
## 22:52  London Paddington                       10    On time
## 22:55  London Paddington                       -     Cancelled
## 23:01  Didcot Parkway                          14    On time
## 23:04  Redhill                                 5     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-21 20:06:05
## Time   To                                      Plat  Expected
## 21:10  Newbury                                 1     On time
## 21:12  London Paddington                       -     Cancelled
## 21:12  London Waterloo                         4     On time
## 21:13  Swansea                                 9     On time
## 21:15  Birmingham New Street                   13    On time
##        via Coventry                            
## 21:15  Ealing Broadway                         15A   On time
## 21:16  London Paddington                       -     Cancelled
## 21:19  Oxford                                  8B    On time
## 21:22  Ealing Broadway                         14    On time
## 21:26  London Paddington                       10    On time
## 21:27  Bath Spa                                9     On time
## 21:32  London Paddington                       11    On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       -     Cancelled
## 21:42  London Waterloo                         6     On time
## 21:45  London Paddington                       11    22:09
## 21:51  London Paddington                       10    21:56
## 21:52  Bournemouth                             7     On time
## 21:52  Ealing Broadway                         14    On time
## 21:56  London Paddington                       11A   On time
## 21:57  Didcot Parkway                          12B   On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         5     On time
## 22:15  Ealing Broadway                         15A   On time
## 22:16  London Paddington                       10    Delayed
## 22:19  Worcester Shrub Hill                    8     On time
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         9B    On time
## 22:34  London Paddington                       14A   On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10    On time
## 22:42  London Waterloo                         4     On time
## 22:52  Ealing Broadway                         14    On time
## 22:52  Southampton Central                     8     On time
## 22:57  Bristol Parkway                         -     Cancelled
## 23:05  Didcot Parkway                          13B   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
