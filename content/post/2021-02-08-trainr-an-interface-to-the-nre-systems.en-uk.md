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

## Example (Last rendered on 2024-01-07 17:04)

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
## Reading (RDG) Station Board on 2024-01-07 17:04:24.929196
## Time   From                                    Plat  Expected
## 16:31  London Paddington                       7B    16:34
## 16:49  Manchester Piccadilly                   3     17:05
## 16:50  Swansea                                 10    17:25
## 16:51  London Paddington                       8B    17:04
## 16:57  London Paddington                       7     17:06
## 16:58  Penzance                                11    17:15
## 17:03  Bournemouth                             12B   On time
## 17:08  Redhill                                 4     17:11
## 17:09  Hereford                                10A   17:17
## 17:12  Abbey Wood                              9     On time
## 17:13  Sheffield                               13    17:22
## 17:15  London Paddington                       10    17:18
## 17:20  London Paddington                       8     Delayed
## 17:21  Theale                                  3     On time
## 17:23  Oxford                                  10    17:29
## 17:24  Weston-super-Mare                       11    17:43
## 17:26  London Paddington                       7     17:35
## 17:31  London Paddington                       8     On time
## 17:32  Basingstoke                             2     17:39
## 17:36  Didcot Parkway                          15    On time
## 17:37  Paignton                                -     Cancelled
## 17:38  Gatwick Airport                         4     On time
## 17:42  Abbey Wood                              14    17:46
## 17:47  London Paddington                       8B    On time
## 17:49  Manchester Piccadilly                   3     18:05
## 17:51  Swansea                                 10A   17:57
## 17:58  Plymouth                                11    18:01
## 18:03  Bournemouth                             3     On time
## 18:08  Redhill                                 4     On time
## 18:09  Ledbury                                 10    18:27
## 18:12  Abbey Wood                              14    On time
## 18:12  London Paddington                       7B    On time
## 18:15  London Paddington                       12    On time
## 18:21  Theale                                  1     On time
## 18:23  Oxford                                  10A   On time
## 18:24  Plymouth                                11    On time
## 18:27  London Paddington                       7     On time
## 18:30  London Paddington                       8B    On time
## 18:32  Basingstoke                             2     On time
## 18:36  Didcot Parkway                          15    On time
## 18:38  Gatwick Airport                         4     On time
## 18:42  Abbey Wood                              14    On time
## 18:48  Manchester Piccadilly                   7     On time
## 18:50  Carmarthen                              10    On time
## 18:51  London Paddington                       8     On time
## 18:57  London Paddington                       7     On time
## 17:15  Swindon                                 BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:31  Staines                                 BUS   On time
## 17:32  Staines                                 BUS   On time
## 17:45  Swindon                                 BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:01  Staines                                 BUS   On time
## 18:02  Staines                                 BUS   On time
## 18:15  Swindon                                 BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:31  Staines                                 BUS   On time
## 18:32  Staines                                 BUS   On time
## 18:45  Swindon                                 BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:01  Staines                                 BUS   On time
## 19:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 17:04:26.88869
## Time   To                                      Plat  Expected
## 16:34  Bristol Temple Meads                    7B    Delayed
## 16:52  Oxford                                  8B    17:05
## 16:53  Bournemouth                             3     17:06
## 16:56  London Paddington                       10    17:26
## 17:01  Plymouth                                7     17:07
## 17:04  London Paddington                       11    17:16
## 17:07  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 17:12  London Paddington                       10A   17:18
## 17:12  Salisbury                               2     On time
## 17:14  Great Malvern                           7B    17:28
## 17:17  Swansea                                 10    17:19
## 17:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:25  London Paddington                       10    17:30
## 17:28  Abbey Wood                              9     On time
## 17:28  Didcot Parkway                          8     Delayed
## 17:28  Penzance                                7     17:36
## 17:33  Newcastle                               13B   On time
##        via Coventry & Doncaster                
## 17:34  Plymouth                                8     On time
##        via Bristol                             
## 17:36  London Paddington                       11    17:44
## 17:37  Basingstoke                             2     On time
## 17:37  London Paddington                       15    On time
## 17:43  London Paddington                       -     Cancelled
## 17:45  Theale                                  3     On time
## 17:51  Redhill                                 4     On time
## 17:52  Oxford                                  8B    On time
## 17:53  Bournemouth                             3     18:06
## 17:59  Abbey Wood                              14    On time
## 18:00  London Paddington                       10A   On time
## 18:04  London Paddington                       11    On time
## 18:07  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 18:12  London Paddington                       10    18:28
## 18:14  Great Malvern                           9     On time
## 18:17  Swansea                                 7B    On time
## 18:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:25  London Paddington                       10A   On time
## 18:28  Didcot Parkway                          12    On time
## 18:28  Penzance                                7     On time
## 18:29  Abbey Wood                              14    On time
## 18:34  Bristol Temple Meads                    8B    On time
## 18:36  London Paddington                       11    On time
## 18:37  Basingstoke                             2     On time
## 18:37  London Paddington                       15    On time
## 18:43  Theale                                  1     On time
## 18:51  Redhill                                 4     On time
## 18:52  Oxford                                  8     On time
## 18:53  Bournemouth                             7     On time
## 18:59  Abbey Wood                              14    On time
## 19:00  London Paddington                       10    On time
## 19:01  Plymouth                                7     On time
## 17:05  Swindon                                 BUS   On time
## 17:25  Staines                                 BUS   On time
## 17:27  Staines                                 BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:40  Swindon                                 BUS   On time
## 17:55  Staines                                 BUS   On time
## 17:57  Staines                                 BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:05  Swindon                                 BUS   On time
## 18:25  Staines                                 BUS   On time
## 18:27  Staines                                 BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:40  Swindon                                 BUS   On time
## 18:55  Staines                                 BUS   On time
## 18:57  Staines                                 BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
