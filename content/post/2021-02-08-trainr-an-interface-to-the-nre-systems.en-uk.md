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

## Example (Last rendered on 2021-05-09 20:09)

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
## Reading (RDG) Station Board on 2021-05-09 20:09:13
## Time   From                                    Plat  Expected
## 21:02  Plymouth                                -     Cancelled
## 21:07  Bournemouth                             7     On time
## 21:07  London Paddington                       -     Cancelled
## 21:07  Redhill                                 15B   On time
## 21:11  Didcot Parkway                          -     Delayed
## 21:11  London Paddington                       -     Cancelled
## 21:13  Didcot Parkway                          13    21:15
## 21:13  London Paddington                       14    21:06
## 21:14  London Paddington                       12    On time
## 21:16  Taunton                                 -     Cancelled
## 21:22  London Paddington                       -     21:24
## 21:26  London Paddington                       -     Cancelled
## 21:27  Penzance                                -     Cancelled
## 21:33  Basingstoke                             2     On time
## 21:35  London Waterloo                         6     On time
## 21:39  Gatwick Airport                         15    On time
## 21:39  Manchester Piccadilly                   7     On time
## 21:43  London Paddington                       14    On time
## 21:48  Swansea                                 -     Cancelled
## 21:53  London Paddington                       -     Cancelled
## 21:58  Hereford                                -     Cancelled
## 22:05  London Waterloo                         6     On time
## 22:06  London Paddington                       -     Cancelled
## 22:11  Didcot Parkway                          -     On time
## 22:13  Didcot Parkway                          13    On time
## 22:13  London Paddington                       14    On time
## 22:14  London Paddington                       12    On time
## 22:15  Weston-super-Mare                       -     Cancelled
## 22:22  London Paddington                       -     On time
## 22:33  Basingstoke                             13    On time
## 22:33  London Paddington                       14    On time
## 22:35  London Waterloo                         6     On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:45  Gatwick Airport                         13    On time
## 22:49  Carmarthen                              -     Cancelled
## 22:53  Worcester Shrub Hill                    10    On time
## 22:57  Penzance                                -     Cancelled
## 23:03  London Paddington                       10    On time
## 23:05  London Waterloo                         6     On time
## 21:17  Newbury                                 BUS   On time
## 21:57  Bedwyn                                  BUS   On time
## 23:03  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-09 20:09:16
## Time   To                                      Plat  Expected
## 21:09  Swansea                                 -     Cancelled
## 21:10  London Paddington                       -     Cancelled
## 21:12  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:12  London Paddington                       -     Delayed
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    21:16
## 21:14  Worcester Shrub Hill                    -     Cancelled
## 21:18  London Paddington                       -     Cancelled
## 21:23  Didcot Parkway                          -     21:25
## 21:24  London Waterloo                         4     On time
## 21:25  Ealing Broadway                         14    On time
## 21:27  Exeter St Davids                        -     Cancelled
## 21:29  London Paddington                       -     Cancelled
## 21:38  Basingstoke                             2     On time
## 21:50  London Paddington                       -     Cancelled
## 21:52  Southampton Central                     7     On time
## 21:54  Bristol Temple Meads                    -     Cancelled
## 21:54  London Waterloo                         6     On time
## 21:55  Ealing Broadway                         14    On time
## 22:09  Swansea                                 -     Cancelled
## 22:12  London Paddington                       -     On time
## 22:13  Worcester Shrub Hill                    9     On time
## 22:14  Didcot Parkway                          12    On time
## 22:14  Ealing Broadway                         13    On time
## 22:17  London Paddington                       -     Cancelled
## 22:23  Didcot Parkway                          -     On time
## 22:24  London Waterloo                         6     On time
## 22:25  Ealing Broadway                         14    On time
## 22:50  London Paddington                       -     Cancelled
## 22:54  London Waterloo                         6     On time
## 22:55  Ealing Broadway                         14    On time
## 23:02  London Paddington                       -     Cancelled
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:50  Bedwyn                                  BUS   On time
## 22:44  Newbury                                 BUS   On time
```
