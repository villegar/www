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

## Example (Last rendered on 2024-01-07 15:05)

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
## Reading (RDG) Station Board on 2024-01-07 15:05:29.120572
## Time   From                                    Plat  Expected
## 14:49  Manchester Piccadilly                   3     14:59
## 14:58  Penzance                                11    15:16
## 15:03  Bournemouth                             -     Cancelled
## 15:08  Guildford                               4     15:11
## 15:09  Worcester Shrub Hill                    10    15:29
## 15:12  Abbey Wood                              9     On time
## 15:15  London Paddington                       7     On time
## 15:19  London Paddington                       -     Cancelled
## 15:20  Theale                                  3     On time
## 15:23  Oxford                                  10A   15:32
## 15:25  Weston-super-Mare                       11A   15:39
## 15:26  London Paddington                       7     15:35
## 15:31  London Paddington                       8     On time
## 15:32  Basingstoke                             2     On time
## 15:37  Exeter St Davids                        -     Cancelled
## 15:38  Didcot Parkway                          8     On time
## 15:38  Gatwick Airport                         4     15:41
## 15:46  Abbey Wood                              9     On time
## 15:47  Salisbury                               2     On time
## 15:49  Manchester Piccadilly                   -     Cancelled
## 15:50  Carmarthen                              10A   On time
## 15:51  London Paddington                       8     On time
## 15:58  Plymouth                                11    On time
## 16:03  Bournemouth                             3     On time
## 16:08  Redhill                                 4     On time
## 16:09  Worcester Foregate Street               10    On time
## 16:12  Abbey Wood                              9     On time
## 16:15  London Paddington                       7     On time
## 16:15  Theale                                  3     On time
## 16:19  London Paddington                       8     On time
## 16:21  Oxford                                  10    On time
## 16:23  Bristol Temple Meads                    11    On time
## 16:26  London Paddington                       7     On time
## 16:31  London Paddington                       7     On time
## 16:32  Basingstoke                             2     On time
## 16:38  Didcot Parkway                          8     On time
## 16:38  Gatwick Airport                         4     On time
## 16:46  Abbey Wood                              9     On time
## 16:47  Salisbury                               2     On time
## 16:49  Manchester Piccadilly                   3     On time
## 16:50  Swansea                                 10    On time
## 16:51  London Paddington                       8     On time
## 16:57  London Paddington                       7     On time
## 16:58  Penzance                                11    On time
## 15:15  Heathrow Airport T3 (Bus)               BUS   On time
## 15:15  Swindon                                 BUS   On time
## 15:31  Staines                                 BUS   On time
## 15:32  Staines                                 BUS   On time
## 15:45  Heathrow Airport T3 (Bus)               BUS   On time
## 15:45  Swindon                                 BUS   On time
## 16:01  Staines                                 BUS   On time
## 16:02  Staines                                 BUS   On time
## 16:15  Heathrow Airport T3 (Bus)               BUS   On time
## 16:15  Swindon                                 BUS   On time
## 16:31  Staines                                 BUS   On time
## 16:32  Staines                                 BUS   On time
## 16:45  Heathrow Airport T3 (Bus)               BUS   On time
## 16:45  Swindon                                 BUS   On time
## 17:01  Staines                                 BUS   On time
## 17:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 15:05:33.433065
## Time   To                                      Plat  Expected
## 14:53  Bournemouth                             3     15:04
## 15:04  London Paddington                       11    15:17
## 15:07  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 15:12  Gillingham (Dorset)                     2     On time
## 15:12  London Paddington                       10    15:30
## 15:14  Great Malvern                           8B    On time
## 15:17  Swansea                                 7     On time
## 15:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:25  London Paddington                       10A   15:33
## 15:28  Abbey Wood                              9     On time
## 15:28  Didcot Parkway                          14    On time
## 15:28  Plymouth                                7     15:36
## 15:34  Taunton                                 8     On time
## 15:36  London Paddington                       11A   15:40
## 15:37  Basingstoke                             2     On time
## 15:39  London Paddington                       8     On time
## 15:43  London Paddington                       -     Cancelled
## 15:43  Theale                                  3     On time
## 15:51  Redhill                                 4     On time
## 15:52  Oxford                                  8     On time
## 15:53  Bournemouth                             -     Cancelled
## 15:56  London Paddington                       10A   On time
## 15:58  Abbey Wood                              9     On time
## 16:04  London Paddington                       11    On time
## 16:07  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 16:12  London Paddington                       10    On time
## 16:12  Salisbury                               2     On time
## 16:14  Great Malvern                           8     On time
## 16:17  Swansea                                 7     On time
## 16:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:26  London Paddington                       10    On time
## 16:28  Abbey Wood                              9     On time
## 16:28  Didcot Parkway                          8     On time
## 16:28  Penzance                                7     On time
## 16:34  Bristol Temple Meads                    7     On time
## 16:36  London Paddington                       11    On time
## 16:37  Basingstoke                             2     On time
## 16:39  London Paddington                       8     On time
## 16:43  Theale                                  3     On time
## 16:51  Redhill                                 4     On time
## 16:52  Oxford                                  8     On time
## 16:53  Bournemouth                             3     On time
## 16:56  London Paddington                       10    On time
## 16:58  Ealing Broadway                         9     On time
## 17:01  Plymouth                                7     On time
## 17:04  London Paddington                       11    On time
## 15:05  Swindon                                 BUS   On time
## 15:25  Staines                                 BUS   On time
## 15:27  Staines                                 BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:40  Swindon                                 BUS   On time
## 15:55  Staines                                 BUS   On time
## 15:57  Staines                                 BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:05  Swindon                                 BUS   On time
## 16:25  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:40  Swindon                                 BUS   On time
## 16:55  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
