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

## Example (Last rendered on 2023-03-19 18:04)

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
## Reading (RDG) Station Board on 2023-03-19 18:04:01
## Time   From                                    Plat  Expected
## 17:53  London Paddington                       9     18:15
## 17:56  London Paddington                       8     Delayed
## 17:57  Exeter St Davids                        11    18:07
## 17:57  Hereford                                10    18:01
## 18:02  Ascot                                   4     On time
## 18:06  Bristol Temple Meads                    10A   18:09
## 18:07  London Paddington                       9     18:14
## 18:11  Redhill                                 6     On time
## 18:12  London Paddington                       9     18:17
## 18:13  Didcot Parkway                          15A   On time
## 18:13  London Paddington                       12B   On time
## 18:21  Newbury                                 1     On time
## 18:23  Cardiff Central                         10A   18:28
## 18:23  London Paddington                       9     18:37
## 18:23  Oxford                                  13A   On time
## 18:26  London Paddington                       7     On time
## 18:33  Abbey Wood                              14    18:37
## 18:33  Cheltenham Spa                          11A   On time
## 18:34  Ascot                                   4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   13A   On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:44  Swansea                                 10    On time
## 18:47  London Paddington                       8B    On time
## 18:53  London Paddington                       9     On time
## 18:56  Bournemouth                             8     On time
## 18:56  Great Malvern                           10A   On time
## 18:58  Exeter St Davids                        11    On time
## 18:59  London Paddington                       7     19:13
## 19:02  Ascot                                   4     On time
## 19:03  Abbey Wood                              14    On time
## 19:07  London Paddington                       9     On time
## 19:10  Taunton                                 10    On time
## 19:11  Redhill                                 15    On time
## 19:12  London Paddington                       9     On time
## 19:13  Didcot Parkway                          13A   On time
## 19:13  London Paddington                       12B   On time
## 19:19  Bedwyn                                  1     On time
## 19:23  London Paddington                       9     On time
## 19:25  Oxford                                  10A   On time
## 19:26  London Paddington                       7     On time
## 19:32  Ascot                                   6     On time
## 19:33  Abbey Wood                              14    On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  Exeter St Davids                        11    On time
## 19:39  London Paddington                       9     On time
## 19:39  Manchester Piccadilly                   7     On time
## 19:47  London Paddington                       8B    On time
## 19:48  Swansea                                 10    On time
## 19:53  London Paddington                       9B    On time
## 19:55  Hereford                                10    On time
## 19:57  Exeter St Davids                        11    On time
## 20:02  Ascot                                   4     On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:23  Basingstoke                             BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:00  Winchester                              BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:23  Bramley (Hampshire)                     BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-19 18:04:07
## Time   To                                      Plat  Expected
## 17:55  Weston-super-Mare                       9     18:16
## 17:58  Cheltenham Spa                          8     Delayed
## 17:59  London Paddington                       11    18:08
## 18:01  London Paddington                       10    18:04
## 18:09  Swansea                                 9     18:15
## 18:11  London Paddington                       10A   On time
## 18:14  Ealing Broadway                         15A   On time
## 18:14  Great Malvern                           9     18:18
## 18:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:24  Abbey Wood                              14    On time
## 18:24  Ascot                                   4     On time
## 18:24  London Paddington                       10A   18:29
## 18:25  Bristol Temple Meads                    9     18:38
## 18:25  Didcot Parkway                          12B   On time
## 18:26  London Paddington                       13A   On time
## 18:28  Exeter St Davids                        7     On time
## 18:33  London Paddington                       11A   On time
## 18:41  London Paddington                       11    On time
## 18:41  Redhill                                 6     On time
## 18:43  Newbury                                 1     On time
## 18:46  Bournemouth                             13A   On time
## 18:46  London Paddington                       10    On time
## 18:49  Oxford                                  8B    On time
## 18:54  Abbey Wood                              14    On time
## 18:54  Ascot                                   4     On time
## 18:55  Weston-super-Mare                       9     On time
## 19:00  London Paddington                       11    On time
## 19:01  Exeter St Davids                        7     19:14
## 19:02  London Paddington                       10A   On time
## 19:09  Swansea                                 9     On time
## 19:11  London Paddington                       10    On time
## 19:13  Ealing Broadway                         13A   On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:24  Abbey Wood                              14    On time
## 19:24  Ascot                                   4     On time
## 19:25  Bristol Temple Meads                    9     On time
## 19:25  Didcot Parkway                          12B   On time
## 19:26  London Paddington                       10A   On time
## 19:28  Exeter St Davids                        7     On time
## 19:40  Swindon                                 9     On time
## 19:42  London Paddington                       11    On time
## 19:43  Bedwyn                                  1     On time
## 19:49  Oxford                                  8B    On time
## 19:50  London Paddington                       10    On time
## 19:54  Abbey Wood                              14    On time
## 19:54  Ascot                                   6     On time
## 19:55  Bristol Temple Meads                    9B    On time
## 19:58  London Paddington                       11    On time
## 20:01  London Paddington                       10    On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Basingstoke                             BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:52  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
