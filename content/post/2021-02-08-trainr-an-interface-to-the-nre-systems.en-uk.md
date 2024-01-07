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

## Example (Last rendered on 2024-01-07 19:05)

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
## Reading (RDG) Station Board on 2024-01-07 19:05:01.27406
## Time   From                                    Plat  Expected
## 18:27  London Paddington                       7     19:03
## 18:36  Didcot Parkway                          15A   19:06
## 18:50  Carmarthen                              10    19:16
## 18:57  London Paddington                       12    19:05
## 18:58  Penzance                                -     Cancelled
## 19:03  Southampton Central                     8B    On time
## 19:08  Redhill                                 4     19:10
## 19:09  Worcester Foregate Street               10    19:28
## 19:12  Abbey Wood                              14    On time
## 19:12  London Paddington                       7     19:21
## 19:15  London Paddington                       12    19:39
## 19:19  Theale                                  1     On time
## 19:21  Oxford                                  10A   Delayed
## 19:26  Taunton                                 -     Cancelled
## 19:27  London Paddington                       -     Cancelled
## 19:32  Basingstoke                             2     19:47
## 19:36  Didcot Parkway                          15A   On time
## 19:38  Gatwick Airport                         4     On time
## 19:40  Paignton                                11    19:47
## 19:42  Abbey Wood                              14    19:46
## 19:45  Swansea                                 10    On time
## 19:47  London Paddington                       -     Cancelled
## 19:49  Manchester Piccadilly                   3     On time
## 19:58  Taunton                                 11    On time
## 20:03  Bournemouth                             3     On time
## 20:07  London Paddington                       8     On time
## 20:08  Redhill                                 15    On time
## 20:09  Hereford                                10    On time
## 20:12  Abbey Wood                              14    On time
## 20:12  London Paddington                       7     On time
## 20:18  London Paddington                       12    On time
## 20:18  Theale                                  1     On time
## 20:23  Exeter St Davids                        11    On time
## 20:23  Oxford                                  10    On time
## 20:27  London Paddington                       7     On time
## 20:32  Basingstoke                             2     On time
## 20:35  London Paddington                       13    On time
## 20:36  Didcot Parkway                          15    On time
## 20:37  London Paddington                       7     On time
## 20:38  Gatwick Airport                         4     On time
## 20:42  Abbey Wood                              14    On time
## 20:42  Swansea                                 10    On time
## 20:46  Plymouth                                11    On time
## 20:49  London Paddington                       8     On time
## 20:49  Manchester Piccadilly                   3     On time
## 20:58  Penzance                                10    On time
## 19:15  Swindon                                 BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:31  Staines                                 BUS   On time
## 19:32  Staines                                 BUS   On time
## 19:45  Swindon                                 BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 20:01  Staines                                 BUS   On time
## 20:02  Staines                                 BUS   On time
## 20:10  Heathrow Airport T3 (Bus)               BUS   On time
## 20:15  Swindon                                 BUS   On time
## 20:31  Staines                                 BUS   On time
## 20:32  Staines                                 BUS   On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
## 20:45  Swindon                                 BUS   On time
## 21:01  Staines                                 BUS   On time
## 21:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 19:05:04.144135
## Time   To                                      Plat  Expected
## 18:28  Penzance                                7     19:05
## 18:37  London Paddington                       15A   19:07
## 19:00  London Paddington                       10    19:17
## 19:01  Plymouth                                12    19:06
## 19:04  London Paddington                       -     Cancelled
## 19:07  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:12  London Paddington                       10    19:29
## 19:14  Hereford                                9B    On time
## 19:20  Swansea                                 7     19:22
## 19:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:28  Didcot Parkway                          12    19:40
## 19:28  London Paddington                       10A   Delayed
## 19:28  Plymouth                                -     Cancelled
## 19:29  Abbey Wood                              14    On time
## 19:34  Bristol Temple Meads                    8B    On time
## 19:36  London Paddington                       -     Cancelled
## 19:37  Basingstoke                             2     On time
## 19:37  London Paddington                       15A   On time
## 19:43  London Paddington                       11    19:52
## 19:43  Theale                                  1     On time
## 19:52  Oxford                                  -     Cancelled
## 19:53  Bournemouth                             3     On time
## 19:55  London Paddington                       10    On time
## 19:59  Abbey Wood                              14    On time
## 20:04  London Paddington                       11    On time
## 20:07  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 20:12  Gatwick Airport                         4     On time
##        via Guildford                           
## 20:12  London Paddington                       10    On time
## 20:14  Great Malvern                           8     On time
## 20:20  Swansea                                 7     On time
## 20:24  London Paddington                       11    On time
## 20:26  London Paddington                       10    On time
## 20:28  Didcot Parkway                          12    On time
## 20:28  Plymouth                                7     On time
## 20:29  Abbey Wood                              14    On time
## 20:37  Basingstoke                             2     On time
## 20:37  London Paddington                       15    On time
## 20:42  Weston-super-Mare                       7     On time
## 20:45  Theale                                  1     On time
## 20:48  London Paddington                       10    On time
## 20:52  Oxford                                  8     On time
## 20:53  Bournemouth                             3     On time
## 20:55  London Paddington                       11    On time
## 20:59  Abbey Wood                              14    On time
## 21:04  London Paddington                       10    On time
## 19:05  Swindon                                 BUS   On time
## 19:25  Staines                                 BUS   On time
## 19:27  Staines                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:40  Swindon                                 BUS   On time
## 19:55  Staines                                 BUS   On time
## 19:57  Staines                                 BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Newbury                                 BUS   On time
## 20:05  Swindon                                 BUS   On time
## 20:25  Staines                                 BUS   On time
## 20:27  Staines                                 BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:45  Swindon                                 BUS   On time
## 20:55  Staines                                 BUS   On time
## 20:57  Staines                                 BUS   On time
## 21:00  Newbury                                 BUS   On time
```
