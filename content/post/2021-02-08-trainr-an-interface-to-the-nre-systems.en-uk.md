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

## Example (Last rendered on 2024-01-14 09:04)

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
## Reading (RDG) Station Board on 2024-01-14 09:04:01.873231
## Time   From                                    Plat  Expected
## 08:32  London Paddington                       8     09:04
## 08:41  London Paddington                       10    09:07
## 08:42  Didcot Parkway                          -     09:04
## 08:57  London Paddington                       8     09:06
## 09:02  Ascot                                   4     On time
## 09:06  Bristol Temple Meads                    11    09:26
## 09:10  London Paddington                       -     Cancelled
## 09:12  London Paddington                       7B    09:17
## 09:15  London Paddington                       8     Delayed
## 09:19  London Paddington                       7     09:26
## 09:22  Newbury                                 1     On time
## 09:32  London Paddington                       7     Delayed
## 09:33  Ascot                                   4     On time
## 09:37  London Paddington                       9     09:43
## 09:39  Oxford                                  10A   On time
## 09:40  Gatwick Airport                         7B    On time
## 09:41  Didcot Parkway                          -     Cancelled
## 09:50  London Paddington                       8B    On time
## 09:58  Southampton Central                     8B    On time
## 10:00  London Paddington                       7B    On time
## 10:03  Ascot                                   4     On time
## 10:10  London Paddington                       10    On time
## 10:10  Redhill                                 -     Cancelled
## 10:11  Worcester Foregate Street               11A   On time
## 10:14  London Paddington                       8     On time
## 10:18  London Paddington                       7     On time
## 10:20  Bedwyn                                  3     10:28
## 10:22  Weston-super-Mare                       11    On time
## 10:28  London Paddington                       8     On time
## 10:31  London Paddington                       7     On time
## 10:33  Ascot                                   4     On time
## 10:36  Didcot Parkway                          8     On time
## 10:36  Exeter St Davids                        11    On time
## 10:38  Gatwick Airport                         6     On time
## 10:40  Bristol Parkway                         10    On time
## 10:43  London Paddington                       9     On time
## 10:46  London Paddington                       7     On time
## 10:48  Birmingham New Street                   8     On time
## 10:59  London Paddington                       -     Cancelled
## 11:03  Ascot                                   4     On time
## 09:15  Chippenham                              BUS   On time
## 09:15  Heathrow Airport T3 (Bus)               BUS   On time
## 09:45  Heathrow Airport T3 (Bus)               BUS   On time
## 09:45  Swindon                                 BUS   On time
## 09:55  Basingstoke                             BUS   On time
## 10:15  Heathrow Airport T3 (Bus)               BUS   On time
## 10:15  Swindon                                 BUS   On time
## 10:16  Bramley (Hampshire)                     BUS   On time
## 10:45  Heathrow Airport T3 (Bus)               BUS   On time
## 10:45  Swindon                                 BUS   On time
## 10:55  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-14 09:04:03.45391
## Time   To                                      Plat  Expected
## 08:34  Exeter St Davids                        8     09:05
##        via Bristol                             
## 08:43  London Paddington                       -     09:05
## 08:53  London Paddington                       -     09:10
## 09:07  Manchester Piccadilly                   3     On time
##        via Coventry & Wilmslow                 
## 09:08  Carmarthen                              8     09:18
## 09:10  London Paddington                       11    09:27
## 09:14  Great Malvern                           7B    09:18
## 09:18  Gatwick Airport                         -     On time
##        via Guildford                           
## 09:20  Didcot Parkway                          7     09:27
## 09:20  Penzance                                8     Delayed
## 09:23  Abbey Wood                              -     Cancelled
## 09:24  Ascot                                   4     On time
## 09:34  Bristol Temple Meads                    7     Delayed
## 09:40  London Paddington                       10A   On time
## 09:43  Bedwyn                                  3     On time
## 09:43  London Paddington                       8     On time
## 09:52  Oxford                                  8B    On time
## 09:53  Ascot                                   4     On time
## 10:01  Abbey Wood                              9     On time
## 10:01  Redhill                                 6     On time
## 10:07  Manchester Piccadilly                   8B    On time
##        via Coventry & Wilmslow                 
## 10:12  London Paddington                       11A   On time
## 10:14  Hereford                                7B    On time
## 10:17  Swansea                                 8     On time
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:24  Ascot                                   4     On time
## 10:25  Didcot Parkway                          7     On time
## 10:28  London Paddington                       11    On time
## 10:29  Penzance                                8     On time
## 10:31  Abbey Wood                              10    On time
## 10:34  Weston-super-Mare                       7     On time
## 10:36  London Paddington                       8     On time
## 10:42  London Paddington                       11    On time
## 10:43  Newbury                                 1     On time
## 10:45  London Paddington                       10    On time
## 10:49  Bournemouth                             8     On time
## 10:52  Oxford                                  7     On time
## 10:53  Ascot                                   4     On time
## 10:59  Abbey Wood                              9     On time
## 11:01  Paignton                                -     Cancelled
## 11:01  Redhill                                 6     On time
## 09:05  Swindon                                 BUS   On time
## 09:07  Basingstoke                             BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:40  Swindon                                 BUS   On time
## 09:52  Winchester                              BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:05  Swindon                                 BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:37  Bramley (Hampshire)                     BUS   On time
## 10:40  Swindon                                 BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Winchester                              BUS   On time
```
