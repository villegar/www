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

## Example (Last rendered on 2024-03-24 17:06)

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
## Reading (RDG) Station Board on 2024-03-24 17:06:21.583887
## Time   From                                    Plat  Expected
## 16:58  Plymouth                                11    17:00
## 16:59  London Paddington                       7     17:09
## 17:06  Abbey Wood                              14    On time
## 17:07  London Paddington                       9     On time
## 17:07  Southampton Central                     8B    17:03
## 17:08  Redhill                                 5     17:05
## 17:09  Weston-super-Mare                       10    17:17
## 17:17  Swindon                                 11    17:25
## 17:20  Newbury                                 3     On time
## 17:24  London Paddington                       9     On time
## 17:27  London Paddington                       7     On time
## 17:32  Basingstoke                             2     On time
## 17:34  Ascot                                   4     On time
## 17:35  Didcot Parkway                          12    On time
## 17:36  Abbey Wood                              14    On time
## 17:36  Paignton                                11    On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   7B    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:46  London Paddington                       9     On time
## 17:49  Cardiff Central                         11    On time
## 17:54  London Paddington                       8     On time
## 17:57  Charlbury                               10    On time
## 17:58  Plymouth                                11    On time
## 17:59  London Paddington                       9     On time
## 18:04  Ascot                                   4     On time
## 18:06  Abbey Wood                              14    On time
## 18:06  London Paddington                       9     On time
## 18:06  Southampton Central                     8B    On time
## 18:08  Redhill                                 5     On time
## 18:09  Plymouth                                10    On time
## 18:15  Swindon                                 11    On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:27  London Paddington                       7     On time
## 18:29  Cheltenham Spa                          11    On time
## 18:32  Basingstoke                             2     On time
## 18:34  Ascot                                   4     On time
## 18:35  Didcot Parkway                          13    On time
## 18:36  Abbey Wood                              14    On time
## 18:38  Gatwick Airport                         5     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:40  Manchester Piccadilly                   7     On time
## 18:45  London Paddington                       9     On time
## 18:49  Cardiff Central                         11    On time
## 18:54  London Paddington                       8     On time
## 18:57  Charlbury                               10    On time
## 18:57  London Paddington                       9     On time
## 18:58  Penzance                                11    On time
## 18:59  London Paddington                       7     On time
## 19:04  Ascot                                   4     On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-24 17:06:23.497267
## Time   To                                      Plat  Expected
## 17:01  Plymouth                                7     17:10
## 17:05  London Paddington                       11    On time
## 17:09  Cardiff Central                         9     On time
## 17:12  Salisbury                               2     On time
## 17:13  London Paddington                       10    17:18
## 17:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 17:18  London Paddington                       11    17:26
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:24  Ascot                                   4     On time
## 17:25  Didcot Parkway                          12    On time
## 17:26  Bristol Temple Meads                    9     On time
## 17:28  Penzance                                7     On time
## 17:32  Abbey Wood                              14    On time
## 17:37  Basingstoke                             2     On time
## 17:39  London Paddington                       11    On time
## 17:45  Newbury                                 3     On time
## 17:46  London Paddington                       10    On time
## 17:46  Swindon                                 9     On time
## 17:51  Redhill                                 5     On time
## 17:52  Southampton Central                     7B    On time
## 17:53  London Paddington                       11    On time
## 17:54  Ascot                                   4     On time
## 17:56  Charlbury                               8     On time
## 17:58  Cheltenham Spa                          7     On time
## 17:59  London Paddington                       11    On time
## 18:02  Abbey Wood                              14    On time
## 18:03  Weston-super-Mare                       9     On time
## 18:05  London Paddington                       10    On time
## 18:10  Cardiff Central                         9     On time
## 18:14  London Paddington                       10    On time
## 18:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 18:17  London Paddington                       11    On time
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:24  Ascot                                   4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:28  Penzance                                7     On time
## 18:32  Abbey Wood                              14    On time
## 18:34  London Paddington                       11    On time
## 18:37  Basingstoke                             2     On time
## 18:43  Newbury                                 1     On time
## 18:46  London Paddington                       10    On time
## 18:46  Swindon                                 9     On time
## 18:51  Redhill                                 5     On time
## 18:52  Southampton Central                     7     On time
## 18:53  London Paddington                       11    On time
## 18:54  Ascot                                   4     On time
## 18:55  Charlbury                               8     On time
## 18:59  London Paddington                       10    On time
## 19:00  Weston-super-Mare                       9     On time
## 19:01  Plymouth                                7     On time
## 19:02  Abbey Wood                              14    On time
## 19:05  London Paddington                       11    On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
