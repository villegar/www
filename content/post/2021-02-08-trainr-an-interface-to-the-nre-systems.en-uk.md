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

## Example (Last rendered on 2022-12-11 14:04)

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
## Reading (RDG) Station Board on 2022-12-11 14:04:12
## Time   From                                    Plat  Expected
## 13:48  London Paddington                       9     Delayed
## 14:03  Abbey Wood                              14    On time
## 14:05  Ascot                                   4     14:02
## 14:05  London Paddington                       9     13:58
## 14:08  Guildford                               6     On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:10  Didcot Parkway                          13A   On time
## 14:10  London Paddington                       8B    On time
## 14:14  Salisbury                               2     14:21
## 14:19  Newbury                                 1     On time
## 14:21  London Paddington                       13B   14:25
## 14:25  Oxford                                  10A   On time
## 14:26  London Paddington                       7     On time
## 14:32  Ascot                                   4     On time
## 14:32  Basingstoke                             2     14:35
## 14:33  Abbey Wood                              14    On time
## 14:38  Guildford                               5     On time
## 14:39  Manchester Piccadilly                   13    On time
## 14:43  London Paddington                       8B    On time
## 14:44  Swansea                                 10    On time
## 14:48  London Paddington                       9     On time
## 14:56  Penzance                                11    15:05
## 14:58  Hereford                                10    On time
## 14:58  London Paddington                       7     On time
## 15:02  Ascot                                   4     On time
## 15:03  Abbey Wood                              14    On time
## 15:05  London Paddington                       9     On time
## 15:06  Southampton Central                     8     On time
## 15:08  Guildford                               6     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15    On time
## 15:14  Salisbury                               1     On time
## 15:17  London Paddington                       9     On time
## 15:21  Bedwyn                                  3     On time
## 15:21  London Paddington                       12B   On time
## 15:25  Oxford                                  10A   On time
## 15:26  London Paddington                       7     On time
## 15:32  Ascot                                   4     On time
## 15:32  Basingstoke                             2     On time
## 15:33  Abbey Wood                              14    On time
## 15:34  Exeter St Davids                        11    On time
## 15:38  Guildford                               5     On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:45  London Paddington                       8B    On time
## 15:45  Swansea                                 10    On time
## 15:48  London Paddington                       9     On time
## 15:56  Great Malvern                           10    On time
## 15:58  Exeter St Davids                        11    On time
## 16:02  Ascot                                   4     On time
## 16:03  Abbey Wood                              14    On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-11 14:04:18
## Time   To                                      Plat  Expected
## 13:55  Bristol Temple Meads                    9     Delayed
## 14:09  Swansea                                 9     On time
## 14:13  London Paddington                       10    On time
## 14:14  Ealing Broadway                         13A   On time
## 14:14  Hereford                                8B    On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 14:21  Guildford                               5     On time
## 14:24  Abbey Wood                              14    On time
## 14:24  Ascot                                   4     On time
## 14:24  Salisbury                               2     On time
## 14:25  Didcot Parkway                          13B   14:25
## 14:26  London Paddington                       10A   On time
## 14:28  Penzance                                7     On time
## 14:37  Basingstoke                             2     On time
## 14:42  Guildford                               6     On time
## 14:43  Newbury                                 1     On time
## 14:46  London Paddington                       10    On time
## 14:48  Oxford                                  8B    On time
## 14:54  Abbey Wood                              14    On time
## 14:54  Ascot                                   4     On time
## 14:55  Taunton                                 9     On time
## 14:58  London Paddington                       11    15:06
## 15:01  Exeter St Davids                        7     On time
## 15:02  London Paddington                       10    On time
## 15:09  Swansea                                 9     On time
## 15:13  London Paddington                       11    On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           9B    On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:21  Guildford                               5     On time
## 15:24  Abbey Wood                              14    On time
## 15:24  Ascot                                   4     On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:25  Didcot Parkway                          12B   On time
## 15:25  London Paddington                       10A   On time
## 15:28  Plymouth                                7     On time
## 15:33  Salisbury                               1     On time
## 15:37  Basingstoke                             2     On time
## 15:41  Guildford                               6     On time
## 15:43  Bedwyn                                  3     On time
## 15:43  London Paddington                       11    On time
## 15:47  London Paddington                       10    On time
## 15:48  Oxford                                  8B    On time
## 15:52  Southampton Central                     7     On time
## 15:54  Abbey Wood                              14    On time
## 15:54  Ascot                                   4     On time
## 15:55  Taunton                                 9     On time
## 15:57  London Paddington                       10    On time
## 16:00  London Paddington                       11    On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
