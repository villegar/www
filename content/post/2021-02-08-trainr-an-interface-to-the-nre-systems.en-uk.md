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

## Example (Last rendered on 2024-01-06 18:49)

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
## Reading (RDG) Station Board on 2024-01-06 18:49:13.368334
## Time   From                                    Plat  Expected
## 17:48  Swansea                                 10    18:46
## 17:58  Plymouth                                11    Delayed
## 18:41  Manchester Piccadilly                   7B    On time
## 18:44  London Paddington                       12B   18:53
## 18:46  Swansea                                 10    19:13
## 18:49  Basingstoke                             2     On time
## 18:50  Ascot                                   6     18:45
## 18:53  London Paddington                       9     On time
## 18:57  Gatwick Airport                         5     On time
## 18:58  Great Malvern                           10    On time
## 18:58  London Paddington                       9     On time
## 19:01  Didcot Parkway                          15A   19:03
## 19:01  Salisbury                               3     On time
## 19:03  Penzance                                11    Delayed
## 19:06  Bournemouth                             7B    On time
## 19:10  Abbey Wood                              14    On time
## 19:10  Bristol Temple Meads                    10    On time
## 19:11  London Paddington                       9     19:25
## 19:14  London Paddington                       13B   19:18
## 19:15  London Paddington                       9     On time
## 19:20  Ascot                                   4     On time
## 19:22  Basingstoke                             2     On time
## 19:23  London Paddington                       9     On time
## 19:26  London Paddington                       9     19:55
## 19:28  Gatwick Airport                         5     On time
## 19:29  Newbury                                 -     Cancelled
## 19:31  Didcot Parkway                          15A   On time
## 19:31  London Paddington                       7     On time
## 19:40  Abbey Wood                              14    On time
## 19:41  London Paddington                       -     Cancelled
## 19:41  Manchester Piccadilly                   -     Cancelled
## 19:41  Weston-super-Mare                       10    On time
## 19:43  Theale                                  13B   On time
## 19:44  London Paddington                       12B   On time
## 19:46  London Paddington                       9B    On time
## 19:48  Swansea                                 10    20:03
## 19:50  Ascot                                   4     On time
## 19:50  Basingstoke                             2     On time
## 19:53  London Paddington                       9     On time
## 19:55  Salisbury                               1     On time
## 19:57  Gatwick Airport                         5     On time
## 19:58  Great Malvern                           10A   On time
## 19:58  Plymouth                                11    On time
## 20:01  Didcot Parkway                          15A   On time
## 20:06  York                                    3     On time
## 20:10  Abbey Wood                              14    On time
## 20:10  Bristol Temple Meads                    10    On time
## 20:11  Bournemouth                             13B   On time
## 20:11  London Paddington                       -     Cancelled
## 20:15  London Paddington                       9B    On time
## 20:16  London Paddington                       12B   On time
## 20:16  Newbury                                 -     Cancelled
## 20:20  Ascot                                   4     On time
## 20:22  Basingstoke                             2     On time
## 20:23  London Paddington                       9     On time
## 20:23  Oxford                                  10A   On time
## 20:26  London Paddington                       7     On time
## 20:29  Didcot Parkway                          15A   On time
## 20:33  Gatwick Airport                         14B   On time
## 20:34  Cheltenham Spa                          11A   On time
## 20:38  London Paddington                       9B    On time
## 20:40  Abbey Wood                              14    On time
## 20:41  Theale                                  1     On time
## 20:45  London Paddington                       9B    On time
## 20:46  Swansea                                 11    Delayed
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 20:10  Heathrow Airport T3 (Bus)               BUS   On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-06 18:49:15.666771
## Time   To                                      Plat  Expected
## 17:50  London Paddington                       10    18:49
## 18:05  London Paddington                       11    Delayed
## 18:49  London Paddington                       10    19:14
## 18:50  Didcot Parkway                          12B   18:54
## 18:52  Bournemouth                             7B    On time
## 18:53  Cheltenham Spa                          -     Cancelled
## 18:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:56  Taunton                                 9     On time
## 18:59  Abbey Wood                              14    On time
## 19:00  Didcot Parkway                          9     On time
## 19:00  London Paddington                       10    On time
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    Delayed
## 19:08  Ascot                                   6     On time
## 19:10  Theale                                  1     On time
## 19:12  London Paddington                       10    On time
## 19:13  London Paddington                       15A   On time
## 19:13  Swansea                                 9     19:26
## 19:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 19:18  Salisbury                               3     On time
## 19:19  Great Malvern                           9     On time
## 19:23  Didcot Parkway                          13B   On time
## 19:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:25  Bristol Temple Meads                    9     On time
## 19:28  Plymouth                                9     19:56
## 19:29  Abbey Wood                              14    On time
## 19:32  Basingstoke                             2     On time
## 19:32  London Paddington                       8B    On time
## 19:38  Ascot                                   4     On time
## 19:38  Newbury                                 -     Cancelled
## 19:42  London Paddington                       10    On time
## 19:43  London Paddington                       15A   On time
## 19:43  Swansea                                 -     Cancelled
## 19:48  Oxford                                  9B    On time
## 19:50  London Paddington                       10    20:04
## 19:52  Bournemouth                             -     Cancelled
## 19:53  Didcot Parkway                          12B   On time
## 19:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:55  Taunton                                 9     On time
## 19:58  Cheltenham Spa                          8     On time
## 19:59  Abbey Wood                              14    On time
## 20:00  London Paddington                       10A   On time
## 20:03  London Paddington                       11    On time
## 20:05  Basingstoke                             2     On time
## 20:08  Ascot                                   4     On time
## 20:10  Newbury                                 -     Cancelled
## 20:12  London Paddington                       10    On time
## 20:13  London Paddington                       15A   On time
## 20:13  Swansea                                 -     Cancelled
## 20:15  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 20:19  Great Malvern                           9B    On time
## 20:20  London Paddington                       11    On time
## 20:20  Salisbury                               1     On time
## 20:23  Didcot Parkway                          12B   On time
## 20:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:25  Bristol Temple Meads                    9     On time
## 20:27  London Paddington                       10A   On time
## 20:28  Plymouth                                7     On time
## 20:29  Abbey Wood                              14    On time
## 20:35  London Paddington                       11A   On time
## 20:37  Basingstoke                             2     On time
## 20:40  Swindon                                 9B    On time
## 20:41  Ascot                                   4     On time
## 20:43  London Paddington                       15A   On time
## 20:48  London Paddington                       11    Delayed
## 20:48  Oxford                                  9B    On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
```
