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

## Example (Last rendered on 2022-12-10 18:03)

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
## Reading (RDG) Station Board on 2022-12-10 18:03:58
## Time   From                                    Plat  Expected
## 17:40  Bristol Temple Meads                    10    18:13
## 17:47  Swansea                                 10    18:09
## 17:55  London Paddington                       8     18:01
## 18:00  Plymouth                                11    18:18
## 18:01  Didcot Parkway                          15A   18:03
## 18:03  Abbey Wood                              14    On time
## 18:10  Bristol Temple Meads                    10    18:18
## 18:11  London Paddington                       9     18:24
## 18:13  London Paddington                       12    On time
## 18:14  London Waterloo                         5     18:27
## 18:17  London Paddington                       9     On time
## 18:21  Basingstoke                             2     On time
## 18:21  Bristol Parkway                         11    18:24
## 18:25  London Paddington                       9     18:34
## 18:25  Oxford                                  10    On time
## 18:27  London Paddington                       7     Delayed
## 18:29  Newbury                                 11    On time
## 18:31  Didcot Parkway                          15    On time
## 18:33  Abbey Wood                              14    On time
## 18:33  Cheltenham Spa                          10    On time
## 18:33  London Paddington                       7     On time
## 18:33  Redhill                                 4     On time
## 18:40  Weston-super-Mare                       11    18:51
## 18:41  London Paddington                       9     On time
## 18:41  Manchester Piccadilly                   7     19:00
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       12    On time
## 18:44  London Waterloo                         -     Cancelled
## 18:46  Swansea                                 10    18:48
## 18:47  London Paddington                       9     On time
## 18:50  Basingstoke                             -     Cancelled
## 18:51  Gatwick Airport                         5     On time
## 18:51  London Paddington                       8     On time
## 18:54  Great Malvern                           10    On time
## 18:55  London Paddington                       9     On time
## 18:59  Penzance                                11    On time
## 19:01  Didcot Parkway                          15    On time
## 19:04  Abbey Wood                              14    On time
## 19:06  Bournemouth                             13B   On time
## 19:11  Bristol Temple Meads                    10    19:17
## 19:11  London Paddington                       9     On time
## 19:14  London Paddington                       12    On time
## 19:14  London Waterloo                         5     19:26
## 19:17  London Paddington                       9     On time
## 19:22  Basingstoke                             2     On time
## 19:25  London Paddington                       -     Cancelled
## 19:26  Oxford                                  10    On time
## 19:27  London Paddington                       7     On time
## 19:27  Newbury                                 11    On time
## 19:31  Didcot Parkway                          15    On time
## 19:32  London Paddington                       7     On time
## 19:32  Redhill                                 6     On time
## 19:33  Abbey Wood                              14    On time
## 19:38  London Paddington                       9     On time
## 19:40  Manchester Piccadilly                   13    On time
## 19:40  Newbury                                 1     On time
## 19:40  Weston-super-Mare                       10    On time
## 19:43  London Paddington                       12    On time
## 19:44  London Waterloo                         4     19:56
## 19:46  Swansea                                 10    On time
## 19:47  London Paddington                       7     On time
## 19:49  London Paddington                       8     On time
## 19:51  Basingstoke                             2     On time
## 19:51  Gatwick Airport                         5     On time
## 19:51  London Paddington                       9     On time
## 19:54  Great Malvern                           10    On time
## 19:55  London Paddington                       8     On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-10 18:04:04
## Time   To                                      Plat  Expected
## 17:42  London Paddington                       10    18:16
## 17:48  London Paddington                       10    18:10
## 18:00  Weston-super-Mare                       8     18:05
## 18:05  London Paddington                       11    18:19
## 18:08  Newbury                                 1     On time
## 18:09  London Waterloo                         -     Cancelled
## 18:12  Basingstoke                             3     On time
## 18:12  London Paddington                       10    18:19
## 18:13  Swansea                                 9     18:25
## 18:15  Ealing Broadway                         15A   On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:19  Worcester Foregate Street               9     On time
## 18:23  Didcot Parkway                          12    On time
## 18:24  Abbey Wood                              14    On time
## 18:24  London Paddington                       11    18:24
## 18:27  Bristol Temple Meads                    9     18:35
## 18:27  London Paddington                       10    On time
## 18:29  Penzance                                7     Delayed
## 18:31  London Paddington                       11    On time
## 18:34  Newbury                                 7     On time
## 18:35  London Paddington                       10    On time
## 18:36  Redhill                                 4     On time
## 18:37  Basingstoke                             2     On time
## 18:39  London Waterloo                         5     On time
## 18:42  London Paddington                       11    18:52
## 18:43  Swansea                                 9     On time
## 18:45  Ealing Broadway                         15    On time
## 18:49  Oxford                                  9     On time
## 18:50  London Paddington                       10    On time
## 18:52  Bournemouth                             7     19:01
## 18:53  Cheltenham Spa                          8     On time
## 18:53  Didcot Parkway                          12    On time
## 18:54  Abbey Wood                              14    On time
## 18:56  London Paddington                       10    On time
## 18:57  Bristol Temple Meads                    9     On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    On time
## 19:09  London Waterloo                         6     On time
## 19:10  Newbury                                 1     On time
## 19:13  London Paddington                       10    19:18
## 19:13  Swansea                                 9     On time
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 19:19  Hereford                                9     On time
## 19:20  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:23  Didcot Parkway                          12    On time
## 19:24  Abbey Wood                              14    On time
## 19:27  Bristol Temple Meads                    -     Cancelled
## 19:28  London Paddington                       10    On time
## 19:29  Plymouth                                7     On time
## 19:32  London Paddington                       11    On time
## 19:34  Newbury                                 7     On time
## 19:37  Basingstoke                             2     On time
## 19:39  London Waterloo                         5     On time
## 19:41  Swansea                                 9     On time
## 19:42  London Paddington                       10    On time
## 19:45  Ealing Broadway                         15    On time
## 19:48  London Paddington                       10    On time
## 19:51  Oxford                                  8     On time
## 19:53  Cheltenham Spa                          9     On time
## 19:54  Abbey Wood                              14    On time
## 19:55  Didcot Parkway                          12    On time
## 19:56  London Paddington                       10    On time
## 19:57  Taunton                                 8     On time
## 20:01  Redhill                                 -     Cancelled
## 20:03  London Paddington                       11    20:46
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
