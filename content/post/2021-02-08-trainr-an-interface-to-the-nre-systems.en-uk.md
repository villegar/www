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

## Example (Last rendered on 2023-03-19 20:04)

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
## Reading (RDG) Station Board on 2023-03-19 20:04:08
## Time   From                                    Plat  Expected
## 19:39  Manchester Piccadilly                   7     20:02
## 19:48  Swansea                                 11    20:04
## 19:55  Hereford                                10    19:58
## 20:04  Abbey Wood                              14    20:13
## 20:10  Bristol Temple Meads                    10    20:14
## 20:11  Redhill                                 15    20:13
## 20:12  London Paddington                       9B    20:15
## 20:13  Didcot Parkway                          13A   On time
## 20:19  London Paddington                       12B   On time
## 20:20  Newbury                                 1     On time
## 20:24  Oxford                                  10A   On time
## 20:27  London Paddington                       7     On time
## 20:32  Ascot                                   6     On time
## 20:33  Abbey Wood                              14    On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   14    On time
## 20:41  Exeter St Davids                        11    On time
## 20:47  London Paddington                       9B    On time
## 20:49  Swansea                                 10    20:55
## 20:53  London Paddington                       9     On time
## 20:58  Bournemouth                             8B    21:30
## 20:58  Exeter St Davids                        11    On time
## 20:58  Great Malvern                           10A   On time
## 21:02  Ascot                                   4     On time
## 21:03  Abbey Wood                              14    On time
## 21:07  London Paddington                       9     On time
## 21:11  Redhill                                 15B   On time
## 21:11  Taunton                                 10    On time
## 21:12  London Paddington                       12B   On time
## 21:12  London Paddington                       9B    On time
## 21:13  Didcot Parkway                          13A   On time
## 21:19  Bedwyn                                  1     On time
## 21:26  London Paddington                       7B    On time
## 21:32  Ascot                                   6     On time
## 21:33  Abbey Wood                              14    On time
## 21:39  Manchester Piccadilly                   13    On time
## 21:40  Gatwick Airport                         15    On time
## 21:42  London Paddington                       12B   On time
## 21:48  Swansea                                 10    On time
## 21:53  Great Malvern                           11A   On time
## 21:53  London Paddington                       9     On time
## 22:02  Ascot                                   6     On time
## 22:03  Abbey Wood                              14    On time
## 20:23  Basingstoke                             BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:00  Winchester                              BUS   On time
## 21:23  Bramley (Hampshire)                     BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-19 20:04:13
## Time   To                                      Plat  Expected
## 19:50  London Paddington                       11    20:05
## 20:01  London Paddington                       10    On time
## 20:09  Swansea                                 8B    On time
## 20:11  London Paddington                       10    20:15
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         13A   On time
## 20:14  Great Malvern                           9B    20:16
## 20:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 20:24  Abbey Wood                              14    On time
## 20:24  Ascot                                   4     On time
## 20:25  Didcot Parkway                          12B   On time
## 20:27  London Paddington                       10A   On time
## 20:28  Exeter St Davids                        7     On time
## 20:42  London Paddington                       11    On time
## 20:43  Newbury                                 1     On time
## 20:46  Southampton Central                     14    On time
## 20:49  Oxford                                  9B    On time
## 20:50  London Paddington                       10    20:56
## 20:54  Abbey Wood                              14    On time
## 20:54  Ascot                                   6     On time
## 20:55  Bristol Temple Meads                    9     On time
## 20:59  London Paddington                       11    On time
## 21:02  London Paddington                       10A   On time
## 21:09  Swansea                                 9     On time
## 21:11  London Paddington                       10    On time
## 21:12  Birmingham New Street                   8B    21:31
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Didcot Parkway                          12B   On time
## 21:14  Ealing Broadway                         13A   On time
## 21:15  Worcester Shrub Hill                    9B    On time
## 21:24  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        7B    On time
## 21:43  Bedwyn                                  1     On time
## 21:46  Oxford                                  12B   On time
## 21:46  Southampton Central                     13    On time
## 21:50  London Paddington                       10    On time
## 21:54  Ascot                                   6     On time
## 21:54  Ealing Broadway                         14    On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:55  London Paddington                       11A   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:52  Winchester                              BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:38  Bramley (Hampshire)                     BUS   On time
## 21:52  Winchester                              BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
