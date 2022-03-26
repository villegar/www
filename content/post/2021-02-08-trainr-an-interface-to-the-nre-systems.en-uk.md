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

## Example (Last rendered on 2022-03-26 08:04)

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
## Reading (RDG) Station Board on 2022-03-26 08:04:17
## Time   From                                    Plat  Expected
## 07:51  Gatwick Airport                         14    Delayed
## 08:02  Didcot Parkway                          15    On time
## 08:10  Weston-super-Mare                       10    On time
## 08:11  London Paddington                       9     On time
## 08:13  Ascot                                   4     On time
## 08:13  London Paddington                       14    On time
## 08:14  London Paddington                       12    On time
## 08:16  Bedwyn                                  11    On time
## 08:16  Swansea                                 10    On time
## 08:17  London Paddington                       9     On time
## 08:21  Basingstoke                             2     On time
## 08:25  London Paddington                       9     On time
## 08:25  Oxford                                  11A   On time
## 08:28  London Paddington                       7     On time
## 08:30  Gloucester                              10A   On time
## 08:32  Didcot Parkway                          15    On time
## 08:33  London Paddington                       7B    On time
## 08:33  Redhill                                 5     On time
## 08:38  London Paddington                       9     On time
## 08:39  Manchester Piccadilly                   8     On time
## 08:41  Bristol Temple Meads                    11    On time
## 08:42  Newbury                                 1     On time
## 08:43  Ascot                                   6     On time
## 08:43  London Paddington                       14    On time
## 08:44  London Paddington                       12    On time
## 08:46  Swansea                                 10    On time
## 08:47  London Paddington                       9     On time
## 08:51  Basingstoke                             2     On time
## 08:51  Gatwick Airport                         4     On time
## 08:52  London Paddington                       9B    On time
## 08:54  Worcester Shrub Hill                    10A   On time
## 08:55  London Paddington                       8     On time
## 08:58  London Paddington                       7     On time
## 09:01  Didcot Parkway                          15    On time
## 09:03  Plymouth                                11    On time
## 09:06  Southampton Airport Parkway             13B   On time
## 09:10  Taunton                                 10    On time
## 09:11  London Paddington                       8     On time
## 09:13  Ascot                                   4     On time
## 09:13  London Paddington                       14    On time
## 09:15  London Paddington                       12    On time
## 09:16  Swansea                                 11    On time
## 09:17  London Paddington                       9B    On time
## 09:20  Basingstoke                             2     On time
## 09:23  Bedwyn                                  -     Cancelled
## 09:25  London Paddington                       9     On time
## 09:25  Oxford                                  10    On time
## 09:27  London Paddington                       7     On time
## 09:31  Didcot Parkway                          15    On time
## 09:33  London Paddington                       -     Cancelled
## 09:33  Redhill                                 5     On time
## 09:34  Gloucester                              11    On time
## 09:41  Bristol Temple Meads                    10    On time
## 09:41  Newbury                                 -     Cancelled
## 09:43  Ascot                                   6     On time
## 09:43  London Paddington                       14    On time
## 09:43  Plymouth                                11    On time
## 09:44  London Paddington                       12    On time
## 09:46  Swansea                                 10    On time
## 09:47  London Paddington                       9B    On time
## 09:48  Basingstoke                             2     On time
## 09:51  Gatwick Airport                         4     On time
## 09:51  London Paddington                       8B    On time
## 09:55  London Paddington                       9     On time
## 08:35  Heathrow Central Bus Stn                BUS   On time
## 09:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-26 08:04:21
## Time   To                                      Plat  Expected
## 08:06  Redhill                                 4     On time
## 08:07  Basingstoke                             2     On time
## 08:09  Ascot                                   5     On time
## 08:12  London Paddington                       10    On time
## 08:13  Swansea                                 9     On time
## 08:18  London Paddington                       10    On time
## 08:20  Great Malvern                           9     On time
## 08:20  London Paddington                       11    On time
## 08:22  Ealing Broadway                         14    On time
## 08:23  Didcot Parkway                          12    On time
## 08:26  Bristol Temple Meads                    9     On time
## 08:26  London Paddington                       11A   On time
## 08:30  Penzance                                7     On time
## 08:35  London Paddington                       10A   On time
## 08:35  Newbury                                 7B    On time
## 08:38  Basingstoke                             2     On time
## 08:39  Ascot                                   4     On time
## 08:40  Bristol Parkway                         9     On time
## 08:43  London Paddington                       11    On time
## 08:48  London Paddington                       10    On time
## 08:49  Oxford                                  9     On time
## 08:52  Ealing Broadway                         14    On time
## 08:52  Southampton Airport Parkway             8     On time
## 08:53  Didcot Parkway                          12    On time
## 08:54  Gloucester                              9B    On time
## 08:57  London Paddington                       10A   On time
## 08:59  Taunton                                 8     On time
## 09:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:02  Exeter St Davids                        7     On time
## 09:05  London Paddington                       11    On time
## 09:06  Newbury                                 -     Cancelled
## 09:09  Ascot                                   6     On time
## 09:09  Basingstoke                             2     On time
## 09:12  London Paddington                       10    On time
## 09:13  Swansea                                 8     On time
## 09:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 09:18  London Paddington                       11    On time
## 09:20  Great Malvern                           9B    On time
## 09:20  Redhill                                 5     On time
## 09:24  Didcot Parkway                          12    On time
## 09:25  London Paddington                       -     Cancelled
## 09:27  Bristol Temple Meads                    9     On time
## 09:27  London Paddington                       10    On time
## 09:30  Plymouth                                7     On time
## 09:35  Bedwyn                                  -     Cancelled
## 09:35  London Paddington                       11    On time
## 09:38  Basingstoke                             2     On time
## 09:39  Ascot                                   4     On time
## 09:43  London Paddington                       10    On time
## 09:45  London Paddington                       11    On time
## 09:48  London Paddington                       10    On time
## 09:49  Oxford                                  9B    On time
## 09:53  Didcot Parkway                          12    On time
## 09:53  Gloucester                              8B    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
