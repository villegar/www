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

## Example (Last rendered on 2022-07-02 16:03)

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
## Reading (RDG) Station Board on 2022-07-02 16:03:29
## Time   From                                    Plat  Expected
## 16:51  London Paddington                       8     17:09
## 17:01  Didcot Parkway                          15    On time
## 17:01  Penzance                                11    17:30
## 17:03  London Paddington                       14    On time
## 17:05  Bournemouth                             13    On time
## 17:10  Bristol Temple Meads                    10    On time
## 17:11  Ascot                                   4     On time
## 17:13  London Paddington                       12    On time
## 17:17  London Paddington                       9B    On time
## 17:25  London Paddington                       9     On time
## 17:25  Oxford                                  10A   On time
## 17:28  Newbury                                 11    On time
## 17:31  Didcot Parkway                          15    On time
## 17:33  Cheltenham Spa                          -     Cancelled
## 17:33  London Paddington                       7     On time
## 17:33  London Paddington                       14    On time
## 17:33  Redhill                                 5     On time
## 17:38  Swansea                                 10    On time
## 17:40  Manchester Piccadilly                   7     18:00
## 17:41  Ascot                                   6     On time
## 17:41  London Paddington                       9     On time
## 17:41  Newbury                                 1     On time
## 17:43  London Paddington                       12    On time
## 17:44  Paignton                                11    17:57
## 17:46  Weston-super-Mare                       10    On time
## 17:47  London Paddington                       8B    On time
## 17:51  Gatwick Airport                         4     On time
## 17:52  London Paddington                       9B    On time
## 17:54  Great Malvern                           10A   On time
## 17:55  London Paddington                       8     On time
## 17:58  Basingstoke                             2     On time
## 18:01  Didcot Parkway                          15    On time
## 18:01  Penzance                                11    On time
## 18:03  London Paddington                       14    On time
## 18:10  Bristol Temple Meads                    10    On time
## 18:11  Ascot                                   5     On time
## 18:11  London Paddington                       9     On time
## 18:13  London Paddington                       12    On time
## 18:17  London Paddington                       9     On time
## 18:21  Bristol Parkway                         11    On time
## 18:25  London Paddington                       9     On time
## 18:25  Oxford                                  10A   On time
## 18:29  Newbury                                 11    On time
## 18:31  Didcot Parkway                          15    On time
## 18:33  Cheltenham Spa                          10A   On time
## 18:33  London Paddington                       7     On time
## 18:33  London Paddington                       14    On time
## 18:33  Redhill                                 4     On time
## 18:39  Weston-super-Mare                       11A   On time
## 18:41  Ascot                                   6     On time
## 18:41  London Paddington                       9     On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       12    On time
## 18:45  Swansea                                 10    On time
## 18:47  London Paddington                       9B    On time
## 18:51  Gatwick Airport                         5     On time
## 18:51  London Paddington                       8     On time
## 18:54  Great Malvern                           10A   On time
## 18:55  London Paddington                       9     On time
## 18:58  Basingstoke                             2     On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-02 16:03:32
## Time   To                                      Plat  Expected
## 16:53  Cheltenham Spa                          8     17:10
## 17:01  Paignton                                -     Cancelled
## 17:05  Basingstoke                             2     On time
## 17:05  London Paddington                       11    17:31
## 17:12  Ascot                                   6     On time
## 17:12  Newbury                                 1     On time
## 17:14  London Paddington                       10    On time
## 17:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                9B    On time
## 17:20  Ealing Broadway                         15    On time
## 17:20  Redhill                                 5     On time
## 17:23  Didcot Parkway                          12    On time
## 17:24  Ealing Broadway                         14    On time
## 17:27  Bristol Temple Meads                    9     On time
## 17:27  London Paddington                       10A   On time
## 17:30  London Paddington                       11    On time
## 17:30  Penzance                                7     17:37
## 17:35  London Paddington                       -     Cancelled
## 17:35  Newbury                                 7     On time
## 17:40  London Paddington                       10    On time
## 17:42  Ascot                                   4     On time
## 17:43  Swansea                                 9     On time
## 17:45  Ealing Broadway                         15    On time
## 17:46  London Paddington                       11    17:58
## 17:50  London Paddington                       10    On time
## 17:50  Oxford                                  8B    On time
## 17:54  Cheltenham Spa                          9B    On time
## 17:54  Ealing Broadway                         14    On time
## 17:55  Didcot Parkway                          12    On time
## 17:56  London Paddington                       10A   On time
## 18:00  Weston-super-Mare                       8     On time
## 18:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:05  Basingstoke                             2     On time
## 18:05  London Paddington                       11    On time
## 18:08  Newbury                                 1     On time
## 18:12  Ascot                                   6     On time
## 18:12  London Paddington                       10    On time
## 18:13  Bristol Parkway                         9     On time
## 18:15  Birmingham New Street                   7     On time
##        via Coventry                            
## 18:15  Ealing Broadway                         15    On time
## 18:19  Worcester Foregate Street               9     On time
## 18:23  Didcot Parkway                          12    On time
## 18:24  Ealing Broadway                         14    On time
## 18:24  London Paddington                       11    On time
## 18:27  Bristol Temple Meads                    9     On time
## 18:27  London Paddington                       10A   On time
## 18:29  Penzance                                7B    On time
## 18:31  London Paddington                       11    On time
## 18:34  Newbury                                 7     On time
## 18:35  London Paddington                       10A   On time
## 18:36  Redhill                                 6     On time
## 18:41  London Paddington                       11A   On time
## 18:42  Ascot                                   5     On time
## 18:43  Swansea                                 9     On time
## 18:45  Ealing Broadway                         15    On time
## 18:46  London Paddington                       10    On time
## 18:49  Oxford                                  9B    On time
## 18:52  Bournemouth                             7     On time
## 18:53  Cheltenham Spa                          8     On time
## 18:53  Didcot Parkway                          12    On time
## 18:54  Ealing Broadway                         14    On time
## 18:56  London Paddington                       10A   On time
## 18:57  Bristol Temple Meads                    9     On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
