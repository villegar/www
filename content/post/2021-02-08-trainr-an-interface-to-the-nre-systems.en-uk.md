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

## Example (Last rendered on 2023-04-03 20:03)

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
## Reading (RDG) Station Board on 2023-04-03 20:03:30
## Time   From                                    Plat  Expected
## 20:17  London Paddington                       -     21:13
## 20:32  Cheltenham Spa                          7A    20:45
## 20:36  London Paddington                       -     Cancelled
## 20:44  Swansea                                 -     21:02
## 20:46  London Paddington                       -     Cancelled
## 20:55  London Paddington                       9     21:18
## 21:00  Penzance                                -     21:15
## 21:04  Basingstoke                             2     21:01
## 21:07  Bournemouth                             -     On time
## 21:09  Bristol Temple Meads                    -     21:14
## 21:10  London Paddington                       14    Delayed
## 21:11  London Paddington                       9     Delayed
## 21:13  Abbey Wood                              -     Cancelled
## 21:13  London Waterloo                         6     21:18
## 21:16  London Paddington                       -     Cancelled
## 21:20  London Paddington                       -     Cancelled
## 21:21  Bedwyn                                  -     On time
## 21:24  Oxford                                  -     Cancelled
## 21:25  London Paddington                       9     On time
## 21:27  London Paddington                       7     On time
## 21:28  Basingstoke                             2     On time
## 21:29  Didcot Parkway                          14A   On time
## 21:29  Redhill                                 5     On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:38  Newbury                                 13    On time
## 21:41  Abbey Wood                              14    On time
## 21:41  Manchester Piccadilly                   -     Cancelled
## 21:42  London Waterloo                         4     On time
## 21:44  Swansea                                 -     21:46
## 21:45  London Paddington                       -     Cancelled
## 21:46  London Paddington                       -     Cancelled
## 21:51  London Paddington                       -     Cancelled
## 21:53  Great Malvern                           -     Cancelled
## 21:56  Gatwick Airport                         15    On time
## 21:57  Basingstoke                             3     On time
## 22:00  Paignton                                -     On time
## 22:05  Didcot Parkway                          15A   On time
## 22:07  London Paddington                       13    On time
## 22:08  Exeter St Davids                        -     On time
## 22:11  Abbey Wood                              14    On time
## 22:11  London Paddington                       9     On time
## 22:15  London Paddington                       -     Cancelled
## 22:15  Newbury                                 15    On time
## 22:16  London Paddington                       -     22:20
## 22:18  Newbury                                 -     On time
## 22:25  Oxford                                  -     Cancelled
## 22:26  London Paddington                       9     22:29
## 22:32  Cheltenham Spa                          -     On time
## 22:34  Shalford                                14A   On time
## 22:39  Manchester Piccadilly                   -     Cancelled
## 22:40  Abbey Wood                              14    On time
## 22:40  Basingstoke                             2     On time
## 22:42  London Waterloo                         5     On time
## 22:43  Swansea                                 -     On time
## 22:45  London Paddington                       12    On time
## 22:47  Didcot Parkway                          15    On time
## 22:50  Salisbury                               11    On time
## 22:55  London Paddington                       13    On time
## 22:58  London Paddington                       -     Cancelled
## 22:59  Worcester Foregate Street               -     Cancelled
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
## Reading (RDG) Station Board on 2023-04-03 20:03:36
## Time   To                                      Plat  Expected
## 20:23  Didcot Parkway                          -     Cancelled
## 20:36  London Paddington                       7A    Delayed
## 20:36  Newbury                                 8B    Delayed
## 20:47  London Paddington                       -     21:03
## 20:51  Didcot Parkway                          12B   Delayed
## 20:57  Weston-super-Mare                       9     21:19
## 21:01  Gatwick Airport                         6     21:03
##        via Guildford                           
## 21:03  London Paddington                       -     21:16
## 21:05  Newbury                                 1     On time
## 21:09  London Waterloo                         4     On time
## 21:11  London Paddington                       -     21:15
## 21:13  Swansea                                 9     Delayed
## 21:14  Birmingham New Street                   -     Cancelled
##        via Coventry                            
## 21:18  Great Malvern                           -     Cancelled
## 21:22  Basingstoke                             2     On time
## 21:23  Didcot Parkway                          14    Delayed
## 21:23  London Paddington                       -     On time
## 21:26  London Paddington                       -     Cancelled
## 21:27  Abbey Wood                              -     Cancelled
## 21:27  Bristol Temple Meads                    9     On time
## 21:29  Plymouth                                7     On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:37  Ealing Broadway                         -     Cancelled
## 21:39  London Waterloo                         -     On time
## 21:43  London Paddington                       -     Cancelled
## 21:46  London Paddington                       -     21:46
## 21:48  Oxford                                  -     Cancelled
## 21:49  Didcot Parkway                          12    On time
## 21:52  Bournemouth                             3     On time
## 21:52  Bournemouth                             -     On time
## 21:52  Bournemouth                             -     Cancelled
## 21:53  Cheltenham Spa                          -     Cancelled
## 21:56  London Paddington                       -     Cancelled
## 21:57  Abbey Wood                              14    On time
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       -     On time
## 22:08  Ealing Broadway                         15A   On time
## 22:09  London Waterloo                         4     On time
## 22:10  London Paddington                       -     On time
## 22:13  Neath                                   9     On time
## 22:18  Didcot Parkway                          12    On time
## 22:18  Worcester Shrub Hill                    -     22:21
## 22:19  London Paddington                       -     On time
## 22:26  London Paddington                       -     Cancelled
## 22:27  Abbey Wood                              14    On time
## 22:27  Plymouth                                9     22:30
##        via Bristol                             
## 22:29  Basingstoke                             2     On time
## 22:35  London Paddington                       -     On time
## 22:46  London Paddington                       -     On time
## 22:47  Didcot Parkway                          12    On time
## 22:49  Southampton Central                     -     On time
## 22:49  Southampton Central                     -     On time
## 22:49  Southampton Central                     -     Cancelled
## 22:52  Basingstoke                             2     On time
## 22:57  Abbey Wood                              14    On time
## 22:57  Bristol Temple Meads                    13    On time
## 23:00  Oxford                                  -     Cancelled
## 23:01  London Paddington                       -     Cancelled
## 21:15  Birmingham New Street                   -     On time
##        via Coventry                            
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Bedwyn                                  BUS   On time
## 22:10  Newbury                                 BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
