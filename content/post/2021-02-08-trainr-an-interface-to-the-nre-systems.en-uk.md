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

## Example (Last rendered on 2024-04-13 11:06)

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
## Reading (RDG) Station Board on 2024-04-13 11:06:23.078566
## Time   From                                    Plat  Expected
## 11:46  Swansea                                 10A   Delayed
## 11:59  Penzance                                11    12:09
## 12:03  Didcot Parkway                          15A   On time
## 12:10  Abbey Wood                              14    On time
## 12:10  Bristol Temple Meads                    10    12:23
## 12:11  London Waterloo                         5     On time
## 12:13  London Paddington                       8     12:18
## 12:14  London Paddington                       12B   On time
## 12:19  Basingstoke                             2     On time
## 12:19  Swindon                                 11A   12:24
## 12:23  London Paddington                       9     On time
## 12:23  Oxford                                  10    On time
## 12:26  London Paddington                       7     On time
## 12:28  Guildford                               5     On time
## 12:31  London Paddington                       8B    On time
## 12:31  Newbury                                 11A   On time
## 12:34  Cheltenham Spa                          10A   On time
## 12:37  Didcot Parkway                          15    On time
## 12:38  London Paddington                       9     On time
## 12:40  Abbey Wood                              14    On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:40  Manchester Piccadilly                   7     On time
## 12:41  Newbury                                 1     On time
## 12:43  London Waterloo                         6     On time
## 12:44  London Paddington                       12B   On time
## 12:45  London Paddington                       9B    On time
## 12:46  Carmarthen                              10A   On time
## 12:49  Basingstoke                             2     On time
## 12:53  London Paddington                       9     On time
## 12:55  London Paddington                       -     Cancelled
## 12:58  London Paddington                       7     On time
## 12:59  Penzance                                11    13:07
## 13:00  Great Malvern                           10A   On time
## 13:02  Didcot Parkway                          15    On time
## 13:06  Southampton Central                     13B   On time
## 13:10  Abbey Wood                              14    On time
## 13:10  Bristol Temple Meads                    10    13:12
## 13:11  London Paddington                       8     On time
## 13:11  London Waterloo                         4     13:23
## 13:14  London Paddington                       12    On time
## 13:16  London Paddington                       9B    On time
## 13:19  Basingstoke                             2     On time
## 13:19  Swindon                                 10    On time
## 13:24  London Paddington                       9     On time
## 13:24  Oxford                                  10    On time
## 13:26  London Paddington                       7     On time
## 13:28  Guildford                               5     On time
## 13:30  London Paddington                       8B    On time
## 13:31  Newbury                                 11    On time
## 13:32  Didcot Parkway                          15    On time
## 13:34  Cheltenham Spa                          10A   On time
## 13:40  Abbey Wood                              14    On time
## 13:40  London Paddington                       9     On time
## 13:41  Manchester Piccadilly                   7     On time
## 13:41  Newbury                                 1     On time
## 13:41  Taunton                                 10    On time
## 13:44  London Paddington                       13    On time
## 13:45  Exeter St Davids                        11A   On time
## 13:45  London Paddington                       9     On time
## 13:46  London Waterloo                         6     On time
## 13:46  Swansea                                 10    On time
## 13:50  Basingstoke                             2     On time
## 13:53  London Paddington                       9     On time
## 13:55  London Paddington                       8B    On time
## 13:58  Great Malvern                           10    On time
## 13:59  Penzance                                11    On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 13:15  Heathrow Airport T3 (Bus)               BUS   On time
## 13:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-13 11:06:26.868917
## Time   To                                      Plat  Expected
## 11:50  London Paddington                       -     Cancelled
## 12:05  London Paddington                       11    12:10
## 12:07  Basingstoke                             2     On time
## 12:09  London Waterloo                         6     On time
## 12:12  London Paddington                       10    12:24
## 12:12  Newbury                                 1     On time
## 12:13  London Paddington                       15A   On time
## 12:13  Swansea                                 9     On time
## 12:14  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Hereford                                8     On time
## 12:20  Didcot Parkway                          12B   On time
## 12:20  London Paddington                       11A   12:25
## 12:24  Guildford                               5     On time
## 12:25  Bristol Temple Meads                    9     On time
## 12:27  London Paddington                       10    On time
## 12:29  Abbey Wood                              14    On time
## 12:30  Penzance                                7     On time
## 12:32  London Paddington                       11A   On time
## 12:33  Newbury                                 8B    On time
## 12:35  London Paddington                       10A   On time
## 12:37  Basingstoke                             2     On time
## 12:39  London Waterloo                         5     On time
## 12:40  Cardiff Central                         9     On time
## 12:42  London Paddington                       10    On time
## 12:43  London Paddington                       15    On time
## 12:48  Oxford                                  9B    On time
## 12:50  London Paddington                       10A   On time
## 12:52  Southampton Central                     7     On time
## 12:53  Didcot Parkway                          12B   On time
## 12:55  Weston-super-Mare                       9     On time
## 12:58  Cheltenham Spa                          8B    On time
## 12:59  Abbey Wood                              14    On time
## 13:01  Exeter St Davids                        7     On time
## 13:01  London Paddington                       10A   On time
## 13:05  London Paddington                       11    13:08
## 13:07  Basingstoke                             2     On time
## 13:09  London Waterloo                         6     On time
## 13:12  London Paddington                       10    13:12
## 13:12  Newbury                                 1     On time
## 13:13  Carmarthen                              8     On time
## 13:13  London Paddington                       15    On time
## 13:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 13:19  Worcester Foregate Street               9B    On time
## 13:21  London Paddington                       10    On time
## 13:23  Didcot Parkway                          12    On time
## 13:24  Guildford                               5     On time
## 13:25  Bristol Temple Meads                    9     On time
## 13:28  London Paddington                       10    On time
## 13:29  Abbey Wood                              14    On time
## 13:30  Penzance                                7     On time
## 13:32  London Paddington                       11    On time
## 13:33  Newbury                                 8B    On time
## 13:35  London Paddington                       10A   On time
## 13:37  Basingstoke                             2     On time
## 13:39  London Waterloo                         4     On time
## 13:42  London Paddington                       10    On time
## 13:42  Swindon                                 9     On time
## 13:43  London Paddington                       15    On time
## 13:46  London Paddington                       11A   On time
## 13:48  Oxford                                  9     On time
## 13:49  London Paddington                       10    On time
## 13:52  Didcot Parkway                          13    On time
## 13:55  Weston-super-Mare                       9     On time
## 13:58  Cheltenham Spa                          8B    On time
## 13:59  Abbey Wood                              14    On time
## 14:00  London Paddington                       10    On time
## 14:05  London Paddington                       11    On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
