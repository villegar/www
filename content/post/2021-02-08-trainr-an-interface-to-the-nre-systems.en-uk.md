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

## Example (Last rendered on 2022-10-23 16:06)

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
## Reading (RDG) Station Board on 2022-10-23 16:06:13
## Time   From                                    Plat  Expected
## 16:56  Great Malvern                           10    17:04
## 16:58  Penzance                                11    17:03
## 17:05  Ascot                                   4     On time
## 17:05  Eastleigh                               3     17:09
## 17:08  Redhill                                 6     On time
## 17:09  London Paddington                       14    17:14
## 17:10  Weston-super-Mare                       10    17:17
## 17:13  Didcot Parkway                          15    17:17
## 17:13  London Paddington                       12    On time
## 17:20  Bedwyn                                  3     On time
## 17:26  London Paddington                       7     On time
## 17:33  Basingstoke                             2     17:35
## 17:35  Ascot                                   4     On time
## 17:38  Gatwick Airport                         5     17:40
## 17:39  London Paddington                       14    17:41
## 17:39  Manchester Piccadilly                   -     17:44
## 17:39  Paignton                                12    17:47
## 17:40  Bristol Temple Meads                    10    17:45
## 17:44  Carmarthen                              11    On time
## 17:57  Plymouth                                11    On time
## 17:57  Worcester Foregate Street               10    On time
## 18:05  Ascot                                   4     On time
## 18:06  Plymouth                                10    On time
## 18:08  London Paddington                       14    On time
## 18:08  Redhill                                 6     On time
## 18:12  London Paddington                       9     On time
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       12    On time
## 18:21  Newbury                                 1     On time
## 18:33  Basingstoke                             2     On time
## 18:33  Cheltenham Spa                          11    On time
## 18:35  Ascot                                   4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  London Paddington                       14    On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:40  Bristol Temple Meads                    9     On time
## 18:44  Swansea                                 10    On time
## 18:56  Great Malvern                           10    On time
## 18:58  Penzance                                11    On time
## 19:05  Ascot                                   4     On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-23 16:06:17
## Time   To                                      Plat  Expected
## 17:00  London Paddington                       11    17:05
## 17:02  London Paddington                       10    17:06
## 17:02  Plymouth                                -     Delayed
## 17:10  Swansea                                 -     17:12
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15    17:18
## 17:14  Great Malvern                           -     On time
## 17:15  London Paddington                       10    17:18
## 17:15  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:21  Ascot                                   4     On time
## 17:25  Bristol Temple Meads                    -     On time
## 17:25  Didcot Parkway                          12    On time
## 17:28  Penzance                                7     On time
## 17:31  Ealing Broadway                         14    On time
## 17:38  Basingstoke                             2     On time
## 17:41  Redhill                                 6     On time
## 17:42  London Paddington                       12    17:48
## 17:43  Bedwyn                                  3     On time
## 17:45  London Paddington                       10    17:45
## 17:48  London Paddington                       11    On time
## 17:48  Oxford                                  -     On time
## 17:51  Ascot                                   4     On time
## 17:52  Eastleigh                               -     On time
## 17:55  Weston-super-Mare                       -     On time
## 18:00  Cheltenham Spa                          -     On time
## 18:00  London Paddington                       11    On time
## 18:01  Ealing Broadway                         14    On time
## 18:02  London Paddington                       10    On time
## 18:10  Swansea                                 -     On time
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9     On time
## 18:15  London Paddington                       10    On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:21  Ascot                                   4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:28  Penzance                                7     On time
## 18:31  Ealing Broadway                         14    On time
## 18:38  Basingstoke                             2     On time
## 18:41  Redhill                                 6     On time
## 18:42  London Paddington                       11    On time
## 18:43  Newbury                                 1     On time
## 18:45  London Paddington                       9     On time
## 18:48  London Paddington                       10    On time
## 18:48  Oxford                                  8     On time
## 18:51  Ascot                                   4     On time
## 18:55  Weston-super-Mare                       9     On time
## 19:00  London Paddington                       11    On time
## 19:01  Ealing Broadway                         14    On time
## 19:01  Plymouth                                8     On time
## 19:02  London Paddington                       10    On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
