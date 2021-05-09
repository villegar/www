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

## Example (Last rendered on 2021-05-09 12:10)

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
## Reading (RDG) Station Board on 2021-05-09 12:10:03
## Time   From                                    Plat  Expected
## 13:06  Bournemouth                             7     On time
## 13:10  Didcot Parkway                          15    On time
## 13:11  Didcot Parkway                          10    13:20
## 13:11  Weston-super-Mare                       -     Cancelled
## 13:14  London Paddington                       14    On time
## 13:15  Penzance                                11    On time
## 13:15  Slough                                  12    On time
## 13:17  London Paddington                       -     Cancelled
## 13:22  London Paddington                       -     On time
## 13:33  Basingstoke                             2     13:35
## 13:35  London Waterloo                         4     On time
## 13:38  Gatwick Airport                         5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:41  Bristol Temple Meads                    -     Cancelled
## 13:42  London Paddington                       14    On time
## 13:45  Salisbury                               1     On time
## 13:47  Swansea                                 -     Cancelled
## 13:50  London Paddington                       -     Cancelled
## 13:56  Worcester Shrub Hill                    10    On time
## 13:59  London Paddington                       -     Cancelled
## 14:05  London Waterloo                         4     On time
## 14:07  Redhill                                 15    On time
## 14:11  Didcot Parkway                          -     On time
## 14:12  Bristol Temple Meads                    -     Cancelled
## 14:12  Didcot Parkway                          15    On time
## 14:14  London Paddington                       14    On time
## 14:15  Slough                                  12    On time
## 14:17  London Paddington                       -     Cancelled
## 14:22  London Paddington                       -     On time
## 14:28  Penzance                                -     Cancelled
## 14:33  Basingstoke                             2     On time
## 14:35  London Waterloo                         4     On time
## 14:38  Gatwick Airport                         5     On time
## 14:39  Manchester Piccadilly                   13    On time
## 14:44  London Paddington                       14    On time
## 14:49  Salisbury                               1     On time
## 14:49  Swansea                                 -     Cancelled
## 14:53  London Paddington                       -     Cancelled
## 14:56  Worcester Foregate Street               10    On time
## 14:59  London Paddington                       -     Cancelled
## 15:05  London Waterloo                         4     On time
## 15:07  Redhill                                 6     On time
## 13:17  Newbury                                 BUS   On time
## 13:50  Newbury                                 BUS   On time
## 13:57  Bedwyn                                  BUS   On time
## 14:50  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-09 12:10:05
## Time   To                                      Plat  Expected
## 13:09  Swansea                                 9     13:25
## 13:12  London Paddington                       10    13:21
## 13:12  Salisbury                               1     On time
## 13:12  Slough                                  15    On time
## 13:13  London Paddington                       -     Cancelled
## 13:14  Worcester Foregate Street               13B   On time
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 13:16  London Paddington                       11    On time
## 13:17  Plymouth                                -     Cancelled
## 13:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:23  Didcot Parkway                          -     On time
## 13:24  London Waterloo                         4     On time
## 13:27  Didcot Parkway                          12    On time
## 13:31  Ealing Broadway                         14    On time
## 13:38  Basingstoke                             2     On time
## 13:41  Redhill                                 6     On time
## 13:42  London Paddington                       -     Cancelled
## 13:49  London Paddington                       -     Cancelled
## 13:51  Bristol Temple Meads                    -     Cancelled
## 13:52  Bournemouth                             7     On time
## 13:54  London Waterloo                         4     On time
## 14:01  Ealing Broadway                         14    On time
## 14:09  Carmarthen                              -     Cancelled
## 14:12  London Paddington                       -     On time
## 14:12  Salisbury                               1     On time
## 14:13  London Paddington                       -     Cancelled
## 14:13  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 14:13  Slough                                  15    On time
## 14:15  Worcester Shrub Hill                    8     On time
## 14:17  Penzance                                -     Cancelled
## 14:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:23  Didcot Parkway                          -     On time
## 14:24  London Waterloo                         4     On time
## 14:25  Didcot Parkway                          12    On time
## 14:30  London Paddington                       -     Cancelled
## 14:31  Ealing Broadway                         14    On time
## 14:38  Basingstoke                             2     On time
## 14:41  Redhill                                 15    On time
## 14:54  Bristol Temple Meads                    -     Cancelled
## 14:54  London Waterloo                         4     On time
## 14:58  London Paddington                       -     Cancelled
## 15:01  Ealing Broadway                         14    On time
## 15:09  Swansea                                 -     Cancelled
## 13:35  Bedwyn                                  BUS   On time
## 13:40  Newbury                                 BUS   On time
## 14:35  Newbury                                 BUS   On time
## 14:40  Newbury                                 BUS   On time
```
