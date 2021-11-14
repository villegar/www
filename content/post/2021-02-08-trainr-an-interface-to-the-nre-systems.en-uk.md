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

## Example (Last rendered on 2021-11-14 14:03)

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
## Reading (RDG) Station Board on 2021-11-14 14:03:43
## Time   From                                    Plat  Expected
## 13:55  Great Malvern                           15A   14:07
## 13:58  Plymouth                                11    Delayed
## 14:06  London Paddington                       9     14:09
## 14:09  Bristol Temple Meads                    11    On time
## 14:10  Didcot Parkway                          14    On time
## 14:12  London Paddington                       8     14:17
## 14:12  London Paddington                       13    14:24
## 14:19  Newbury                                 1     On time
## 14:22  London Paddington                       12    On time
## 14:22  London Waterloo                         6     On time
## 14:26  London Paddington                       7     On time
## 14:33  Basingstoke                             2     On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:44  London Paddington                       14    On time
## 14:44  Swansea                                 11    14:47
## 14:50  London Paddington                       9     On time
## 14:52  London Waterloo                         4     On time
## 14:57  Plymouth                                11    On time
## 14:58  Worcester Shrub Hill                    10    On time
## 15:01  London Paddington                       -     Cancelled
## 15:06  London Paddington                       9     On time
## 15:07  Eastleigh                               8     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:12  London Paddington                       9     On time
## 15:12  London Paddington                       14    On time
## 15:13  Didcot Parkway                          15    On time
## 15:19  Bedwyn                                  3     On time
## 15:22  London Waterloo                         6     On time
## 15:23  London Paddington                       12    On time
## 15:26  London Paddington                       7     On time
## 15:33  Basingstoke                             2     On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:43  Swansea                                 11    On time
## 15:44  London Paddington                       14    On time
## 15:50  London Paddington                       9     On time
## 15:52  London Waterloo                         4     On time
## 15:58  Exeter St Davids                        -     Cancelled
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 14:43  Guildford                               BUS   On time
## 15:13  Guildford                               BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
## 15:54  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-14 14:03:46
## Time   To                                      Plat  Expected
## 14:00  London Paddington                       11    Delayed
## 14:05  London Paddington                       15A   14:08
## 14:09  Carmarthen                              9     14:10
## 14:11  Ealing Broadway                         14    On time
## 14:12  London Paddington                       11    On time
## 14:14  Hereford                                8     14:18
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 14:21  London Waterloo                         4     On time
## 14:22  Ealing Broadway                         13    Delayed
## 14:26  Didcot Parkway                          12    On time
## 14:29  Plymouth                                7     On time
## 14:38  Basingstoke                             2     On time
## 14:44  Newbury                                 1     On time
## 14:46  London Paddington                       11    14:48
## 14:51  London Waterloo                         6     On time
## 14:52  Ealing Broadway                         14    On time
## 14:55  Bristol Temple Meads                    9     On time
## 15:00  London Paddington                       11    On time
## 15:03  Exeter St Davids                        -     Cancelled
## 15:05  London Paddington                       10    On time
## 15:09  Swansea                                 9     On time
## 15:12  London Paddington                       11    On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           9     On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:21  London Waterloo                         4     On time
## 15:22  Ealing Broadway                         14    On time
## 15:25  Didcot Parkway                          12    On time
## 15:29  Plymouth                                7     On time
## 15:38  Basingstoke                             2     On time
## 15:42  London Paddington                       10    On time
## 15:44  Bedwyn                                  3     On time
## 15:46  London Paddington                       11    On time
## 15:51  Ealing Broadway                         14    On time
## 15:51  London Waterloo                         6     On time
## 15:52  Eastleigh                               7     On time
## 15:55  Taunton                                 9     On time
## 16:00  London Paddington                       -     Cancelled
## 14:05  Guildford                               BUS   On time
## 14:45  Guildford                               BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:30  Guildford                               BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
