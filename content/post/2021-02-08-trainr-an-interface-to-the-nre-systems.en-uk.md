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

## Example (Last rendered on 2024-01-14 19:03)

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
## Reading (RDG) Station Board on 2024-01-14 19:04:00.012542
## Time   From                                    Plat  Expected
## 18:50  Carmarthen                              11    18:53
## 18:58  Penzance                                12    19:05
## 18:59  Great Malvern                           10A   19:04
## 19:00  London Paddington                       9     On time
## 19:02  Ascot                                   4     On time
## 19:03  Bournemouth                             8B    On time
## 19:05  Abbey Wood                              14    On time
## 19:10  Redhill                                 5     19:12
## 19:15  London Paddington                       13A   On time
## 19:19  Bedwyn                                  -     Cancelled
## 19:22  Oxford                                  -     Cancelled
## 19:26  Taunton                                 10    On time
## 19:28  London Paddington                       7     On time
## 19:31  London Paddington                       8     On time
## 19:32  Ascot                                   6     On time
## 19:35  Abbey Wood                              14    On time
## 19:35  Didcot Parkway                          15    On time
## 19:38  Gatwick Airport                         5     On time
## 19:40  Manchester Piccadilly                   3     On time
## 19:40  Paignton                                11    19:42
## 19:45  Swansea                                 10    On time
## 19:46  London Paddington                       9B    On time
## 19:57  Penzance                                -     Cancelled
## 19:59  Hereford                                10A   On time
## 20:00  London Paddington                       9B    On time
## 20:02  Ascot                                   4     On time
## 20:05  Abbey Wood                              14    On time
## 20:05  Exeter St Davids                        -     20:08
## 20:10  Redhill                                 15    On time
## 20:18  London Paddington                       13    On time
## 20:18  Newbury                                 1     On time
## 20:22  Oxford                                  10A   On time
## 20:23  Exeter St Davids                        11    On time
## 20:28  London Paddington                       7     On time
## 20:32  Ascot                                   6     On time
## 20:34  London Paddington                       9B    On time
## 20:35  Abbey Wood                              14    On time
## 20:35  Didcot Parkway                          15    On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:42  Carmarthen                              10    On time
## 20:43  London Paddington                       7     On time
## 21:02  Ascot                                   4     On time
## 19:15  Swindon                                 BUS   On time
## 19:16  Bramley (Hampshire)                     BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:45  Swindon                                 BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Winchester                              BUS   On time
## 20:10  Heathrow Airport T3 (Bus)               BUS   On time
## 20:15  Swindon                                 BUS   On time
## 20:16  Bramley (Hampshire)                     BUS   On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
## 20:45  Swindon                                 BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-14 19:04:01.701545
## Time   To                                      Plat  Expected
## 19:05  London Paddington                       11    On time
## 19:08  London Paddington                       12    On time
## 19:12  Manchester Piccadilly                   8B    On time
##        via Coventry & Wilmslow                 
## 19:14  Hereford                                9     On time
## 19:15  London Paddington                       10A   On time
## 19:20  Swansea                                 7     On time
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:24  Ascot                                   4     On time
## 19:24  London Paddington                       -     Cancelled
## 19:25  Didcot Parkway                          13A   On time
## 19:29  Abbey Wood                              14    On time
## 19:29  Plymouth                                7     On time
## 19:34  Bristol Temple Meads                    8     On time
## 19:36  London Paddington                       10    On time
## 19:37  London Paddington                       15    On time
## 19:42  London Paddington                       11    19:42
## 19:43  Bedwyn                                  1     On time
## 19:46  London Paddington                       10    On time
## 19:49  Oxford                                  9B    On time
## 19:53  Ascot                                   6     On time
## 19:59  Abbey Wood                              14    On time
## 20:05  London Paddington                       -     Cancelled
## 20:05  London Paddington                       -     20:08
## 20:08  London Paddington                       10A   On time
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Great Malvern                           9B    On time
## 20:14  Manchester Piccadilly                   3     On time
##        via Coventry & Wilmslow                 
## 20:20  Swansea                                 8     On time
## 20:24  Ascot                                   4     On time
## 20:24  London Paddington                       10A   On time
## 20:28  Didcot Parkway                          13    On time
## 20:29  Abbey Wood                              14    On time
## 20:29  Plymouth                                7     On time
## 20:35  London Paddington                       11    On time
## 20:35  Oxford                                  9B    On time
## 20:37  London Paddington                       15    On time
## 20:45  London Paddington                       10    On time
## 20:45  Weston-super-Mare                       7     On time
## 20:48  Newbury                                 1     On time
## 20:49  Southampton Central                     8     On time
## 20:53  Ascot                                   6     On time
## 20:59  Abbey Wood                              14    On time
## 19:05  Swindon                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:37  Bramley (Hampshire)                     BUS   On time
## 19:40  Swindon                                 BUS   On time
## 19:52  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:05  Swindon                                 BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:37  Bramley (Hampshire)                     BUS   On time
## 20:45  Swindon                                 BUS   On time
## 20:52  Winchester                              BUS   On time
```
