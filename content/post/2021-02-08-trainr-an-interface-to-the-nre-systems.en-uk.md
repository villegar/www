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

## Example (Last rendered on 2022-11-20 12:09)

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
## Reading (RDG) Station Board on 2022-11-20 12:09:18
## Time   From                                    Plat  Expected
## 12:07  London Paddington                       9B    12:24
## 12:08  Redhill                                 6     12:13
## 12:09  Bristol Temple Meads                    10    12:15
## 12:10  Didcot Parkway                          15    On time
## 12:12  London Paddington                       8     On time
## 12:12  London Paddington                       14    On time
## 12:15  London Paddington                       12    Delayed
## 12:19  Newbury                                 1     On time
## 12:25  Oxford                                  10A   On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          11A   On time
## 12:35  Clapham Junction                        4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  Manchester Piccadilly                   15    On time
## 12:42  London Paddington                       14    On time
## 12:44  Swansea                                 10    On time
## 12:47  London Paddington                       9B    On time
## 12:53  London Paddington                       9     On time
## 12:55  Plymouth                                11    On time
## 12:56  Great Malvern                           10    On time
## 12:57  Bournemouth                             8     On time
## 13:01  London Paddington                       7     On time
## 13:05  Clapham Junction                        4     On time
## 13:07  London Paddington                       9     On time
## 13:08  Redhill                                 6     On time
## 13:09  Weston-super-Mare                       10    13:11
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       14    On time
## 13:12  London Paddington                       9     On time
## 13:16  London Paddington                       13    On time
## 13:17  Bedwyn                                  1     On time
## 13:21  Bristol Parkway                         10    On time
## 13:26  Exeter St Davids                        11    On time
## 13:26  London Paddington                       7     On time
## 13:26  Oxford                                  9     On time
## 13:35  Clapham Junction                        4     On time
## 13:38  Gatwick Airport                         5     On time
## 13:39  Manchester Piccadilly                   12    On time
## 13:40  Bristol Temple Meads                    10    On time
## 13:42  London Paddington                       14    On time
## 13:44  Swansea                                 11    On time
## 13:47  London Paddington                       8     On time
## 13:53  London Paddington                       9     On time
## 13:56  Great Malvern                           10    On time
## 13:58  Plymouth                                11    On time
## 14:05  Clapham Junction                        4     On time
## 14:08  Redhill                                 15    On time
## 12:20  Basingstoke                             BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 13:00  Winchester                              BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:20  Basingstoke                             BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-20 12:09:23
## Time   To                                      Plat  Expected
## 12:09  Carmarthen                              9B    12:25
## 12:14  Ealing Broadway                         15    On time
## 12:14  London Paddington                       10    12:16
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:18  Hereford                                8     On time
## 12:21  Clapham Junction                        4     On time
## 12:25  London Paddington                       10A   On time
## 12:26  Didcot Parkway                          12    Delayed
## 12:28  Plymouth                                7     On time
## 12:30  Ealing Broadway                         14    On time
## 12:39  Redhill                                 6     On time
## 12:42  London Paddington                       11A   On time
## 12:43  Newbury                                 1     On time
## 12:46  Bournemouth                             15    On time
## 12:46  London Paddington                       10    On time
## 12:49  Oxford                                  9B    On time
## 12:52  Clapham Junction                        4     On time
## 12:55  Weston-super-Mare                       9     On time
## 13:00  Ealing Broadway                         14    On time
## 13:00  London Paddington                       11    On time
## 13:02  Exeter St Davids                        7     On time
## 13:02  London Paddington                       10    On time
## 13:09  Swansea                                 9     On time
## 13:14  Ealing Broadway                         15    On time
## 13:14  Great Malvern                           9     On time
## 13:14  London Paddington                       10    On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:21  Clapham Junction                        4     On time
## 13:26  Didcot Parkway                          13    On time
## 13:26  London Paddington                       10    On time
## 13:28  London Paddington                       9     On time
## 13:28  Plymouth                                7     On time
## 13:30  Ealing Broadway                         14    On time
## 13:35  London Paddington                       11    On time
## 13:41  Redhill                                 6     On time
## 13:43  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:48  London Paddington                       11    On time
## 13:49  Oxford                                  8     On time
## 13:51  Clapham Junction                        4     On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:00  Ealing Broadway                         14    On time
## 14:00  London Paddington                       11    On time
## 14:02  London Paddington                       10    On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:38  Basingstoke                             BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:38  Basingstoke                             BUS   On time
## 13:52  Winchester                              BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
