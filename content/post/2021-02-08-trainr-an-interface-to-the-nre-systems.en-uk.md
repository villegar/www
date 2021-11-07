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

## Example (Last rendered on 2021-11-07 14:03)

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
## Reading (RDG) Station Board on 2021-11-07 14:03:39
## Time   From                                    Plat  Expected
## 13:58  Penzance                                11    14:00
## 14:07  London Paddington                       9     On time
## 14:08  London Waterloo                         4     On time
## 14:09  Bristol Temple Meads                    10A   On time
## 14:10  Didcot Parkway                          14    On time
## 14:12  London Paddington                       9     On time
## 14:12  Redhill                                 15    On time
## 14:14  London Paddington                       13    On time
## 14:19  Newbury                                 1     On time
## 14:24  London Paddington                       12    On time
## 14:28  London Paddington                       7     On time
## 14:35  London Waterloo                         4     On time
## 14:39  Redhill                                 5     On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:43  Swansea                                 11    On time
## 14:44  London Paddington                       14    On time
## 14:53  London Paddington                       9     On time
## 14:55  Bournemouth                             13    On time
## 14:57  Penzance                                11    14:59
## 14:58  Hereford                                10    On time
## 15:00  London Paddington                       7     On time
## 15:05  London Waterloo                         4     On time
## 15:07  London Paddington                       9     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:11  Redhill                                 6     On time
## 15:12  London Paddington                       8     On time
## 15:13  Didcot Parkway                          15    On time
## 15:14  London Paddington                       14    On time
## 15:19  Bedwyn                                  3     On time
## 15:23  London Paddington                       12    On time
## 15:26  London Paddington                       7     On time
## 15:35  London Waterloo                         4     On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:39  Redhill                                 5     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:44  London Paddington                       14    On time
## 15:44  Swansea                                 11    On time
## 15:53  Hereford                                15    On time
## 15:53  London Paddington                       9     On time
## 15:58  Exeter St Davids                        11    On time
## 14:18  Basingstoke                             BUS   On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 15:00  Basingstoke                             BUS   On time
## 15:18  Bramley (Hampshire)                     BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-07 14:03:42
## Time   To                                      Plat  Expected
## 14:00  London Paddington                       11    14:02
## 14:09  Carmarthen                              9     On time
## 14:12  Ealing Broadway                         14    On time
## 14:14  Hereford                                9     On time
## 14:15  London Paddington                       10A   On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Redhill                                 5     On time
## 14:21  London Waterloo                         4     On time
## 14:28  Didcot Parkway                          12    On time
## 14:29  Penzance                                7     On time
## 14:30  Ealing Broadway                         13    On time
## 14:38  Redhill                                 5     On time
## 14:44  Newbury                                 1     On time
## 14:45  London Paddington                       11    On time
## 14:46  Bournemouth                             13    On time
## 14:51  London Waterloo                         4     On time
## 14:55  Bristol Temple Meads                    9     On time
## 14:59  London Paddington                       10    On time
## 14:59  London Paddington                       11    14:59
## 15:00  Ealing Broadway                         14    On time
## 15:03  Exeter St Davids                        7     On time
## 15:09  Swansea                                 9     On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           8     On time
## 15:15  London Paddington                       11    On time
## 15:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 15:18  Redhill                                 5     On time
## 15:21  London Waterloo                         4     On time
## 15:25  Didcot Parkway                          12    On time
## 15:27  Plymouth                                7     On time
## 15:30  Ealing Broadway                         14    On time
## 15:41  Redhill                                 6     On time
## 15:44  Bedwyn                                  3     On time
## 15:45  London Paddington                       10    On time
## 15:50  London Paddington                       11    On time
## 15:51  London Waterloo                         4     On time
## 15:55  London Paddington                       15    On time
## 15:55  Taunton                                 9     On time
## 16:00  Ealing Broadway                         14    On time
## 16:00  London Paddington                       11    On time
## 14:38  Basingstoke                             BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:38  Bramley (Hampshire)                     BUS   On time
## 15:52  Basingstoke                             BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
