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

## Example (Last rendered on 2024-01-06 21:04)

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
## Reading (RDG) Station Board on 2024-01-06 21:04:21.782211
## Time   From                                    Plat  Expected
## 20:46  Swansea                                 11A   Delayed
## 20:58  Great Malvern                           10    21:02
## 21:04  Didcot Parkway                          15A   21:00
## 21:06  Bournemouth                             13B   21:09
## 21:10  Abbey Wood                              14    On time
## 21:10  Bristol Temple Meads                    10    21:12
## 21:11  London Paddington                       9     On time
## 21:14  London Paddington                       12B   On time
## 21:15  London Paddington                       8B    21:17
## 21:17  Penzance                                11    21:19
## 21:20  Ascot                                   6     On time
## 21:22  Basingstoke                             2     On time
## 21:24  Oxford                                  10A   On time
## 21:26  London Paddington                       13B   On time
## 21:31  Didcot Parkway                          15A   On time
## 21:33  Cheltenham Spa                          10A   On time
## 21:33  Gatwick Airport                         14B   On time
## 21:40  Abbey Wood                              14    On time
## 21:40  Manchester Piccadilly                   7B    21:57
## 21:40  Theale                                  1     On time
## 21:44  London Paddington                       13A   On time
## 21:45  London Paddington                       9B    On time
## 21:49  Basingstoke                             2     On time
## 21:49  Swansea                                 10    22:04
## 21:50  Ascot                                   5     On time
## 21:53  Gatwick Airport                         6     On time
## 21:53  London Paddington                       9     On time
## 21:57  Salisbury                               3     On time
## 21:58  Worcester Foregate Street               10A   On time
## 21:59  Didcot Parkway                          13A   On time
## 22:10  Abbey Wood                              14    On time
## 22:13  Taunton                                 10    On time
## 22:14  London Paddington                       12B   On time
## 22:16  London Paddington                       8B    On time
## 22:18  Basingstoke                             2     On time
## 22:20  Ascot                                   4     On time
## 22:22  Theale                                  13A   On time
## 22:25  London Paddington                       9     On time
## 22:27  Didcot Parkway                          15    On time
## 22:29  Oxford                                  11A   On time
## 22:33  Gatwick Airport                         14    On time
## 22:39  Manchester Piccadilly                   7B    On time
## 22:40  Abbey Wood                              14    On time
## 22:41  Cheltenham Spa                          -     Cancelled
## 22:44  London Paddington                       12B   On time
## 22:50  Ascot                                   5     On time
## 22:50  Basingstoke                             13B   On time
## 22:54  London Paddington                       9     On time
## 22:55  Gatwick Airport                         15B   On time
## 21:10  Heathrow Airport T3 (Bus)               BUS   On time
## 21:40  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Heathrow Airport T3 (Bus)               BUS   On time
## 22:40  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-06 21:04:23.694975
## Time   To                                      Plat  Expected
## 20:48  London Paddington                       11A   Delayed
## 21:00  London Paddington                       10    21:04
## 21:05  Basingstoke                             7B    On time
## 21:08  Ascot                                   6     On time
## 21:09  Theale                                  1     On time
## 21:12  London Paddington                       10    21:13
## 21:13  London Paddington                       15A   On time
## 21:13  Swansea                                 9     21:33
## 21:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 21:15  Salisbury                               3     On time
## 21:18  London Paddington                       11    21:23
## 21:19  Oxford                                  8B    On time
## 21:23  Didcot Parkway                          12B   On time
## 21:27  London Paddington                       10A   On time
## 21:29  Abbey Wood                              14    On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       10A   On time
## 21:38  Ascot                                   6     On time
## 21:43  London Paddington                       15A   On time
## 21:47  Oxford                                  9B    On time
## 21:50  London Paddington                       10    22:05
## 21:52  Bournemouth                             7B    21:58
## 21:55  Bristol Temple Meads                    9     On time
## 21:59  Abbey Wood                              14    On time
## 22:00  London Paddington                       10A   On time
## 22:05  Basingstoke                             2     On time
## 22:08  Ascot                                   5     On time
## 22:10  Theale                                  1     On time
## 22:13  London Paddington                       13A   On time
## 22:14  London Paddington                       10    On time
## 22:18  Worcester Shrub Hill                    8B    On time
## 22:27  Bristol Parkway                         9     On time
## 22:29  Abbey Wood                              14    On time
## 22:30  Didcot Parkway                          12B   On time
## 22:30  Salisbury                               3     On time
## 22:33  Shalford                                6     On time
## 22:34  London Paddington                       11A   On time
## 22:35  Basingstoke                             2     On time
## 22:38  Ascot                                   4     On time
## 22:42  London Paddington                       -     Cancelled
## 22:52  Southampton Central                     7B    On time
## 22:56  Bristol Temple Meads                    9     On time
## 22:57  Abbey Wood                              14    On time
## 23:01  Didcot Parkway                          12B   On time
## 21:05  Heathrow Airport T3 (Bus)               BUS   On time
## 22:05  Heathrow Airport T3 (Bus)               BUS   On time
```
