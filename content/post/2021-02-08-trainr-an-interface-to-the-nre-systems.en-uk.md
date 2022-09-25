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

## Example (Last rendered on 2022-09-25 10:05)

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
## Reading (RDG) Station Board on 2022-09-25 10:05:10
## Time   From                                    Plat  Expected
## 09:31  Bristol Parkway                         -     10:47
## 10:57  London Paddington                       -     Cancelled
## 11:03  London Waterloo                         4     On time
## 11:05  Bournemouth                             8     11:07
## 11:05  Bristol Temple Meads                    10    11:23
## 11:08  London Paddington                       14    On time
## 11:10  Didcot Parkway                          15    On time
## 11:14  Cardiff Central                         11    On time
## 11:17  Slough                                  13    Delayed
## 11:19  Bedwyn                                  1     On time
## 11:26  London Paddington                       7     On time
## 11:32  London Waterloo                         4     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Plymouth                                11    On time
## 11:38  London Paddington                       14    On time
## 11:39  Didcot Parkway                          7     On time
## 11:44  Bridgend                                -     Cancelled
## 11:47  Salisbury                               1     On time
## 11:54  London Paddington                       8     On time
## 11:58  Plymouth                                11    On time
## 12:00  Didcot Parkway                          10    On time
## 12:00  London Paddington                       9     On time
## 12:02  London Waterloo                         4     On time
## 12:08  London Paddington                       14    On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Didcot Parkway                          15    On time
## 12:17  London Paddington                       12    On time
## 12:19  Newbury                                 1     On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          -     Cancelled
## 12:32  London Waterloo                         4     On time
## 12:33  Basingstoke                             2     On time
## 12:38  London Paddington                       14    On time
## 12:39  Didcot Parkway                          12    On time
## 12:44  Bridgend                                -     Cancelled
## 12:47  Salisbury                               1     On time
## 12:54  London Paddington                       8     On time
## 12:55  Penzance                                11    On time
## 12:57  London Paddington                       -     Cancelled
## 13:00  Didcot Parkway                          10    On time
## 13:02  London Waterloo                         4     On time
## 11:18  Guildford                               BUS   On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:04  Guildford                               -     Cancelled
## 12:40  Guildford                               -     Cancelled
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-25 10:05:15
## Time   To                                      Plat  Expected
## 11:01  Paignton                                -     Cancelled
## 11:04  Ealing Broadway                         14    On time
## 11:09  Swansea                                 9     On time
## 11:12  Salisbury                               1     On time
## 11:15  Didcot Parkway                          8     On time
## 11:15  London Paddington                       10    11:24
## 11:17  London Paddington                       11    On time
## 11:20  Didcot Parkway                          13    Delayed
## 11:24  London Waterloo                         4     On time
## 11:28  Didcot Parkway                          15    On time
## 11:28  Plymouth                                7     On time
## 11:34  Ealing Broadway                         14    On time
## 11:35  London Paddington                       11    On time
## 11:38  Basingstoke                             2     On time
## 11:43  Bedwyn                                  1     On time
## 11:45  London Paddington                       -     Cancelled
## 11:52  Bournemouth                             7     On time
## 11:54  London Waterloo                         4     On time
## 11:56  Bristol Temple Meads                    8     On time
## 12:00  London Paddington                       11    On time
## 12:02  London Paddington                       10    On time
## 12:04  Ealing Broadway                         14    On time
## 12:09  Carmarthen                              9     On time
## 12:12  Salisbury                               1     On time
## 12:15  Didcot Parkway                          15    On time
## 12:15  London Paddington                       10    On time
## 12:20  Didcot Parkway                          12    On time
## 12:24  London Waterloo                         4     On time
## 12:28  Didcot Parkway                          15    On time
## 12:28  Penzance                                7     On time
## 12:33  London Paddington                       -     Cancelled
## 12:34  Ealing Broadway                         14    On time
## 12:38  Basingstoke                             2     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       -     Cancelled
## 12:54  London Waterloo                         4     On time
## 12:56  Bristol Temple Meads                    8     On time
## 13:00  London Paddington                       11    On time
## 13:01  Paignton                                -     Cancelled
## 13:02  London Paddington                       10    On time
## 13:04  Ealing Broadway                         14    On time
## 11:23  Guildford                               -     Cancelled
## 11:56  Guildford                               BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 12:45  Guildford                               -     Cancelled
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
