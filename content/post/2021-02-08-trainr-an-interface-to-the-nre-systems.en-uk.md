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

## Example (Last rendered on 2022-10-23 20:05)

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
## Reading (RDG) Station Board on 2022-10-23 20:05:31
## Time   From                                    Plat  Expected
## 20:57  Great Malvern                           10A   21:18
## 21:01  London Paddington                       12    21:06
## 21:05  Ascot                                   4     On time
## 21:05  Eastleigh                               -     21:15
## 21:08  Redhill                                 15B   21:19
## 21:09  London Paddington                       14    21:11
## 21:11  Taunton                                 10A   21:17
## 21:12  London Paddington                       -     21:22
## 21:12  London Paddington                       12    On time
## 21:13  Didcot Parkway                          13    On time
## 21:19  Bedwyn                                  1     21:24
## 21:26  London Paddington                       -     On time
## 21:33  Basingstoke                             2     21:39
## 21:35  Ascot                                   6     On time
## 21:39  London Paddington                       14    On time
## 21:39  Manchester Piccadilly                   -     22:06
## 21:41  Gatwick Airport                         15    Delayed
## 21:48  Swansea                                 10    On time
## 21:53  London Paddington                       -     On time
## 21:55  Great Malvern                           10    21:57
## 22:05  Ascot                                   4     On time
## 22:05  Plymouth                                11    On time
## 22:06  London Paddington                       -     On time
## 22:08  London Paddington                       14    On time
## 22:09  Weston-super-Mare                       10    On time
## 22:11  London Paddington                       12    On time
## 22:12  London Paddington                       -     On time
## 22:13  Didcot Parkway                          13    On time
## 22:23  London Paddington                       -     On time
## 22:24  Newbury                                 1     On time
## 22:33  Basingstoke                             13    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:40  London Paddington                       9     On time
## 22:45  Gatwick Airport                         15B   Delayed
## 22:49  Carmarthen                              10    On time
## 22:50  Penzance                                11    On time
## 22:52  Great Malvern                           14    On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-23 20:05:34
## Time   To                                      Plat  Expected
## 21:01  Ealing Broadway                         14    21:03
## 21:02  London Paddington                       10A   21:19
## 21:09  Swansea                                 12    On time
## 21:12  Birmingham New Street                   -     21:16
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    On time
## 21:15  Worcester Shrub Hill                    -     21:23
## 21:17  London Paddington                       10A   21:18
## 21:24  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        -     On time
## 21:38  Basingstoke                             2     On time
## 21:43  Bedwyn                                  1     On time
## 21:50  London Paddington                       10    On time
## 21:51  Ascot                                   6     On time
## 21:52  Eastleigh                               -     22:07
## 21:54  Ealing Broadway                         14    On time
## 21:55  Bristol Temple Meads                    -     On time
## 21:57  London Paddington                       10    On time
## 22:09  Swansea                                 -     On time
## 22:10  London Paddington                       10    On time
## 22:12  Didcot Parkway                          12    On time
## 22:12  London Paddington                       11    On time
## 22:13  Worcester Shrub Hill                    -     On time
## 22:24  Bristol Temple Meads                    -     On time
## 22:28  Ealing Broadway                         14    On time
## 22:43  Newbury                                 1     On time
## 22:54  Ascot                                   4     On time
## 22:54  London Paddington                       10    On time
## 22:55  London Paddington                       14    On time
## 23:00  London Paddington                       11    On time
## 23:03  Ealing Broadway                         -     On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
