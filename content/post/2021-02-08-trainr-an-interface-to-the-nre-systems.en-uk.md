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

## Example (Last rendered on 2021-05-12 08:24)

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
## Reading (RDG) Station Board on 2021-05-12 08:24:19
## Time   From                                    Plat  Expected
## 09:05  Bournemouth                             7B    On time
## 09:06  London Paddington                       8     Delayed
## 09:14  London Paddington                       12    On time
## 09:20  Swansea                                 -     Cancelled
## 09:27  Basingstoke                             12    On time
## 09:27  London Paddington                       -     Cancelled
## 09:28  London Paddington                       14    On time
## 09:29  Gatwick Airport                         15A   On time
## 09:30  Worcester Shrub Hill                    -     Cancelled
## 09:31  London Paddington                       -     Cancelled
## 09:34  Didcot Parkway                          15B   On time
## 09:39  Taunton                                 -     Cancelled
## 09:40  London Waterloo                         6     09:43
## 09:40  Nottingham                              7     09:42
## 09:43  London Paddington                       14    On time
## 09:45  Bristol Parkway                         10    10:21
## 09:49  Shalford                                15    On time
## 09:51  London Paddington                       -     Cancelled
## 09:53  London Paddington                       -     On time
## 09:54  Gatwick Airport                         4     On time
## 09:55  London Paddington                       -     Cancelled
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    -     Cancelled
## 10:00  London Paddington                       -     Cancelled
## 10:00  Penzance                                -     Cancelled
## 10:05  Didcot Parkway                          15    On time
## 10:06  Swansea                                 -     Cancelled
## 10:10  London Waterloo                         5     On time
## 10:11  Bedwyn                                  -     Cancelled
## 10:13  London Paddington                       14    On time
## 10:14  Bristol Temple Meads                    -     Cancelled
## 10:14  London Paddington                       12    On time
## 10:14  Swindon                                 -     On time
## 10:17  London Paddington                       -     Cancelled
## 10:19  Basingstoke                             2     On time
## 10:27  London Paddington                       -     Cancelled
## 10:28  Cheltenham Spa                          -     Cancelled
## 10:33  London Paddington                       -     Cancelled
## 10:35  Newbury                                 1     On time
## 10:39  Bristol Temple Meads                    -     Cancelled
## 10:39  Manchester Piccadilly                   7     On time
## 10:43  London Paddington                       14    On time
## 10:45  Carmarthen                              -     Cancelled
## 10:45  London Waterloo                         6     On time
## 10:48  Redhill                                 15B   On time
## 10:52  London Paddington                       -     Cancelled
## 10:53  Gatwick Airport                         5     On time
## 10:54  Great Malvern                           -     Cancelled
## 10:55  London Paddington                       -     Cancelled
## 10:57  London Paddington                       -     On time
## 10:57  Penzance                                -     Cancelled
## 10:59  London Paddington                       -     Cancelled
## 11:01  Didcot Parkway                          15    On time
## 11:06  Bournemouth                             8B    On time
## 11:10  London Waterloo                         4     On time
## 11:11  London Paddington                       -     Cancelled
## 11:13  London Paddington                       14    On time
## 11:14  Swindon                                 -     On time
## 11:16  London Paddington                       -     Cancelled
## 11:19  Basingstoke                             2     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-12 08:24:22
## Time   To                                      Plat  Expected
## 09:06  Swindon                                 8     Delayed
## 09:13  Manchester Piccadilly                   7B    Delayed
##        via Coventry & Stoke-on-Trent           
## 09:13  Newport (South Wales)                   9     09:38
## 09:21  London Paddington                       -     Cancelled
## 09:22  Ealing Broadway                         14    On time
## 09:23  Didcot Parkway                          12    On time
## 09:29  Plymouth                                -     Cancelled
## 09:33  London Paddington                       -     Cancelled
## 09:36  Bedwyn                                  -     Cancelled
## 09:42  London Paddington                       -     Cancelled
## 09:42  London Waterloo                         4     On time
## 09:52  Ealing Broadway                         14    On time
## 09:53  Cheltenham Spa                          -     Cancelled
## 09:53  Swindon                                 -     On time
## 09:57  London Paddington                       -     Cancelled
## 09:58  Bristol Temple Meads                    -     Cancelled
## 10:02  Paignton                                -     Cancelled
## 10:04  London Paddington                       -     Cancelled
## 10:05  Basingstoke                             2     On time
## 10:08  London Paddington                       -     Cancelled
## 10:12  London Paddington                       -     Cancelled
## 10:12  London Waterloo                         6     On time
## 10:12  Newbury                                 1     On time
## 10:13  Newport (South Wales)                   9     On time
## 10:14  London Paddington                       -     On time
## 10:15  Ealing Broadway                         15    On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:16  London Paddington                       -     Cancelled
## 10:19  Hereford                                -     Cancelled
## 10:20  Redhill                                 4     On time
## 10:22  Ealing Broadway                         14    On time
## 10:23  Didcot Parkway                          12    On time
## 10:29  Penzance                                -     Cancelled
## 10:34  London Paddington                       -     Cancelled
## 10:40  Bedwyn                                  -     Cancelled
## 10:42  London Paddington                       -     Cancelled
## 10:42  London Waterloo                         5     On time
## 10:48  London Paddington                       -     Cancelled
## 10:52  Bournemouth                             7     On time
## 10:52  Ealing Broadway                         14    On time
## 10:53  Cheltenham Spa                          -     Cancelled
## 10:57  London Paddington                       -     Cancelled
## 10:57  Swindon                                 -     On time
## 10:58  Bristol Temple Meads                    -     Cancelled
## 11:01  Exeter St Davids                        -     Cancelled
## 11:04  London Paddington                       -     Cancelled
## 11:07  Basingstoke                             2     On time
## 11:12  London Waterloo                         6     On time
## 11:12  Newbury                                 1     On time
## 11:13  Swansea                                 -     Cancelled
## 11:14  London Paddington                       -     On time
## 11:15  Ealing Broadway                         15    On time
## 11:16  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Shrub Hill                    -     Cancelled
## 11:20  Redhill                                 5     On time
## 11:22  Ealing Broadway                         14    On time
```
