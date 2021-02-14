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

## Example (Last rendered on 2021-02-14 14:07)

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
## Reading (RDG) Station Board on 2021-02-14 14:07:02
## Time   From                                    Plat  Expected
## 14:07  Gatwick Airport                         5     On time
## 14:07  London Paddington                       9     On time
## 14:09  Bristol Temple Meads                    10    14:06
## 14:12  Didcot Parkway                          15    On time
## 14:13  London Paddington                       14    14:06
## 14:15  London Paddington                       12    On time
## 14:17  Penzance                                11    15:12
## 14:18  London Paddington                       9B    On time
## 14:26  London Paddington                       7     14:35
## 14:32  London Waterloo                         4     On time
## 14:33  Basingstoke                             2     On time
## 14:35  Newbury                                 3     On time
## 14:39  Manchester Piccadilly                   13    On time
## 14:43  London Paddington                       14    On time
## 14:49  Basingstoke                             1     On time
## 14:49  Swansea                                 10    On time
## 14:53  London Paddington                       8     On time
## 14:56  Oxford                                  10A   On time
## 14:57  Penzance                                11    14:59
## 15:00  London Paddington                       -     Cancelled
## 15:02  London Waterloo                         4     On time
## 15:07  Gatwick Airport                         6     On time
## 15:07  London Paddington                       9     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:10  Eastleigh                               8B    On time
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       14    On time
## 15:15  London Paddington                       12    On time
## 15:18  London Paddington                       9     On time
## 15:21  Bedwyn                                  3     On time
## 15:26  London Paddington                       7     On time
## 15:32  London Waterloo                         4     On time
## 15:34  Basingstoke                             2     On time
## 15:39  Manchester Piccadilly                   8B    On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:43  London Paddington                       14    On time
## 15:45  Basingstoke                             1     On time
## 15:46  Swansea                                 11    On time
## 15:53  London Paddington                       9     On time
## 15:56  Oxford                                  10A   On time
## 16:02  London Waterloo                         4     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-14 14:07:04
## Time   To                                      Plat  Expected
## 14:09  Carmarthen                              9     On time
## 14:12  Basingstoke                             1     On time
## 14:13  Ealing Broadway                         15    On time
## 14:13  London Paddington                       10    On time
## 14:13  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 14:20  London Paddington                       11    15:13
## 14:20  Oxford                                  9B    On time
## 14:22  Ealing Broadway                         14    On time
## 14:24  London Waterloo                         4     On time
## 14:25  Didcot Parkway                          12    On time
## 14:27  Penzance                                7     14:36
## 14:38  Basingstoke                             2     On time
## 14:41  Gatwick Airport                         15    On time
##        via Guildford                           
## 14:42  Newbury                                 3     On time
## 14:50  London Paddington                       10    On time
## 14:52  Ealing Broadway                         14    On time
## 14:54  Bristol Temple Meads                    8     On time
## 14:54  London Waterloo                         4     On time
## 14:57  London Paddington                       11    15:00
## 15:00  London Paddington                       10A   On time
## 15:01  Exeter St Davids                        -     Cancelled
## 15:09  Swansea                                 9     On time
## 15:11  London Paddington                       11    On time
## 15:12  Basingstoke                             1     On time
## 15:14  Ealing Broadway                         15    On time
## 15:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 15:20  Oxford                                  9     On time
## 15:22  Ealing Broadway                         14    On time
## 15:24  London Waterloo                         4     On time
## 15:25  Didcot Parkway                          12    On time
## 15:27  Plymouth                                7     On time
## 15:35  Bedwyn                                  3     On time
## 15:39  Basingstoke                             2     On time
## 15:41  Gatwick Airport                         6     On time
##        via Guildford                           
## 15:43  London Paddington                       10    On time
## 15:50  London Paddington                       11    On time
## 15:52  Ealing Broadway                         14    On time
## 15:52  Eastleigh                               8B    On time
## 15:54  London Waterloo                         4     On time
## 15:54  Taunton                                 9     On time
## 16:00  London Paddington                       10A   On time
```
