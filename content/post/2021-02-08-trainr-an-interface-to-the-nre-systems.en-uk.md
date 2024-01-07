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

## Example (Last rendered on 2024-01-07 13:05)

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
## Reading (RDG) Station Board on 2024-01-07 13:05:18.877343
## Time   From                                    Plat  Expected
## 12:49  Manchester Piccadilly                   3     13:01
## 12:57  London Paddington                       7     13:10
## 12:58  Penzance                                11    13:03
## 13:03  Bournemouth                             8     13:18
## 13:08  Redhill                                 4     13:10
## 13:09  Great Malvern                           10    13:17
## 13:12  Abbey Wood                              9     On time
## 13:15  London Paddington                       8     13:17
## 13:20  Slough                                  14A   Delayed
## 13:20  Theale                                  1     On time
## 13:21  Oxford                                  10    13:32
## 13:23  Newton Abbot                            11    14:30
## 13:28  Bristol Temple Meads                    -     Cancelled
## 13:31  London Paddington                       -     Cancelled
## 13:32  Basingstoke                             2     13:47
## 13:38  Didcot Parkway                          -     Cancelled
## 13:40  Gatwick Airport                         4     On time
## 13:46  Abbey Wood                              9     On time
## 13:47  Salisbury                               2     On time
## 13:49  Manchester Piccadilly                   3     On time
## 13:50  London Paddington                       8     Delayed
## 13:50  Swansea                                 -     Cancelled
## 13:58  Penzance                                11    14:31
## 14:02  Bournemouth                             8A    On time
## 14:08  Redhill                                 -     Cancelled
## 14:09  Great Malvern                           -     Cancelled
## 14:12  Abbey Wood                              9     On time
## 14:15  London Paddington                       7     On time
## 14:19  London Paddington                       8     Delayed
## 14:20  Theale                                  1     On time
## 14:23  Bristol Temple Meads                    11    On time
## 14:23  Oxford                                  10    On time
## 14:26  London Paddington                       7     On time
## 14:31  London Paddington                       8     On time
## 14:32  Basingstoke                             2     On time
## 14:38  Didcot Parkway                          8     On time
## 14:38  Gatwick Airport                         4     On time
## 14:46  Abbey Wood                              9     On time
## 14:49  London Paddington                       8     On time
## 14:49  Manchester Piccadilly                   3     On time
## 14:49  Salisbury                               2     On time
## 14:51  Swansea                                 11    On time
## 14:57  London Paddington                       10    On time
## 14:58  Penzance                                11    On time
## 13:15  Heathrow Airport T3 (Bus)               BUS   On time
## 13:15  Swindon                                 BUS   On time
## 13:31  Staines                                 BUS   On time
## 13:32  Staines                                 BUS   On time
## 13:45  Heathrow Airport T3 (Bus)               BUS   On time
## 13:45  Swindon                                 BUS   On time
## 14:01  Staines                                 BUS   On time
## 14:02  Staines                                 BUS   On time
## 14:15  Heathrow Airport T3 (Bus)               BUS   On time
## 14:15  Swindon                                 BUS   On time
## 14:31  Staines                                 BUS   On time
## 14:32  Staines                                 BUS   On time
## 14:45  Heathrow Airport T3 (Bus)               BUS   On time
## 14:45  Swindon                                 BUS   On time
## 15:01  Staines                                 BUS   On time
## 15:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 13:05:22.815671
## Time   To                                      Plat  Expected
## 12:53  Bournemouth                             3     13:05
## 13:01  Paignton                                7     13:11
## 13:06  London Paddington                       11    On time
## 13:07  Manchester Piccadilly                   8     13:19
##        via Coventry & Stoke-on-Trent           
## 13:12  London Paddington                       10    13:18
## 13:12  Yeovil Pen Mill                         2     On time
## 13:14  Hereford                                7     13:23
## 13:17  Swansea                                 8     13:18
## 13:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 13:24  London Paddington                       11    14:31
## 13:26  London Paddington                       10    13:33
## 13:28  Abbey Wood                              9     On time
## 13:28  Didcot Parkway                          14A   Delayed
## 13:28  Plymouth                                7     13:46
## 13:34  Bristol Temple Meads                    -     Cancelled
## 13:36  London Paddington                       -     Cancelled
## 13:37  Basingstoke                             2     On time
## 13:39  London Paddington                       8     On time
## 13:43  Theale                                  1     On time
## 13:51  Redhill                                 4     On time
## 13:52  Oxford                                  8     Delayed
## 13:53  Bournemouth                             3     On time
## 13:56  London Paddington                       -     Cancelled
## 13:58  Abbey Wood                              9     On time
## 14:04  London Paddington                       11    14:32
## 14:07  Manchester Piccadilly                   8A    On time
##        via Coventry & Stoke-on-Trent           
## 14:12  London Paddington                       -     Cancelled
## 14:12  Salisbury                               2     On time
## 14:14  Great Malvern                           8     On time
## 14:17  Swansea                                 7     On time
## 14:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 14:25  London Paddington                       10    On time
## 14:28  Abbey Wood                              9     On time
## 14:28  Didcot Parkway                          8     Delayed
## 14:28  Penzance                                7     On time
## 14:34  Taunton                                 8     On time
## 14:36  London Paddington                       11    On time
## 14:37  Basingstoke                             2     On time
## 14:39  London Paddington                       8     On time
## 14:43  Theale                                  1     On time
## 14:51  Redhill                                 4     On time
## 14:52  Oxford                                  8     On time
## 14:53  Bournemouth                             3     On time
## 14:54  London Paddington                       11    On time
## 14:58  Abbey Wood                              9     On time
## 15:01  Exeter St Davids                        10    On time
## 15:04  London Paddington                       11    On time
## 13:05  Swindon                                 BUS   On time
## 13:25  Staines                                 BUS   On time
## 13:27  Staines                                 BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:40  Swindon                                 BUS   On time
## 13:55  Staines                                 BUS   On time
## 13:57  Staines                                 BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:05  Swindon                                 BUS   On time
## 14:25  Staines                                 BUS   On time
## 14:27  Staines                                 BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:40  Swindon                                 BUS   On time
## 14:55  Staines                                 BUS   On time
## 14:57  Staines                                 BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
