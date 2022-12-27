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

## Example (Last rendered on 2022-12-27 18:04)

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
## Reading (RDG) Station Board on 2022-12-27 18:04:10
## Time   From                                    Plat  Expected
## 17:19  London Paddington                       9B    18:01
## 17:38  Bristol Temple Meads                    10    Delayed
## 17:40  Manchester Piccadilly                   8B    17:59
## 17:55  London Paddington                       8     18:10
## 17:56  Hereford                                10    18:04
## 17:57  Plymouth                                11    18:45
## 17:58  London Paddington                       7B    18:04
## 18:02  Redhill                                 5     18:08
## 18:03  Didcot Parkway                          15A   18:09
## 18:06  Bournemouth                             12B   18:21
## 18:09  Bristol Temple Meads                    11    18:33
## 18:10  London Paddington                       14    On time
## 18:13  Swansea                                 10    Delayed
## 18:20  Basingstoke                             2     On time
## 18:21  London Paddington                       9     18:29
## 18:25  London Paddington                       8     18:28
## 18:25  Newbury                                 11A   18:27
## 18:26  Oxford                                  10    On time
## 18:27  London Paddington                       7     On time
## 18:29  Didcot Parkway                          15A   On time
## 18:30  London Paddington                       12B   On time
## 18:33  Redhill                                 4     18:48
## 18:35  Newbury                                 1     On time
## 18:36  London Paddington                       12B   On time
## 18:40  Bristol Temple Meads                    10    18:45
## 18:40  London Paddington                       14    On time
## 18:40  Manchester Piccadilly                   8     18:49
## 18:40  Newbury                                 11A   On time
## 18:49  London Paddington                       9     On time
## 18:50  Basingstoke                             3     On time
## 18:53  London Paddington                       12B   On time
## 18:53  London Paddington                       7     On time
## 18:57  Penzance                                11    19:21
## 18:57  Worcester Foregate Street               10    On time
## 18:59  London Paddington                       7     On time
## 19:04  Basingstoke                             2     On time
## 19:05  Didcot Parkway                          15A   On time
## 19:09  London Paddington                       13    On time
## 19:09  Redhill                                 14    On time
## 19:10  Bristol Temple Meads                    10    Delayed
## 19:13  Swansea                                 11    On time
## 19:15  Newbury                                 12    On time
## 19:19  London Paddington                       9     On time
## 19:23  Oxford                                  10    On time
## 19:28  Didcot Parkway                          15A   On time
## 19:28  London Paddington                       7     On time
## 19:33  Redhill                                 4     On time
## 19:34  London Paddington                       12B   On time
## 19:35  Basingstoke                             2     On time
## 19:35  London Paddington                       8B    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:40  London Paddington                       13    On time
## 19:41  Manchester Piccadilly                   7     On time
## 19:49  London Paddington                       9     On time
## 19:53  London Paddington                       8     On time
## 19:54  Plymouth                                11    19:59
## 19:54  Worcester Foregate Street               10    On time
## 19:55  London Paddington                       12B   On time
## 19:56  London Paddington                       9     On time
## 20:00  Basingstoke                             1     On time
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
## Reading (RDG) Station Board on 2022-12-27 18:04:16
## Time   To                                      Plat  Expected
## 17:23  Great Malvern                           9B    18:02
## 17:41  London Paddington                       10    Delayed
## 17:52  Bournemouth                             8B    18:04
## 17:53  Carmarthen                              9     18:10
## 17:57  Bristol Temple Meads                    8     18:11
## 17:58  London Paddington                       11    18:46
## 18:00  Hereford                                7B    18:05
## 18:00  London Paddington                       10    18:05
## 18:03  Plymouth                                7B    18:19
## 18:07  Newbury                                 1     On time
## 18:08  Ealing Broadway                         15A   18:10
## 18:12  London Paddington                       11    18:34
## 18:15  Manchester Piccadilly                   12B   18:22
##        via Coventry & Stoke-on-Trent           
## 18:16  London Paddington                       10    Delayed
## 18:20  Redhill                                 5     On time
## 18:23  Worcester Foregate Street               9     18:30
## 18:26  London Paddington                       11A   18:28
## 18:27  Bristol Temple Meads                    8     18:29
## 18:28  Ealing Broadway                         14    On time
## 18:28  London Paddington                       10    On time
## 18:29  Penzance                                7     On time
## 18:32  Basingstoke                             2     On time
## 18:32  Didcot Parkway                          12B   On time
## 18:37  Ealing Broadway                         15A   On time
## 18:41  Newbury                                 12B   On time
## 18:43  London Paddington                       10    18:43
## 18:45  London Paddington                       11A   On time
## 18:53  Banbury                                 9     On time
## 18:56  Swansea                                 7     On time
## 18:57  Didcot Parkway                          12B   On time
## 18:58  Ealing Broadway                         14    On time
## 18:58  London Paddington                       11    19:22
## 19:00  London Paddington                       10    On time
## 19:00  Swansea                                 9     On time
## 19:01  Plymouth                                7     On time
## 19:01  Redhill                                 4     On time
## 19:05  Basingstoke                             3     On time
## 19:10  Newbury                                 1     On time
## 19:12  Ealing Broadway                         15A   On time
## 19:13  London Paddington                       10    Delayed
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:16  London Paddington                       11    On time
## 19:20  Redhill                                 15A   On time
## 19:23  Hereford                                9     On time
## 19:25  Basingstoke                             2     On time
## 19:27  Ealing Broadway                         13    On time
## 19:27  London Paddington                       10    On time
## 19:29  Plymouth                                7     On time
## 19:34  Didcot Parkway                          12B   On time
## 19:37  Bedwyn                                  8B    On time
## 19:37  Ealing Broadway                         15A   On time
## 19:41  London Paddington                       10    On time
## 19:50  Bournemouth                             7     On time
## 19:51  Oxford                                  9     On time
## 19:55  London Paddington                       11    20:00
## 19:55  Swansea                                 8     On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          12B   On time
## 19:57  Ealing Broadway                         13    On time
## 19:58  London Paddington                       10    On time
## 19:59  Weston-super-Mare                       9     On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
