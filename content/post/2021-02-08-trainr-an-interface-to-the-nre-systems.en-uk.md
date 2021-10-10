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

## Example (Last rendered on 2021-10-10 10:04)

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
## Reading (RDG) Station Board on 2021-10-10 10:04:03
## Time   From                                    Plat  Expected
## 10:54  Southampton Central                     7     On time
## 11:05  London Waterloo                         4     11:08
## 11:07  London Paddington                       9     On time
## 11:10  Didcot Parkway                          15    On time
## 11:11  Redhill                                 6     On time
## 11:12  London Paddington                       9     On time
## 11:13  London Paddington                       14    On time
## 11:15  Bristol Parkway                         10    On time
## 11:15  London Paddington                       12    On time
## 11:19  Bedwyn                                  1     11:22
## 11:26  London Paddington                       7     On time
## 11:35  London Waterloo                         4     On time
## 11:38  Gatwick Airport                         5     On time
## 11:39  Manchester Piccadilly                   13    On time
## 11:43  London Paddington                       14    On time
## 11:53  London Paddington                       -     Cancelled
## 11:56  Great Malvern                           10A   On time
## 11:57  Plymouth                                11    On time
## 11:58  London Paddington                       -     On time
## 12:05  London Waterloo                         4     On time
## 12:07  London Paddington                       9     On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Didcot Parkway                          15    On time
## 12:11  Redhill                                 6     On time
## 12:12  London Paddington                       9     On time
## 12:13  London Paddington                       14    On time
## 12:15  London Paddington                       12    On time
## 12:19  Newbury                                 1     On time
## 12:20  Swansea                                 11    13:23
## 12:25  London Paddington                       7     On time
## 12:35  London Waterloo                         4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  Cheltenham Spa                          10    On time
## 12:39  Manchester Piccadilly                   15    On time
## 12:43  London Paddington                       14    On time
## 12:53  London Paddington                       9     On time
## 12:55  Penzance                                11    On time
## 12:56  Oxford                                  10    On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
## 12:18  Basingstoke                             BUS   On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 13:00  Basingstoke                             BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-10 10:04:07
## Time   To                                      Plat  Expected
## 11:09  Cardiff Central                         9     On time
## 11:12  Ealing Broadway                         15    On time
## 11:14  Great Malvern                           9     On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:17  London Paddington                       10    On time
## 11:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:21  London Waterloo                         4     On time
## 11:22  Ealing Broadway                         14    On time
## 11:26  Didcot Parkway                          12    On time
## 11:27  Plymouth                                7     On time
## 11:38  Redhill                                 6     On time
## 11:44  Bedwyn                                  1     On time
## 11:51  London Waterloo                         4     On time
## 11:52  Ealing Broadway                         14    On time
## 11:54  Paignton                                -     Cancelled
##        via Bristol                             
## 11:58  London Paddington                       11    On time
## 11:58  Swindon                                 -     On time
## 12:00  London Paddington                       10A   On time
## 12:09  Swansea                                 9     On time
## 12:11  London Paddington                       10    On time
## 12:12  Ealing Broadway                         15    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:17  Hereford                                9     On time
## 12:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:21  London Waterloo                         4     On time
## 12:22  Ealing Broadway                         14    On time
## 12:26  Didcot Parkway                          12    On time
## 12:27  Penzance                                7     On time
## 12:30  London Paddington                       11    13:24
## 12:41  Redhill                                 6     On time
## 12:42  London Paddington                       10    On time
## 12:44  Newbury                                 1     On time
## 12:46  Bournemouth                             15    On time
## 12:52  Ealing Broadway                         14    On time
## 12:52  London Waterloo                         4     On time
## 12:54  Weston-super-Mare                       9     On time
## 12:55  London Paddington                       11    On time
## 13:00  London Paddington                       10    On time
## 13:03  Exeter St Davids                        -     Cancelled
## 11:38  Basingstoke                             BUS   On time
## 11:52  Winchester                              BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 12:38  Basingstoke                             BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
