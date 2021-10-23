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

## Example (Last rendered on 2021-10-23 20:06)

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
## Reading (RDG) Station Board on 2021-10-23 20:06:16
## Time   From                                    Plat  Expected
## 19:47  London Paddington                       9     21:09
## 19:51  London Paddington                       8     21:22
## 19:55  London Paddington                       9     21:25
## 20:11  Bristol Temple Meads                    10    21:08
## 20:11  London Paddington                       8     Delayed
## 20:54  Great Malvern                           10A   21:16
## 20:55  London Paddington                       9     Delayed
## 21:01  Didcot Parkway                          15    21:06
## 21:05  Bournemouth                             13B   On time
## 21:10  Bristol Temple Meads                    10    21:12
## 21:11  London Paddington                       9     Delayed
## 21:13  London Paddington                       -     Cancelled
## 21:14  Ascot                                   6     On time
## 21:15  Penzance                                11    21:21
## 21:17  London Paddington                       -     Cancelled
## 21:24  Slough                                  -     On time
## 21:25  London Paddington                       9     Delayed
## 21:25  Oxford                                  10A   Delayed
## 21:26  Newbury                                 12    Delayed
## 21:27  Swansea                                 11    On time
## 21:34  Cheltenham Spa                          10A   On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Newbury                                 1     On time
## 21:43  London Paddington                       -     Cancelled
## 21:44  Ascot                                   5     On time
## 21:44  London Paddington                       12    Delayed
## 21:50  Basingstoke                             2     On time
## 21:52  Redhill                                 15B   On time
## 21:54  Worcester Foregate Street               11A   On time
## 21:57  Gatwick Airport                         15B   On time
## 22:09  Taunton                                 10    On time
## 22:13  London Paddington                       14    On time
## 22:14  Ascot                                   4     On time
## 22:17  London Paddington                       8     On time
## 22:22  Newbury                                 1     On time
## 22:24  Swansea                                 10    22:27
## 22:25  Gatwick Airport                         15B   On time
## 22:25  London Paddington                       9     On time
## 22:32  Oxford                                  -     Cancelled
## 22:37  Cheltenham Spa                          10    On time
## 22:41  Manchester Piccadilly                   8B    On time
## 22:43  London Paddington                       14    On time
## 22:44  Ascot                                   6     On time
## 22:50  Basingstoke                             2     On time
## 22:52  London Paddington                       10    On time
## 22:55  London Paddington                       9     On time
## 23:01  Didcot Parkway                          15    On time
## 23:04  Redhill                                 14B   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-23 20:06:19
## Time   To                                      Plat  Expected
## 19:42  Newbury                                 8     21:06
## 19:49  Oxford                                  9     21:14
## 19:53  Cheltenham Spa                          8     21:23
## 19:57  Bristol Temple Meads                    9     21:26
## 20:13  London Paddington                       10    21:09
## 20:13  Swansea                                 8     Delayed
## 20:52  Ealing Broadway                         14    Delayed
## 20:56  London Paddington                       10A   21:17
## 20:57  Exeter St Davids                        9     Delayed
##        via Bristol                             
## 21:09  Ascot                                   4     On time
## 21:10  Newbury                                 1     On time
## 21:12  London Paddington                       10    21:13
## 21:13  Swansea                                 9     Delayed
## 21:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 21:15  Ealing Broadway                         15    On time
## 21:16  London Paddington                       11    21:22
## 21:19  Oxford                                  -     Cancelled
## 21:22  Ealing Broadway                         14    On time
## 21:26  London Paddington                       10A   Delayed
## 21:27  Bristol Temple Meads                    9     Delayed
## 21:30  London Paddington                       11    On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:39  Ascot                                   6     On time
## 21:40  London Paddington                       10A   On time
## 21:52  Bournemouth                             7B    On time
## 21:52  Ealing Broadway                         14    On time
## 21:56  London Paddington                       11A   On time
## 21:57  Didcot Parkway                          12    Delayed
## 22:09  Ascot                                   5     On time
## 22:10  Newbury                                 1     On time
## 22:15  Ealing Broadway                         15    On time
## 22:15  London Paddington                       10    On time
## 22:19  Worcester Shrub Hill                    8     On time
## 22:22  Ealing Broadway                         14    On time
## 22:26  London Paddington                       10    22:28
## 22:27  Bristol Parkway                         9     On time
## 22:34  London Paddington                       -     Cancelled
## 22:35  Basingstoke                             2     On time
## 22:39  Ascot                                   4     On time
## 22:39  London Paddington                       10    On time
## 22:52  Ealing Broadway                         14    On time
## 22:52  Southampton Central                     8B    On time
## 22:57  Bristol Parkway                         9     On time
## 23:05  Basingstoke                             2     On time
## 23:05  Didcot Parkway                          12    On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
