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

## Example (Last rendered on 2021-02-14 18:07)

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
## Reading (RDG) Station Board on 2021-02-14 18:07:42
## Time   From                                    Plat  Expected
## 18:02  London Waterloo                         4     18:07
## 18:07  Gatwick Airport                         6     18:10
## 18:07  London Paddington                       9     On time
## 18:09  Bristol Temple Meads                    10A   On time
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       14    18:07
## 18:14  Plymouth                                11A   On time
## 18:15  London Paddington                       12    On time
## 18:18  London Paddington                       9B    On time
## 18:23  London Paddington                       9B    On time
## 18:26  London Paddington                       7     On time
## 18:32  Basingstoke                             2     On time
## 18:32  London Waterloo                         4     18:34
## 18:35  Newbury                                 1     On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:40  Bristol Temple Meads                    10A   On time
## 18:43  London Paddington                       14    On time
## 18:44  Swansea                                 11    On time
## 18:53  London Paddington                       8B    On time
## 18:55  Oxford                                  10A   On time
## 18:58  Penzance                                11    On time
## 19:02  London Waterloo                         4     On time
## 19:07  Gatwick Airport                         5     On time
## 19:07  London Paddington                       9     On time
## 19:09  Eastleigh                               8B    On time
## 19:10  Paignton                                10    On time
## 19:13  London Paddington                       14    On time
## 19:14  Didcot Parkway                          15    On time
## 19:15  London Paddington                       12    On time
## 19:18  London Paddington                       9B    On time
## 19:21  Bedwyn                                  1     On time
## 19:28  London Paddington                       9B    On time
## 19:32  London Waterloo                         6     On time
## 19:33  Basingstoke                             2     On time
## 19:38  Exeter St Davids                        -     Cancelled
## 19:39  Manchester Piccadilly                   8B    On time
## 19:40  Bristol Temple Meads                    10    On time
## 19:43  London Paddington                       14    On time
## 19:46  London Paddington                       9B    On time
## 19:48  Carmarthen                              10    On time
## 19:53  London Paddington                       9     On time
## 19:57  Oxford                                  10A   On time
## 19:59  Penzance                                11    On time
## 20:02  London Waterloo                         4     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-14 18:07:45
## Time   To                                      Plat  Expected
## 18:09  Swansea                                 9     On time
## 18:14  Ealing Broadway                         15    On time
## 18:15  London Paddington                       10A   On time
## 18:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 18:18  London Paddington                       11A   On time
## 18:20  Oxford                                  9B    On time
## 18:22  Ealing Broadway                         14    On time
## 18:24  London Waterloo                         4     On time
## 18:24  Plymouth                                9B    On time
##        via Bristol                             
## 18:25  Didcot Parkway                          12    On time
## 18:27  Penzance                                7     On time
## 18:38  Basingstoke                             2     On time
## 18:40  London Paddington                       10A   On time
## 18:41  Redhill                                 6     On time
## 18:46  London Paddington                       11    On time
## 18:50  Newbury                                 1     On time
## 18:52  Ealing Broadway                         14    On time
## 18:54  London Waterloo                         4     On time
## 18:54  Weston-super-Mare                       8B    On time
## 18:58  London Paddington                       11    On time
## 19:00  London Paddington                       10A   On time
## 19:08  Swansea                                 9     On time
## 19:13  London Paddington                       10    On time
## 19:14  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:20  Oxford                                  9B    On time
## 19:22  Ealing Broadway                         14    On time
## 19:24  London Waterloo                         4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:30  Hereford                                9B    On time
## 19:35  Bedwyn                                  1     On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       -     Cancelled
## 19:45  London Paddington                       10    On time
## 19:47  Oxford                                  9B    On time
## 19:50  London Paddington                       10    On time
## 19:52  Ealing Broadway                         14    On time
## 19:52  Eastleigh                               8B    On time
## 19:54  Bristol Temple Meads                    9     On time
## 19:54  London Waterloo                         6     On time
## 19:59  London Paddington                       11    On time
## 20:01  London Paddington                       10A   On time
```
