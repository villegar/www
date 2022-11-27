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

## Example (Last rendered on 2022-11-27 12:04)

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
## Reading (RDG) Station Board on 2022-11-27 12:04:28
## Time   From                                    Plat  Expected
## 11:35  Plymouth                                11    11:59
## 11:56  London Paddington                       8     12:00
## 11:58  Great Malvern                           14A   On time
## 11:58  Plymouth                                10    12:04
## 12:05  London Paddington                       8     On time
## 12:06  Abbey Wood                              12    On time
## 12:10  Didcot Parkway                          15A   On time
## 12:11  London Paddington                       12    On time
## 12:14  Bristol Temple Meads                    8     12:16
## 12:19  Newbury                                 1     On time
## 12:24  London Paddington                       12B   On time
## 12:25  London Waterloo                         4     On time
## 12:25  Oxford                                  15A   On time
## 12:27  London Paddington                       7     On time
## 12:32  Gloucester                              15A   On time
## 12:33  Basingstoke                             2     On time
## 12:36  Abbey Wood                              9     On time
## 12:39  Manchester Piccadilly                   13    On time
## 12:45  Swansea                                 14    12:50
## 12:47  London Paddington                       8B    On time
## 12:47  Salisbury                               1     On time
## 12:55  Exeter St Davids                        11    13:10
## 12:55  Great Malvern                           15A   On time
## 12:56  London Paddington                       8     On time
## 12:58  London Paddington                       -     Cancelled
## 12:58  London Waterloo                         4     On time
## 13:05  London Paddington                       8     On time
## 13:05  Southampton Central                     7     On time
## 13:08  Abbey Wood                              9     On time
## 13:10  Didcot Parkway                          15A   On time
## 13:11  London Paddington                       12B   On time
## 13:14  Weston-super-Mare                       14    On time
## 13:19  Bedwyn                                  1     On time
## 13:21  Bristol Parkway                         15    On time
## 13:24  London Paddington                       12    On time
## 13:25  London Waterloo                         4     On time
## 13:25  Oxford                                  14A   On time
## 13:26  Paignton                                11    13:32
## 13:27  London Paddington                       7     On time
## 13:33  Basingstoke                             2     On time
## 13:36  Abbey Wood                              14    On time
## 13:39  Manchester Piccadilly                   7     13:43
## 13:41  Bristol Temple Meads                    15    On time
## 13:45  Swansea                                 12    On time
## 13:47  London Paddington                       8B    On time
## 13:47  Salisbury                               1     On time
## 13:55  Great Malvern                           15A   On time
## 13:56  London Paddington                       8     On time
## 13:58  London Waterloo                         6     On time
## 13:58  Plymouth                                11    On time
## 12:04  Guildford                               BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 12:40  Guildford                               BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:18  Guildford                               BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-27 12:04:33
## Time   To                                      Plat  Expected
## 11:46  London Paddington                       11    12:04
## 11:58  London Paddington                       14A   Delayed
## 12:00  London Paddington                       10    12:05
## 12:07  Carmarthen                              8     On time
## 12:12  Hereford                                12    On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         15A   On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:16  London Paddington                       8     12:17
## 12:20  Abbey Wood                              12    On time
## 12:21  London Waterloo                         6     On time
## 12:26  London Paddington                       15A   On time
## 12:28  Didcot Parkway                          12B   On time
## 12:28  Plymouth                                7     On time
## 12:38  Basingstoke                             2     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       15A   On time
## 12:49  Oxford                                  8B    On time
## 12:50  Abbey Wood                              9     On time
## 12:51  London Waterloo                         4     On time
## 12:55  London Paddington                       14    On time
## 12:57  Weston-super-Mare                       8     On time
## 12:58  London Paddington                       11    13:11
## 13:00  London Paddington                       15A   On time
## 13:01  Paignton                                -     Cancelled
## 13:07  Swansea                                 8     On time
## 13:12  Great Malvern                           12B   On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:14  Ealing Broadway                         15A   On time
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 13:16  London Paddington                       14    On time
## 13:19  Abbey Wood                              9     On time
## 13:21  London Waterloo                         4     On time
## 13:22  London Paddington                       15    On time
## 13:26  London Paddington                       14A   On time
## 13:28  Didcot Parkway                          12    On time
## 13:28  Plymouth                                7     On time
## 13:29  London Paddington                       11    13:33
## 13:38  Basingstoke                             2     On time
## 13:43  Bedwyn                                  1     On time
## 13:45  London Paddington                       15    On time
## 13:49  Oxford                                  8B    On time
## 13:50  London Paddington                       12    On time
## 13:51  London Waterloo                         4     On time
## 13:52  Southampton Central                     7     On time
## 13:54  Abbey Wood                              14    On time
## 13:57  Bristol Temple Meads                    8     On time
## 14:00  London Paddington                       11    On time
## 14:02  London Paddington                       15A   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Guildford                               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:23  Guildford                               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:56  Guildford                               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
