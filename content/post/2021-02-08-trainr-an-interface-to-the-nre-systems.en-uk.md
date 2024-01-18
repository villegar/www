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

## Example (Last rendered on 2024-01-18 07:04)

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
## Reading (RDG) Station Board on 2024-01-18 07:04:47.919243
## Time   From                                    Plat  Expected
## 06:48  London Waterloo                         6     07:04
## 06:53  Worcester Shrub Hill                    10A   07:13
## 06:59  Bristol Temple Meads                    11A   07:04
## 07:00  London Paddington                       14B   On time
## 07:01  Newbury                                 -     Cancelled
## 07:04  Bristol Temple Meads                    11    07:24
## 07:08  Southampton Central                     12B   On time
## 07:09  Oxford                                  10A   Delayed
## 07:10  London Paddington                       14    On time
## 07:11  London Paddington                       9B    On time
## 07:11  London Waterloo                         -     Cancelled
## 07:12  Didcot Parkway                          15    On time
## 07:13  London Paddington                       8     On time
## 07:18  London Paddington                       12B   On time
## 07:18  Swansea                                 10A   07:24
## 07:21  Newbury                                 -     Cancelled
## 07:23  London Paddington                       9     On time
## 07:25  Abbey Wood                              13    On time
## 07:26  Cheltenham Spa                          10    On time
## 07:26  London Paddington                       7     On time
## 07:26  Oxford                                  8A    Delayed
## 07:28  Basingstoke                             2     On time
## 07:31  Frome                                   -     Cancelled
## 07:33  Gatwick Airport                         5     On time
## 07:33  London Paddington                       7B    On time
## 07:38  Bristol Temple Meads                    11    On time
## 07:38  London Paddington                       9     On time
## 07:43  Didcot Parkway                          15    On time
## 07:44  Abbey Wood                              14    On time
## 07:44  London Paddington                       8B    On time
## 07:45  Birmingham New Street                   7B    On time
## 07:46  Basingstoke                             2     On time
## 07:46  London Waterloo                         6     On time
## 07:47  London Paddington                       12B   On time
## 07:49  Swansea                                 10    On time
## 07:51  London Paddington                       9     On time
## 07:51  Newbury                                 -     Cancelled
## 07:54  Hereford                                11    On time
## 07:54  London Paddington                       8     On time
## 07:55  Abbey Wood                              13    On time
## 08:02  Newton Abbot                            11    Delayed
## 08:06  Basingstoke                             2     On time
## 08:09  Bournemouth                             8B    On time
## 08:10  Didcot Parkway                          10    On time
## 08:10  Didcot Parkway                          15    On time
## 08:11  London Paddington                       9     On time
## 08:11  London Waterloo                         4     On time
## 08:12  Abbey Wood                              14    On time
## 08:14  Worcester Shrub Hill                    11    On time
## 08:16  London Paddington                       12B   On time
## 08:16  London Paddington                       9     On time
## 08:16  Redhill                                 6     08:19
## 08:18  Swansea                                 10    On time
## 08:22  London Paddington                       9     On time
## 08:22  Newbury                                 1     On time
## 08:25  Abbey Wood                              13    On time
## 08:26  Cheltenham Spa                          10    On time
## 08:26  London Paddington                       7     08:32
## 08:32  London Paddington                       -     Cancelled
## 08:32  Redhill                                 5     Delayed
## 08:34  Exeter St Davids                        11    08:39
## 08:39  Weston-super-Mare                       11    On time
## 08:41  Basingstoke                             2     On time
## 08:41  London Paddington                       9     On time
## 08:42  Abbey Wood                              14    On time
## 08:43  London Waterloo                         6     On time
## 08:44  Didcot Parkway                          15    On time
## 08:44  London Paddington                       8     On time
## 08:45  Manchester Piccadilly                   7B    On time
## 08:49  London Paddington                       12B   On time
## 08:53  London Paddington                       9     On time
## 08:55  London Paddington                       8     On time
## 08:55  Totnes                                  11    On time
## 08:57  Redhill                                 5     On time
## 08:58  Abbey Wood                              13    On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
## 07:45  Heathrow Airport T3 (Bus)               BUS   On time
## 08:15  Heathrow Airport T3 (Bus)               BUS   On time
## 08:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-18 07:04:51.620319
## Time   To                                      Plat  Expected
## 06:45  Newcastle                               7B    Delayed
##        via Doncaster                           
## 06:56  London Paddington                       10A   07:14
## 07:01  Didcot Parkway                          14B   07:03
## 07:02  London Paddington                       11A   07:05
## 07:07  London Paddington                       11    07:25
## 07:09  London Waterloo                         6     On time
## 07:10  Newbury                                 1     On time
## 07:12  London Paddington                       10A   Delayed
## 07:13  Carmarthen                              9B    On time
## 07:14  Abbey Wood                              12    On time
## 07:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 07:18  Great Malvern                           8     On time
## 07:18  London Paddington                       15    On time
## 07:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:20  London Paddington                       10A   07:25
## 07:24  Abbey Wood                              14    On time
## 07:24  London Paddington                       -     Cancelled
## 07:25  Bristol Temple Meads                    9     On time
## 07:26  Didcot Parkway                          12B   On time
## 07:30  Paignton                                7     On time
## 07:31  London Paddington                       10    On time
## 07:34  London Paddington                       -     Cancelled
## 07:35  Newbury                                 7B    On time
## 07:38  Basingstoke                             2     On time
## 07:38  London Paddington                       8A    Delayed
## 07:39  Cardiff Central                         9     On time
## 07:39  London Paddington                       14A   On time
## 07:39  London Waterloo                         -     Cancelled
## 07:41  London Paddington                       11    On time
## 07:45  Abbey Wood                              13    On time
## 07:49  Didcot Parkway                          12B   On time
## 07:49  London Paddington                       15    On time
## 07:49  Oxford                                  8B    On time
## 07:51  London Paddington                       10    On time
## 07:52  Bournemouth                             7B    On time
## 07:52  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:53  Bristol Temple Meads                    9     On time
## 07:54  Abbey Wood                              14    On time
## 07:56  Cheltenham Spa                          8     On time
## 07:56  London Paddington                       11    On time
## 08:00  Basingstoke                             2     On time
## 08:03  Newbury                                 1     On time
## 08:09  London Waterloo                         6     On time
## 08:10  London Paddington                       11    Delayed
## 08:13  Abbey Wood                              13    On time
## 08:13  London Paddington                       10    On time
## 08:13  Swansea                                 9     On time
## 08:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       15    On time
## 08:18  Great Malvern                           9     On time
## 08:18  London Paddington                       11    On time
## 08:20  London Paddington                       10    On time
## 08:23  Basingstoke                             2     On time
## 08:23  Didcot Parkway                          12B   On time
## 08:23  Gatwick Airport                         6     On time
##        via Guildford                           
## 08:24  Abbey Wood                              14    On time
## 08:25  Bristol Temple Meads                    9     On time
## 08:29  London Paddington                       10    On time
## 08:29  Penzance                                7     08:33
## 08:36  London Paddington                       11    08:40
## 08:36  Newbury                                 7B    On time
## 08:39  London Waterloo                         4     On time
## 08:41  London Paddington                       11    On time
## 08:43  Cardiff Central                         9     On time
## 08:45  Abbey Wood                              13    On time
## 08:46  Newbury                                 12A   On time
## 08:47  Oxford                                  8     On time
## 08:50  London Paddington                       15    On time
## 08:53  Bournemouth                             7B    On time
## 08:54  Didcot Parkway                          12B   On time
## 08:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:55  Weston-super-Mare                       9     On time
## 08:57  London Paddington                       11    On time
## 08:58  Abbey Wood                              14    On time
## 08:58  Cheltenham Spa                          8     On time
## 08:59  Basingstoke                             2     On time
## 07:25  Heathrow Airport T3 (Bus)               BUS   On time
## 07:55  Heathrow Airport T3 (Bus)               BUS   On time
## 08:25  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
