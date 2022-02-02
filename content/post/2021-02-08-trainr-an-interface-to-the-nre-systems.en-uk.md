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

## Example (Last rendered on 2022-02-02 16:04)

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
## Reading (RDG) Station Board on 2022-02-02 16:04:25
## Time   From                                    Plat  Expected
## 15:41  London Paddington                       9B    16:23
## 15:44  London Paddington                       -     16:13
## 15:44  Swansea                                 11    16:04
## 15:46  London Paddington                       9     16:17
## 15:51  London Paddington                       9     16:08
## 15:56  London Paddington                       9     16:13
## 15:57  Plymouth                                11    16:05
## 16:07  Didcot Parkway                          15A   On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:10  London Waterloo                         4     On time
## 16:11  London Paddington                       9     16:17
## 16:13  London Paddington                       14    16:25
## 16:16  Cardiff Central                         11    16:32
## 16:18  Basingstoke                             2     On time
## 16:22  London Paddington                       12B   Delayed
## 16:24  Oxford                                  10A   16:26
## 16:25  London Paddington                       9     16:34
## 16:25  Maidenhead                              -     Cancelled
## 16:27  London Paddington                       7     16:36
## 16:29  Cheltenham Spa                          11A   Delayed
## 16:31  Didcot Parkway                          14A   On time
## 16:33  Redhill                                 5     On time
## 16:34  Bedwyn                                  3     On time
## 16:39  Bristol Temple Meads                    10    16:47
## 16:39  Paignton                                11    On time
## 16:41  London Paddington                       9     On time
## 16:41  London Waterloo                         6     On time
## 16:41  Manchester Piccadilly                   7     On time
## 16:43  London Paddington                       14    On time
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       12B   On time
## 16:46  London Paddington                       9B    On time
## 16:50  Basingstoke                             2     On time
## 16:54  Worcester Foregate Street               10    On time
## 16:56  London Paddington                       9     On time
## 16:56  London Waterloo                         4     On time
## 16:58  London Paddington                       14    On time
## 16:59  London Paddington                       7     On time
## 17:01  Penzance                                10    On time
## 17:04  Gatwick Airport                         5     On time
## 17:06  Bournemouth                             13    On time
## 17:06  Didcot Parkway                          15    On time
## 17:09  Bristol Temple Meads                    11    On time
## 17:11  London Paddington                       9     On time
## 17:11  London Waterloo                         6     On time
## 17:13  London Paddington                       14    On time
## 17:22  Bedwyn                                  11    17:27
## 17:22  London Paddington                       12    On time
## 17:24  Oxford                                  10    On time
## 17:25  London Paddington                       8     On time
## 17:26  Basingstoke                             2     On time
## 17:27  London Paddington                       7     On time
## 17:28  London Paddington                       14    Delayed
## 17:29  Cheltenham Spa                          10    On time
## 17:33  Newbury                                 1     On time
## 17:35  Didcot Parkway                          15    On time
## 17:37  London Paddington                       8     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:39  Exeter St Davids                        11    On time
## 17:40  London Waterloo                         4     On time
## 17:41  London Paddington                       9     On time
## 17:41  Manchester Piccadilly                   7     On time
## 17:43  London Paddington                       14    On time
## 17:43  Swansea                                 10    On time
## 17:44  Redhill                                 5     On time
## 17:46  Basingstoke                             2     On time
## 17:54  London Paddington                       12B   On time
## 17:55  London Paddington                       8     On time
## 17:56  Hereford                                10    On time
## 17:58  London Paddington                       9     On time
## 17:58  London Paddington                       14    On time
## 18:01  London Paddington                       -     On time
## 18:02  Gatwick Airport                         -     On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-02 16:04:29
## Time   To                                      Plat  Expected
## 15:43  Cardiff Central                         9B    16:24
## 15:45  London Paddington                       11    16:05
## 15:48  Worcester Foregate Street               9     16:18
## 15:52  Ealing Broadway                         14    Delayed
## 15:53  Cheltenham Spa                          9     16:11
## 15:58  Weston-super-Mare                       9     16:15
## 16:04  London Paddington                       11    16:06
## 16:07  Basingstoke                             2     On time
## 16:12  London Paddington                       10    On time
## 16:12  London Waterloo                         6     On time
## 16:12  Newbury                                 3     On time
## 16:13  Swansea                                 9     16:18
## 16:15  Ealing Broadway                         15A   On time
## 16:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 16:18  London Paddington                       11    16:33
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 4     On time
## 16:22  Ealing Broadway                         14    16:27
## 16:23  London Paddington                       -     Cancelled
## 16:25  Didcot Parkway                          -     Cancelled
## 16:25  Didcot Parkway                          12B   Delayed
## 16:27  Bristol Temple Meads                    9     16:35
## 16:27  London Paddington                       10A   On time
## 16:29  Penzance                                7     16:37
## 16:32  London Paddington                       11A   Delayed
## 16:33  Basingstoke                             2     On time
## 16:33  Ealing Broadway                         13    On time
## 16:37  Newbury                                 8     On time
## 16:38  Ealing Broadway                         14A   On time
## 16:42  London Paddington                       10    16:48
## 16:42  London Waterloo                         4     On time
## 16:43  Swansea                                 9     On time
## 16:45  Bedwyn                                  3     On time
## 16:45  London Paddington                       11    On time
## 16:47  London Paddington                       10    On time
## 16:48  Oxford                                  9B    On time
## 16:50  Didcot Parkway                          12B   On time
## 16:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:52  Bournemouth                             7     On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  London Waterloo                         6     On time
## 16:57  London Paddington                       10    On time
## 16:58  Bristol Temple Meads                    9     On time
## 17:02  Totnes                                  7     On time
## 17:03  Ealing Broadway                         14    On time
## 17:05  London Paddington                       10    On time
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       11    On time
## 17:12  London Waterloo                         4     On time
## 17:13  Ealing Broadway                         15    On time
## 17:13  Swansea                                 9     On time
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 17:20  Redhill                                 5     On time
## 17:22  Ealing Broadway                         14    On time
## 17:24  London Paddington                       11    17:28
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       10    On time
## 17:29  Penzance                                7     On time
## 17:32  London Paddington                       10    On time
## 17:33  Ealing Broadway                         14    Delayed
## 17:34  Basingstoke                             2     On time
## 17:38  Newbury                                 8     On time
## 17:41  London Paddington                       10    On time
## 17:42  Ealing Broadway                         15    On time
## 17:42  London Waterloo                         6     On time
## 17:43  London Paddington                       11    On time
## 17:43  Swansea                                 9     On time
## 17:46  London Paddington                       10    On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:52  Ealing Broadway                         14    On time
## 17:52  Southampton Central                     7     On time
## 17:57  Basingstoke                             2     On time
## 17:57  Taunton                                 8     On time
## 17:58  Didcot Parkway                          12B   On time
## 18:00  Hereford                                9     On time
## 18:00  London Paddington                       10    On time
## 18:03  Plymouth                                -     On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 18:00  Heathrow Central Bus Stn                -     On time
```
