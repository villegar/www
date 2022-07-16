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

## Example (Last rendered on 2022-07-16 14:06)

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
## Reading (RDG) Station Board on 2022-07-16 14:06:56
## Time   From                                    Plat  Expected
## 14:46  Carmarthen                              10    15:04
## 15:00  Penzance                                12    On time
## 15:05  Bournemouth                             12B   15:08
## 15:10  Bristol Temple Meads                    9     On time
## 15:11  London Paddington                       8     On time
## 15:14  Newbury                                 10    On time
## 15:15  London Paddington                       13    15:25
## 15:17  London Paddington                       9B    On time
## 15:20  Basingstoke                             2     15:22
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10A   On time
## 15:31  Didcot Parkway                          15    On time
## 15:31  Newquay                                 11A   16:21
## 15:33  Cheltenham Spa                          10A   15:36
## 15:33  London Paddington                       7     On time
## 15:33  London Paddington                       14    15:40
## 15:33  Redhill                                 5     On time
## 15:38  London Paddington                       9     On time
## 15:40  Manchester Piccadilly                   13    On time
## 15:40  Weston-super-Mare                       10    On time
## 15:43  London Paddington                       12    On time
## 15:47  London Paddington                       9B    On time
## 15:47  Swansea                                 10    On time
## 15:48  Newbury                                 7     On time
## 15:51  Gatwick Airport                         4     On time
## 15:52  Exeter St Davids                        11    On time
## 15:53  Charlbury                               10A   On time
## 15:55  London Paddington                       9     On time
## 15:56  Basingstoke                             2     On time
## 16:00  Didcot Parkway                          15    On time
## 16:00  Penzance                                11    16:05
## 16:03  London Paddington                       14    On time
## 16:10  Bristol Temple Meads                    10    Delayed
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       12    On time
## 16:17  London Paddington                       9B    On time
## 16:19  Cardiff Central                         10    16:21
## 16:20  Basingstoke                             2     On time
## 16:25  London Paddington                       9     On time
## 16:25  Oxford                                  10A   On time
## 16:29  Newbury                                 11    On time
## 16:31  Didcot Parkway                          15    On time
## 16:33  London Paddington                       7     On time
## 16:33  London Paddington                       14    On time
## 16:33  Redhill                                 4     On time
## 16:39  Manchester Piccadilly                   7B    On time
## 16:40  Weston-super-Mare                       10    On time
## 16:41  London Paddington                       9     On time
## 16:41  Newbury                                 7     On time
## 16:43  London Paddington                       12    On time
## 16:46  Swansea                                 10    On time
## 16:47  London Paddington                       9     On time
## 16:50  Basingstoke                             2     On time
## 16:51  Gatwick Airport                         5     On time
## 16:51  London Paddington                       8     On time
## 16:54  Charlbury                               10    On time
## 16:54  London Paddington                       9     On time
## 16:59  Penzance                                11    On time
## 17:03  London Paddington                       14    On time
## 15:32  Staines                                 BUS   On time
## 15:33  Staines                                 BUS   On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
## 16:02  Staines                                 BUS   On time
## 16:03  Staines                                 -     Cancelled
## 16:32  Staines                                 BUS   On time
## 16:33  Staines                                 BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
## 17:02  Staines                                 BUS   On time
## 17:03  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-16 14:07:00
## Time   To                                      Plat  Expected
## 14:48  London Paddington                       10    15:06
## 15:05  London Paddington                       12    On time
## 15:07  Basingstoke                             2     On time
## 15:11  Newbury                                 11    On time
## 15:12  London Paddington                       9     On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15    On time
## 15:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 15:16  London Paddington                       10    On time
## 15:19  Charlbury                               9B    On time
## 15:20  Redhill                                 6     On time
## 15:24  Didcot Parkway                          13    15:26
## 15:24  Ealing Broadway                         14    On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       10A   On time
## 15:29  Penzance                                7     On time
## 15:33  London Paddington                       11A   16:22
## 15:34  Newbury                                 7     On time
## 15:35  London Paddington                       10A   15:37
## 15:37  Basingstoke                             2     On time
## 15:40  Bristol Parkway                         9     On time
## 15:43  London Paddington                       10    On time
## 15:45  Ealing Broadway                         15    On time
## 15:49  Oxford                                  9B    On time
## 15:50  London Paddington                       10    On time
## 15:53  Didcot Parkway                          12    On time
## 15:54  Ealing Broadway                         14    On time
## 15:56  London Paddington                       11    On time
## 15:57  Weston-super-Mare                       9     On time
## 15:58  London Paddington                       10A   On time
## 16:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:05  London Paddington                       11    16:05
## 16:07  Basingstoke                             2     On time
## 16:12  London Paddington                       10    Delayed
## 16:12  Newbury                                 7     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Charlbury                               9B    On time
## 16:20  London Paddington                       10    16:22
## 16:20  Redhill                                 4     On time
## 16:23  Didcot Parkway                          12    On time
## 16:24  Ealing Broadway                         14    On time
## 16:26  London Paddington                       10A   On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:29  Plymouth                                7     On time
## 16:31  London Paddington                       11    On time
## 16:34  Newbury                                 7     On time
## 16:37  Basingstoke                             2     On time
## 16:42  London Paddington                       10    On time
## 16:43  Cardiff Central                         9     On time
## 16:45  Ealing Broadway                         15    On time
## 16:48  London Paddington                       10    On time
## 16:49  Oxford                                  9     On time
## 16:52  Bournemouth                             7B    On time
## 16:53  Cheltenham Spa                          8     On time
## 16:53  Didcot Parkway                          12    On time
## 16:54  Ealing Broadway                         14    On time
## 16:56  London Paddington                       10    On time
## 16:57  Taunton                                 9     On time
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:01  Paignton                                8     On time
## 17:05  London Paddington                       11    On time
## 15:12  Staines                                 BUS   On time
## 15:13  Staines                                 BUS   On time
## 15:42  Staines                                 BUS   On time
## 15:43  Staines                                 BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 16:12  Staines                                 BUS   On time
## 16:13  Staines                                 BUS   On time
## 16:42  Staines                                 BUS   On time
## 16:43  Staines                                 BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
