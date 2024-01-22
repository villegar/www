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

## Example (Last rendered on 2024-01-22 10:04)

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
## Reading (RDG) Station Board on 2024-01-22 10:04:24.377888
## Time   From                                    Plat  Expected
## 09:30  Penzance                                11    10:01
## 10:01  London Paddington                       7     On time
## 10:02  Plymouth                                11    10:14
## 10:03  Redhill                                 4     10:06
## 10:06  Swansea                                 10A   On time
## 10:10  Abbey Wood                              -     Cancelled
## 10:10  Bournemouth                             7     On time
## 10:10  Didcot Parkway                          15A   On time
## 10:11  London Paddington                       9     On time
## 10:12  London Waterloo                         -     Cancelled
## 10:13  Newbury                                 11A   On time
## 10:14  Bristol Temple Meads                    10    On time
## 10:14  London Paddington                       12B   10:22
## 10:17  London Paddington                       9     On time
## 10:19  Basingstoke                             2     10:21
## 10:20  Oxford                                  11    On time
## 10:23  London Paddington                       9     On time
## 10:27  London Paddington                       8     On time
## 10:29  Cheltenham Spa                          10    10:44
## 10:30  Gatwick Airport                         4     10:38
## 10:31  London Paddington                       7B    On time
## 10:36  Didcot Parkway                          15A   On time
## 10:38  London Paddington                       9     On time
## 10:38  Newbury                                 1     On time
## 10:40  Abbey Wood                              -     Cancelled
## 10:40  Bristol Temple Meads                    10    On time
## 10:43  London Waterloo                         6     10:50
## 10:45  Carmarthen                              10    On time
## 10:46  London Paddington                       8     On time
## 10:46  Manchester Piccadilly                   7     11:21
## 10:49  London Paddington                       15B   On time
## 10:50  Newbury                                 11A   On time
## 10:53  London Paddington                       8     On time
## 10:55  Basingstoke                             2     On time
## 10:55  London Paddington                       9     On time
## 10:56  Great Malvern                           10    On time
## 10:58  Didcot Parkway                          13A   On time
## 10:58  Penzance                                11    On time
## 10:59  London Paddington                       7     On time
## 11:05  Bristol Temple Meads                    10    On time
## 11:05  Gatwick Airport                         5     On time
## 11:06  Bournemouth                             8     On time
## 11:07  Newcastle                               3     On time
## 11:10  Abbey Wood                              -     Cancelled
## 11:11  London Paddington                       9     On time
## 11:14  London Waterloo                         4     On time
## 11:15  London Paddington                       12B   On time
## 11:17  London Paddington                       9     On time
## 11:18  Cardiff Central                         10    On time
## 11:19  Basingstoke                             2     On time
## 11:22  Oxford                                  11    On time
## 11:23  London Paddington                       9     On time
## 11:26  London Paddington                       7     On time
## 11:28  Gatwick Airport                         5     On time
## 11:30  Didcot Parkway                          15A   On time
## 11:31  Cheltenham Spa                          11    On time
## 11:33  London Paddington                       7B    On time
## 11:36  Newbury                                 1     On time
## 11:38  Plymouth                                11A   On time
## 11:39  London Paddington                       9     On time
## 11:40  Abbey Wood                              -     Cancelled
## 11:40  Bristol Temple Meads                    10    On time
## 11:40  Manchester Piccadilly                   8B    On time
## 11:43  London Waterloo                         6     On time
## 11:45  Swansea                                 11    11:51
## 11:47  London Paddington                       9     On time
## 11:49  Basingstoke                             2     On time
## 11:50  London Paddington                       12B   On time
## 11:53  London Paddington                       9     On time
## 11:55  London Paddington                       8     On time
## 11:57  Gatwick Airport                         5     On time
## 11:57  Great Malvern                           10    On time
## 10:15  Heathrow Airport T3 (Bus)               BUS   On time
## 10:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-22 10:04:26.577489
## Time   To                                      Plat  Expected
## 09:32  London Paddington                       11    10:04
## 09:59  Abbey Wood                              14    Delayed
## 10:03  Paignton                                7     On time
## 10:04  London Paddington                       11    10:15
## 10:07  Basingstoke                             15A   On time
## 10:08  London Paddington                       10A   On time
## 10:09  London Waterloo                         6     On time
## 10:12  London Paddington                       15A   On time
## 10:12  Newbury                                 1     On time
## 10:13  Carmarthen                              9     On time
## 10:14  London Paddington                       11A   On time
## 10:16  London Paddington                       10    On time
## 10:16  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9     On time
## 10:23  Didcot Parkway                          12B   On time
## 10:24  Gatwick Airport                         4     On time
##        via Guildford                           
## 10:25  Bristol Temple Meads                    9     On time
## 10:26  London Paddington                       11    On time
## 10:29  Abbey Wood                              14    On time
## 10:29  Penzance                                8     On time
## 10:33  Basingstoke                             2     On time
## 10:34  London Paddington                       10    10:45
## 10:38  London Paddington                       15A   On time
## 10:39  London Waterloo                         -     Cancelled
## 10:39  Newbury                                 7B    On time
## 10:40  Cardiff Central                         9     On time
## 10:42  London Paddington                       10    On time
## 10:47  London Paddington                       10    On time
## 10:48  Oxford                                  8     On time
## 10:52  Bournemouth                             7     11:22
## 10:53  Didcot Parkway                          15B   On time
## 10:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 10:54  London Paddington                       11A   On time
## 10:55  Bristol Temple Meads                    8     On time
## 10:58  Cheltenham Spa                          9     On time
## 10:59  Abbey Wood                              14    On time
## 10:59  London Paddington                       10    On time
## 11:01  Exeter St Davids                        7     On time
## 11:04  London Paddington                       11    On time
## 11:07  Basingstoke                             2     On time
## 11:07  London Paddington                       10    On time
## 11:09  London Waterloo                         6     On time
## 11:12  London Paddington                       13A   On time
## 11:12  Newbury                                 1     On time
## 11:13  Swansea                                 9     On time
## 11:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Shrub Hill                    9     On time
## 11:20  London Paddington                       10    On time
## 11:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:25  Bristol Temple Meads                    9     On time
## 11:25  Didcot Parkway                          12B   On time
## 11:27  London Paddington                       11    On time
## 11:29  Abbey Wood                              14    On time
## 11:29  Plymouth                                7     On time
## 11:32  Basingstoke                             2     On time
## 11:34  London Paddington                       11    On time
## 11:37  Newbury                                 7B    On time
## 11:39  London Waterloo                         4     On time
## 11:41  Cardiff Central                         9     On time
## 11:41  London Paddington                       15A   On time
## 11:41  London Paddington                       11A   On time
## 11:43  London Paddington                       10    On time
## 11:45  York                                    3     On time
##        via Doncaster                           
## 11:47  London Paddington                       11    11:52
## 11:48  Oxford                                  9     On time
## 11:51  Bournemouth                             8B    On time
## 11:51  Didcot Parkway                          12B   On time
## 11:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:55  Bristol Temple Meads                    9     On time
## 11:58  Cheltenham Spa                          8     On time
## 11:59  Abbey Wood                              14    On time
## 12:00  London Paddington                       10    On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
