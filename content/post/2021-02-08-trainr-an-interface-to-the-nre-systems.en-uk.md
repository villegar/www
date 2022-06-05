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

## Example (Last rendered on 2022-06-05 16:03)

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
## Reading (RDG) Station Board on 2022-06-05 16:03:59
## Time   From                                    Plat  Expected
## 16:44  Swansea                                 11    17:02
## 16:53  London Paddington                       9     17:01
## 16:58  Plymouth                                11    18:14
## 17:00  Great Malvern                           10A   On time
## 17:02  London Waterloo                         4     On time
## 17:03  London Paddington                       14    On time
## 17:05  Bournemouth                             8     On time
## 17:07  London Paddington                       9     On time
## 17:08  Redhill                                 6     On time
## 17:10  Bristol Temple Meads                    10    17:14
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       12    On time
## 17:13  London Paddington                       9     On time
## 17:20  Bedwyn                                  3     17:22
## 17:26  London Paddington                       7     17:30
## 17:32  London Waterloo                         4     On time
## 17:33  Basingstoke                             2     17:38
## 17:33  London Paddington                       14    On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:39  Paignton                                -     Cancelled
## 17:45  Carmarthen                              11    On time
## 17:45  London Paddington                       9     On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Newquay                                 11    Delayed
## 18:00  Hereford                                10    18:03
## 18:02  London Waterloo                         4     On time
## 18:03  London Paddington                       14    On time
## 18:06  Exeter St Davids                        10    18:10
## 18:07  London Paddington                       9     On time
## 18:08  Redhill                                 6     On time
## 18:12  London Paddington                       9     On time
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       12    On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:23  Swindon                                 10    On time
## 18:26  London Paddington                       -     Cancelled
## 18:32  London Waterloo                         4     On time
## 18:33  Basingstoke                             2     On time
## 18:33  Cheltenham Spa                          11    On time
## 18:33  London Paddington                       14    On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:44  Swansea                                 10    On time
## 18:45  London Paddington                       8     On time
## 18:53  London Paddington                       9     On time
## 18:58  Penzance                                11    19:04
## 18:59  London Paddington                       7     On time
## 19:00  Great Malvern                           10    On time
## 19:02  London Waterloo                         4     On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-05 16:04:03
## Time   To                                      Plat  Expected
## 16:46  London Paddington                       11    17:04
## 16:55  Plymouth                                9     17:04
##        via Bristol                             
## 16:59  London Paddington                       11    18:15
## 17:02  Exeter St Davids                        7B    17:10
## 17:02  London Paddington                       10A   On time
## 17:09  Swansea                                 9     On time
## 17:12  London Paddington                       10    17:15
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           9     17:16
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:24  Ealing Broadway                         14    On time
## 17:24  London Waterloo                         4     On time
## 17:25  Didcot Parkway                          12    On time
## 17:28  Penzance                                7     17:31
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       -     Cancelled
## 17:41  Redhill                                 6     On time
## 17:43  Bedwyn                                  3     On time
## 17:48  Oxford                                  9     On time
## 17:49  London Paddington                       11    On time
## 17:52  Bournemouth                             8B    On time
## 17:54  Ealing Broadway                         14    On time
## 17:54  London Waterloo                         4     On time
## 17:55  Bristol Temple Meads                    9     On time
## 17:59  London Paddington                       11    Delayed
## 18:00  Cheltenham Spa                          8     On time
## 18:02  London Paddington                       10    18:04
## 18:09  Swansea                                 9     On time
## 18:13  London Paddington                       10    On time
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9     On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:24  Ealing Broadway                         14    On time
## 18:24  London Paddington                       10    On time
## 18:24  London Waterloo                         4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:28  Penzance                                -     Cancelled
## 18:33  London Paddington                       11    On time
## 18:38  Basingstoke                             2     On time
## 18:41  Redhill                                 6     On time
## 18:43  Newbury                                 1     On time
## 18:46  London Paddington                       10    On time
## 18:48  Oxford                                  8     On time
## 18:54  Ealing Broadway                         14    On time
## 18:54  London Waterloo                         4     On time
## 18:55  Bristol Temple Meads                    9     On time
## 18:59  London Paddington                       11    19:05
## 19:01  Plymouth                                7     On time
## 19:02  London Paddington                       10    On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
