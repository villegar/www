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

## Example (Last rendered on 2022-05-01 12:05)

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
## Reading (RDG) Station Board on 2022-05-01 12:05:07
## Time   From                                    Plat  Expected
## 12:56  Great Malvern                           15A   On time
## 12:59  London Paddington                       -     Cancelled
## 13:01  London Paddington                       9     13:12
## 13:06  Southampton Central                     7     On time
## 13:10  Didcot Parkway                          15    On time
## 13:10  Weston-super-Mare                       10    13:17
## 13:12  London Paddington                       8B    On time
## 13:14  London Paddington                       14    On time
## 13:15  London Paddington                       13    On time
## 13:17  Bedwyn                                  1     On time
## 13:26  London Paddington                       7     On time
## 13:26  Paignton                                11    On time
## 13:33  Basingstoke                             2     On time
## 13:39  Manchester Piccadilly                   7     13:41
## 13:40  Bristol Temple Meads                    10    On time
## 13:44  London Paddington                       14    On time
## 13:45  Swansea                                 11    On time
## 13:47  Salisbury                               1     On time
## 13:53  London Paddington                       9     On time
## 13:56  Great Malvern                           10A   On time
## 13:58  Penzance                                11    On time
## 14:01  London Paddington                       9     On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:10  Didcot Parkway                          13    On time
## 14:12  London Paddington                       8     On time
## 14:14  London Paddington                       14    On time
## 14:17  London Paddington                       13    On time
## 14:19  Newbury                                 1     On time
## 14:26  London Paddington                       7     On time
## 14:33  Basingstoke                             2     On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:44  London Paddington                       14    On time
## 14:45  Swansea                                 10    On time
## 14:49  Salisbury                               1     On time
## 14:53  London Paddington                       9     On time
## 14:56  Hereford                                10    On time
## 14:57  Penzance                                11    On time
## 14:59  London Paddington                       -     Cancelled
## 13:07  Ascot                                   BUS   On time
## 13:21  Ascot                                   BUS   On time
## 13:22  North Camp                              BUS   On time
## 13:37  Ascot                                   BUS   On time
## 13:45  Heathrow Central Bus Stn                BUS   On time
## 13:51  Ascot                                   BUS   On time
## 14:07  Ascot                                   BUS   On time
## 14:13  North Camp                              BUS   On time
## 14:21  Ascot                                   BUS   On time
## 14:27  North Camp                              BUS   On time
## 14:37  Ascot                                   BUS   On time
## 14:45  Heathrow Central Bus Stn                BUS   On time
## 14:51  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-01 12:05:11
## Time   To                                      Plat  Expected
## 13:01  Paignton                                -     Cancelled
## 13:02  London Paddington                       15A   On time
## 13:10  Swansea                                 9     13:13
## 13:12  Ealing Broadway                         15    On time
## 13:12  Salisbury                               1     On time
## 13:14  Great Malvern                           8B    On time
## 13:15  London Paddington                       10    13:18
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 13:26  Didcot Parkway                          13    On time
## 13:29  Plymouth                                7     On time
## 13:31  Ealing Broadway                         14    On time
## 13:38  Basingstoke                             2     On time
## 13:40  London Paddington                       11    On time
## 13:44  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:48  London Paddington                       11    On time
## 13:52  Southampton Central                     7     On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:00  London Paddington                       11    On time
## 14:01  Ealing Broadway                         14    On time
## 14:02  London Paddington                       10A   On time
## 14:10  Carmarthen                              9     On time
## 14:12  Ealing Broadway                         13    On time
## 14:12  Salisbury                               1     On time
## 14:14  Hereford                                8     On time
## 14:15  London Paddington                       10    On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 14:25  Didcot Parkway                          13    On time
## 14:28  Penzance                                7     On time
## 14:31  Ealing Broadway                         14    On time
## 14:38  Basingstoke                             2     On time
## 14:44  Newbury                                 1     On time
## 14:48  London Paddington                       10    On time
## 14:54  Taunton                                 9     On time
## 15:00  London Paddington                       11    On time
## 15:01  Ealing Broadway                         14    On time
## 15:02  London Paddington                       10    On time
## 15:03  Exeter St Davids                        -     Cancelled
## 13:15  Ascot                                   BUS   On time
## 13:30  Ascot                                   BUS   On time
## 13:30  North Camp                              BUS   On time
## 13:45  Ascot                                   BUS   On time
## 13:45  North Camp                              BUS   On time
## 14:00  Ascot                                   BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
## 14:15  Ascot                                   BUS   On time
## 14:30  Ascot                                   BUS   On time
## 14:35  North Camp                              BUS   On time
## 14:45  Ascot                                   BUS   On time
## 15:00  Ascot                                   BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
```
