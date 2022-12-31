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

## Example (Last rendered on 2022-12-31 14:04)

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
## Reading (RDG) Station Board on 2022-12-31 14:04:59
## Time   From                                    Plat  Expected
## 13:55  London Paddington                       9     14:11
## 13:59  Plymouth                                11    On time
## 14:02  Didcot Parkway                          15A   13:59
## 14:05  Abbey Wood                              14    14:01
## 14:10  Bristol Temple Meads                    10    On time
## 14:11  London Paddington                       12B   On time
## 14:12  London Waterloo                         -     Cancelled
## 14:13  Swansea                                 11    On time
## 14:17  London Paddington                       9B    On time
## 14:20  Basingstoke                             2     On time
## 14:25  London Paddington                       9B    On time
## 14:25  Oxford                                  10A   On time
## 14:27  London Paddington                       7     On time
## 14:27  Newbury                                 11    On time
## 14:31  Didcot Parkway                          15A   On time
## 14:33  Abbey Wood                              14    On time
## 14:33  London Paddington                       7B    On time
## 14:33  Redhill                                 4     On time
## 14:39  Manchester Piccadilly                   7     On time
## 14:40  Weston-super-Mare                       10    On time
## 14:41  London Paddington                       9     On time
## 14:42  Newbury                                 1     On time
## 14:43  London Paddington                       12B   On time
## 14:45  London Waterloo                         4     On time
## 14:47  London Paddington                       9     On time
## 14:50  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         -     Cancelled
## 14:53  Worcester Foregate Street               10A   On time
## 14:55  London Paddington                       9     On time
## 14:58  London Paddington                       -     Cancelled
## 15:00  Penzance                                11    On time
## 15:01  Didcot Parkway                          15A   On time
## 15:03  Abbey Wood                              14    On time
## 15:06  Bournemouth                             7B    On time
## 15:10  Bristol Temple Meads                    10    On time
## 15:11  London Paddington                       12B   On time
## 15:13  Swansea                                 11    On time
## 15:15  London Waterloo                         4     On time
## 15:17  London Paddington                       -     Cancelled
## 15:20  Basingstoke                             2     On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10A   On time
## 15:27  London Paddington                       7     On time
## 15:28  Newbury                                 11    On time
## 15:31  Didcot Parkway                          15A   On time
## 15:33  Abbey Wood                              14    On time
## 15:33  London Paddington                       7B    On time
## 15:33  Redhill                                 5     On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Newbury                                 1     On time
## 15:40  Weston-super-Mare                       10    On time
## 15:41  London Paddington                       9     On time
## 15:43  London Paddington                       12B   On time
## 15:43  London Waterloo                         4     On time
## 15:46  Exeter St Davids                        -     Cancelled
## 15:47  London Paddington                       9B    On time
## 15:51  Basingstoke                             2     On time
## 15:51  Gatwick Airport                         4     On time
## 15:53  Hereford                                10    On time
## 15:55  London Paddington                       9     On time
## 16:03  Abbey Wood                              14    On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-31 14:05:03
## Time   To                                      Plat  Expected
## 13:57  Weston-super-Mare                       9     14:12
## 14:05  London Paddington                       11    On time
## 14:07  Basingstoke                             3     On time
## 14:07  London Waterloo                         6     On time
## 14:12  London Paddington                       10    On time
## 14:12  Newbury                                 1     On time
## 14:15  Ealing Broadway                         15A   On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  London Paddington                       11    On time
## 14:19  Great Malvern                           9B    On time
## 14:20  Redhill                                 5     On time
## 14:24  Abbey Wood                              14    On time
## 14:24  Didcot Parkway                          12B   On time
## 14:27  Bristol Temple Meads                    9B    On time
## 14:27  London Paddington                       10A   On time
## 14:29  Penzance                                7     On time
## 14:31  London Paddington                       11    On time
## 14:34  Newbury                                 7B    On time
## 14:37  Basingstoke                             2     On time
## 14:37  London Waterloo                         -     Cancelled
## 14:42  London Paddington                       10    On time
## 14:43  Swansea                                 9     On time
## 14:45  Ealing Broadway                         15A   On time
## 14:49  Oxford                                  9     On time
## 14:52  Bournemouth                             7     On time
## 14:53  Didcot Parkway                          12B   On time
## 14:54  Abbey Wood                              14    On time
## 14:56  London Paddington                       10A   On time
## 14:57  Bristol Temple Meads                    9     On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:01  Plymouth                                -     Cancelled
## 15:05  London Paddington                       11    On time
## 15:07  Basingstoke                             2     On time
## 15:07  London Waterloo                         5     On time
## 15:12  London Paddington                       10    On time
## 15:12  Newbury                                 1     On time
## 15:15  Ealing Broadway                         15A   On time
## 15:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 15:18  London Paddington                       11    On time
## 15:19  Great Malvern                           -     Cancelled
## 15:20  Redhill                                 4     On time
## 15:24  Abbey Wood                              14    On time
## 15:24  Didcot Parkway                          12B   On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       10A   On time
## 15:29  Penzance                                7     On time
## 15:32  London Paddington                       11    On time
## 15:34  Newbury                                 7B    On time
## 15:37  Basingstoke                             -     Cancelled
## 15:37  London Waterloo                         4     On time
## 15:43  London Paddington                       10    On time
## 15:43  Swansea                                 9     On time
## 15:45  Ealing Broadway                         15A   On time
## 15:48  London Paddington                       -     Cancelled
## 15:49  Oxford                                  9B    On time
## 15:53  Didcot Parkway                          12B   On time
## 15:54  Abbey Wood                              14    On time
## 15:56  Newbury                                 15    On time
## 15:57  Bristol Temple Meads                    9     On time
## 16:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
