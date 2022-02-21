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

## Example (Last rendered on 2022-02-21 16:04)

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
## Reading (RDG) Station Board on 2022-02-21 16:04:09
## Time   From                                    Plat  Expected
## 14:45  Swansea                                 10    16:02
## 15:44  Swansea                                 8A    16:05
## 15:57  Plymouth                                -     Cancelled
## 16:04  Exeter St Davids                        11    16:32
## 16:07  Didcot Parkway                          15    15:59
## 16:09  Bristol Temple Meads                    10    16:20
## 16:11  London Paddington                       9     16:17
## 16:11  London Waterloo                         4     16:41
## 16:13  London Paddington                       14    On time
## 16:16  Cardiff Central                         -     Cancelled
## 16:18  Basingstoke                             2     On time
## 16:22  Newbury                                 -     Cancelled
## 16:24  Oxford                                  -     Cancelled
## 16:25  London Paddington                       -     Cancelled
## 16:27  London Paddington                       7     On time
## 16:29  Cheltenham Spa                          -     Cancelled
## 16:31  Didcot Parkway                          14    On time
## 16:33  London Paddington                       -     Cancelled
## 16:33  Redhill                                 5     On time
## 16:34  Bedwyn                                  -     Cancelled
## 16:35  Bedwyn                                  -     16:43
## 16:39  Bristol Temple Meads                    -     Cancelled
## 16:39  Paignton                                -     Cancelled
## 16:41  London Paddington                       -     Cancelled
## 16:41  London Waterloo                         6     16:52
## 16:41  Manchester Piccadilly                   7     On time
## 16:43  London Paddington                       14    On time
## 16:45  Swansea                                 10    16:53
## 16:46  London Paddington                       -     Cancelled
## 16:50  Basingstoke                             2     On time
## 16:54  Worcester Foregate Street               -     Cancelled
## 16:56  London Paddington                       9     On time
## 16:58  London Paddington                       14    On time
## 16:59  London Paddington                       -     Cancelled
## 17:01  Penzance                                -     Cancelled
## 17:03  Gatwick Airport                         -     Cancelled
## 17:05  Exeter St Davids                        -     17:17
## 17:06  Bournemouth                             13    On time
## 17:06  Didcot Parkway                          15    On time
## 17:09  Bristol Temple Meads                    11    On time
## 17:11  London Paddington                       9     On time
## 17:13  London Paddington                       14    On time
## 17:16  London Waterloo                         6     On time
## 17:22  Bedwyn                                  -     Cancelled
## 17:24  Oxford                                  -     Cancelled
## 17:25  London Paddington                       -     Cancelled
## 17:26  Basingstoke                             2     On time
## 17:27  London Paddington                       7     On time
## 17:29  Cheltenham Spa                          -     Cancelled
## 17:33  Newbury                                 -     Cancelled
## 17:35  Bedwyn                                  -     On time
## 17:35  Didcot Parkway                          15    On time
## 17:37  London Paddington                       -     Cancelled
## 17:38  Bristol Temple Meads                    -     Cancelled
## 17:39  Exeter St Davids                        -     Cancelled
## 17:41  London Paddington                       9     On time
## 17:41  Manchester Piccadilly                   7     On time
## 17:42  London Waterloo                         4     17:45
## 17:43  London Paddington                       14    On time
## 17:43  Swansea                                 10    On time
## 17:44  Redhill                                 5     On time
## 17:46  Basingstoke                             2     On time
## 17:55  London Paddington                       8     On time
## 17:56  Hereford                                -     Cancelled
## 17:58  Exeter St Davids                        -     On time
## 17:58  London Paddington                       -     Cancelled
## 18:01  London Paddington                       -     Cancelled
## 18:02  Gatwick Airport                         -     Cancelled
## 18:03  Didcot Parkway                          15    On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-21 16:04:13
## Time   To                                      Plat  Expected
## 14:48  London Paddington                       10    16:04
## 15:45  London Paddington                       8A    16:06
## 16:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 16:04  London Paddington                       -     Cancelled
## 16:04  London Paddington                       11    16:32
## 16:07  Basingstoke                             2     On time
## 16:12  Bedwyn                                  3     On time
## 16:12  London Paddington                       10    16:21
## 16:12  London Waterloo                         -     Cancelled
## 16:12  Newbury                                 -     Cancelled
## 16:13  Swansea                                 9     16:18
## 16:16  Manchester Piccadilly                   12    On time
## 16:18  London Paddington                       -     Cancelled
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 5     On time
## 16:23  London Paddington                       -     Cancelled
## 16:25  Didcot Parkway                          15    On time
## 16:27  Bristol Temple Meads                    -     Cancelled
## 16:27  London Paddington                       -     Cancelled
## 16:29  Exeter St Davids                        7     On time
## 16:32  London Paddington                       -     Cancelled
## 16:33  Basingstoke                             2     On time
## 16:33  Ealing Broadway                         13    On time
## 16:37  Newbury                                 -     Cancelled
## 16:41  London Waterloo                         4     16:44
## 16:42  London Paddington                       -     Cancelled
## 16:43  Swansea                                 -     Cancelled
## 16:45  Bedwyn                                  -     Cancelled
## 16:45  London Paddington                       -     Cancelled
## 16:47  London Paddington                       10    16:54
## 16:48  Oxford                                  -     Cancelled
## 16:50  Didcot Parkway                          12    On time
## 16:50  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 16:52  Bournemouth                             7     On time
## 16:57  London Paddington                       -     Cancelled
## 16:58  Bristol Temple Meads                    9     On time
## 17:02  Plymouth                                -     Cancelled
## 17:03  Ealing Broadway                         14    On time
## 17:05  London Paddington                       -     Cancelled
## 17:05  London Paddington                       -     17:17
## 17:10  Newbury                                 -     Cancelled
## 17:11  London Paddington                       11    On time
## 17:12  Bedwyn                                  -     On time
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9     On time
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   13    On time
## 17:20  Redhill                                 5     On time
## 17:22  Ealing Broadway                         14    On time
## 17:24  London Paddington                       -     Cancelled
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    -     Cancelled
## 17:27  London Paddington                       -     Cancelled
## 17:29  Plymouth                                7     On time
## 17:32  London Paddington                       -     Cancelled
## 17:34  Basingstoke                             2     On time
## 17:38  Newbury                                 -     Cancelled
## 17:41  London Paddington                       -     Cancelled
## 17:42  London Waterloo                         6     On time
## 17:43  London Paddington                       -     Cancelled
## 17:43  Swansea                                 9     On time
## 17:46  London Paddington                       10    On time
## 17:50  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 17:52  Ealing Broadway                         14    On time
## 17:52  Southampton Central                     7     On time
## 17:57  Basingstoke                             2     On time
## 17:57  Bristol Temple Meads                    8     On time
## 17:58  Didcot Parkway                          12B   On time
## 17:58  London Paddington                       -     On time
## 18:00  Hereford                                -     Cancelled
## 18:00  London Paddington                       -     Cancelled
## 18:03  Plymouth                                -     Cancelled
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
