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

## Example (Last rendered on 2022-08-07 10:03)

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
## Reading (RDG) Station Board on 2022-08-07 10:03:55
## Time   From                                    Plat  Expected
## 10:57  Great Malvern                           11    11:16
## 10:59  London Paddington                       -     Cancelled
## 11:03  Ascot                                   4     11:27
## 11:05  Bournemouth                             7     On time
## 11:07  London Paddington                       8     11:13
## 11:08  Redhill                                 6     On time
## 11:10  Didcot Parkway                          15    11:13
## 11:11  London Paddington                       9B    11:27
## 11:13  Bristol Temple Meads                    10    On time
## 11:16  London Paddington                       14    On time
## 11:17  Swansea                                 11    On time
## 11:19  Bedwyn                                  1     11:26
## 11:25  Oxford                                  10A   On time
## 11:26  London Paddington                       7     11:35
## 11:32  Ascot                                   4     On time
## 11:33  Basingstoke                             2     On time
## 11:33  London Paddington                       14    On time
## 11:35  Plymouth                                11    On time
## 11:38  Gatwick Airport                         5     11:40
## 11:38  Manchester Piccadilly                   7     11:40
## 11:44  Swansea                                 11    On time
## 11:45  London Paddington                       9B    On time
## 11:47  Salisbury                               1     On time
## 11:53  London Paddington                       9     On time
## 11:56  Great Malvern                           10A   On time
## 11:58  Plymouth                                11    On time
## 12:02  Ascot                                   -     Cancelled
## 12:03  London Paddington                       14    On time
## 12:07  London Paddington                       8     On time
## 12:08  Redhill                                 6     On time
## 12:10  Didcot Parkway                          15    On time
## 12:11  London Paddington                       9     On time
## 12:13  Bristol Temple Meads                    10    On time
## 12:17  London Paddington                       8     On time
## 12:19  Newbury                                 1     On time
## 12:25  Oxford                                  10A   On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10A   On time
## 12:32  Ascot                                   4     On time
## 12:33  Basingstoke                             2     On time
## 12:33  London Paddington                       14    On time
## 12:38  Gatwick Airport                         5     On time
## 12:38  Manchester Piccadilly                   12    On time
## 12:44  Swansea                                 10    On time
## 12:45  London Paddington                       9     On time
## 12:47  Salisbury                               1     On time
## 12:53  London Paddington                       9     On time
## 12:55  Penzance                                11    On time
## 12:56  Great Malvern                           10A   On time
## 12:59  London Paddington                       -     Cancelled
## 13:02  Ascot                                   4     On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-07 10:03:59
## Time   To                                      Plat  Expected
## 10:59  London Paddington                       11    11:17
## 11:01  Paignton                                -     Cancelled
## 11:09  Swansea                                 8     11:14
## 11:10  Salisbury                               1     On time
## 11:12  Great Malvern                           9B    11:28
## 11:14  Ealing Broadway                         15    On time
## 11:15  London Paddington                       10    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  London Paddington                       11    On time
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:24  Ascot                                   4     On time
## 11:24  Ealing Broadway                         13    On time
## 11:25  London Paddington                       10A   On time
## 11:28  Newquay                                 7     11:36
## 11:30  Didcot Parkway                          14    On time
## 11:35  London Paddington                       11    On time
## 11:38  Basingstoke                             2     On time
## 11:41  Redhill                                 6     On time
## 11:43  Bedwyn                                  1     On time
## 11:46  London Paddington                       11    On time
## 11:48  Oxford                                  9B    On time
## 11:52  Bournemouth                             7     On time
## 11:54  Ascot                                   4     On time
## 11:54  Bristol Temple Meads                    9     On time
## 11:54  Ealing Broadway                         14    On time
## 11:59  London Paddington                       11    On time
## 12:02  London Paddington                       10A   On time
## 12:09  Carmarthen                              8     On time
## 12:12  Hereford                                9     On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         15    On time
## 12:15  London Paddington                       10    On time
## 12:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:24  Ascot                                   4     On time
## 12:24  Ealing Broadway                         14    On time
## 12:25  London Paddington                       10A   On time
## 12:28  Penzance                                7     On time
## 12:30  Didcot Parkway                          8     On time
## 12:33  London Paddington                       10A   On time
## 12:38  Basingstoke                             2     On time
## 12:41  Redhill                                 6     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:48  Oxford                                  9     On time
## 12:54  Ascot                                   4     On time
## 12:54  Ealing Broadway                         14    On time
## 12:55  Weston-super-Mare                       9     On time
## 12:57  London Paddington                       11    On time
## 13:00  London Paddington                       10A   On time
## 13:01  Paignton                                -     Cancelled
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
