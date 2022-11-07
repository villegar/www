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

## Example (Last rendered on 2022-11-07 20:10)

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
## Reading (RDG) Station Board on 2022-11-07 20:10:23
## Time   From                                    Plat  Expected
## 20:13  Didcot Parkway                          15    19:57
## 20:13  London Paddington                       9     On time
## 20:14  Abbey Wood                              14    20:10
## 20:19  London Paddington                       9     On time
## 20:23  London Paddington                       12    On time
## 20:29  London Paddington                       7     On time
## 20:34  Basingstoke                             2     On time
## 20:35  Redhill                                 5     On time
## 20:36  Cheltenham Spa                          -     Cancelled
## 20:43  Abbey Wood                              14    On time
## 20:45  Didcot Parkway                          15    On time
## 20:47  Swansea                                 10    20:54
## 20:51  London Paddington                       12    On time
## 20:53  Gatwick Airport                         5     On time
## 20:54  Great Malvern                           11    20:56
## 20:57  London Paddington                       9     On time
## 21:03  Exeter St Davids                        11    Delayed
## 21:10  London Paddington                       14    On time
## 21:11  Bristol Temple Meads                    10    21:13
## 21:13  Abbey Wood                              13    On time
## 21:18  London Paddington                       9     On time
## 21:28  Basingstoke                             2     On time
## 21:29  Redhill                                 5     On time
## 21:37  Didcot Parkway                          15    On time
## 21:42  Abbey Wood                              14    On time
## 21:43  Cheltenham Spa                          -     Cancelled
## 21:46  Swansea                                 10    21:48
## 21:49  London Paddington                       12    On time
## 21:56  Gatwick Airport                         5     On time
## 21:56  Great Malvern                           10A   21:59
## 21:57  Basingstoke                             2     On time
## 22:05  Exeter St Davids                        11    On time
## 22:07  London Paddington                       14    On time
## 22:08  Didcot Parkway                          10    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 20:10:27
## Time   To                                      Plat  Expected
## 20:13  London Paddington                       15    On time
## 20:13  Swansea                                 9     On time
## 20:19  Hereford                                9     On time
## 20:20  Shalford                                4     On time
## 20:21  Basingstoke                             3     On time
## 20:23  Didcot Parkway                          12    On time
## 20:27  Abbey Wood                              14    On time
## 20:29  Exeter St Davids                        7     On time
## 20:36  London Paddington                       -     Cancelled
## 20:45  London Paddington                       15    On time
## 20:47  London Paddington                       10    20:54
## 20:51  Didcot Parkway                          12    On time
## 20:52  Basingstoke                             2     On time
## 20:56  London Paddington                       11    On time
## 20:57  Abbey Wood                              14    On time
## 20:57  Bristol Temple Meads                    9     On time
## 21:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 21:03  London Paddington                       11    Delayed
## 21:11  London Paddington                       10    21:13
## 21:18  Great Malvern                           9     On time
## 21:27  Abbey Wood                              13    On time
## 21:34  Gatwick Airport                         4     On time
##        via Guildford                           
## 21:37  London Paddington                       15    On time
## 21:43  London Paddington                       -     Cancelled
## 21:46  London Paddington                       10    21:48
## 21:49  Didcot Parkway                          12    On time
## 21:56  London Paddington                       10A   21:59
## 21:57  Abbey Wood                              14    On time
## 22:05  Basingstoke                             2     On time
## 22:05  London Paddington                       11    On time
## 22:08  London Paddington                       10    On time
```
