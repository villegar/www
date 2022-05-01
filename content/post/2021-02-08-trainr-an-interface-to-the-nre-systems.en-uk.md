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

## Example (Last rendered on 2022-05-01 10:05)

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
## Reading (RDG) Station Board on 2022-05-01 10:05:21
## Time   From                                    Plat  Expected
## 10:56  Great Malvern                           11    11:09
## 11:01  London Paddington                       9     11:03
## 11:05  Bristol Temple Meads                    10    On time
## 11:08  Southampton Central                     7     On time
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       8B    On time
## 11:14  London Paddington                       14    On time
## 11:14  Swansea                                 11A   11:24
## 11:15  London Paddington                       12    On time
## 11:19  Bedwyn                                  1     11:36
## 11:26  London Paddington                       7     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Plymouth                                11A   On time
## 11:39  Manchester Piccadilly                   7     11:58
## 11:44  London Paddington                       14    On time
## 11:45  Swansea                                 11    On time
## 11:47  Salisbury                               1     On time
## 11:53  London Paddington                       9     On time
## 11:56  Great Malvern                           10    On time
## 11:58  Plymouth                                11    On time
## 12:01  London Paddington                       9     On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Didcot Parkway                          15    On time
## 12:12  London Paddington                       8     On time
## 12:14  London Paddington                       14    On time
## 12:15  London Paddington                       12    On time
## 12:19  Newbury                                 1     On time
## 12:25  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10    On time
## 12:33  Basingstoke                             2     On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:44  London Paddington                       14    On time
## 12:45  Swansea                                 10    On time
## 12:47  Salisbury                               1     On time
## 12:53  London Paddington                       9     On time
## 12:55  Penzance                                11    On time
## 12:56  Great Malvern                           10    On time
## 12:59  London Paddington                       -     Cancelled
## 11:07  Ascot                                   BUS   On time
## 11:21  Ascot                                   BUS   On time
## 11:22  North Camp                              BUS   On time
## 11:37  Ascot                                   BUS   On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 11:51  Ascot                                   BUS   On time
## 12:07  Ascot                                   BUS   On time
## 12:13  North Camp                              BUS   On time
## 12:21  Ascot                                   BUS   On time
## 12:27  North Camp                              BUS   On time
## 12:37  Ascot                                   BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
## 12:51  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-01 10:05:25
## Time   To                                      Plat  Expected
## 11:02  London Paddington                       11    11:10
## 11:10  Swansea                                 9     On time
## 11:12  Ealing Broadway                         15    On time
## 11:12  Salisbury                               1     On time
## 11:14  Great Malvern                           8B    On time
## 11:15  London Paddington                       10    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 11:18  London Paddington                       11A   11:25
## 11:26  Didcot Parkway                          12    On time
## 11:28  Plymouth                                7     On time
## 11:31  Ealing Broadway                         14    On time
## 11:38  Basingstoke                             2     On time
## 11:42  London Paddington                       11A   On time
## 11:44  Bedwyn                                  -     On time
## 11:48  London Paddington                       11    On time
## 11:52  Southampton Central                     7     11:59
## 11:54  Bristol Temple Meads                    9     On time
## 12:00  London Paddington                       11    On time
## 12:01  Ealing Broadway                         14    On time
## 12:02  London Paddington                       10    On time
## 12:10  Carmarthen                              9     On time
## 12:12  Ealing Broadway                         15    On time
## 12:12  Salisbury                               1     On time
## 12:15  London Paddington                       10    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 12:18  Hereford                                8     On time
## 12:26  Didcot Parkway                          12    On time
## 12:27  Penzance                                7     On time
## 12:31  Ealing Broadway                         14    On time
## 12:38  Basingstoke                             2     On time
## 12:40  London Paddington                       10    On time
## 12:44  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:55  Weston-super-Mare                       9     On time
## 13:00  London Paddington                       11    On time
## 13:01  Ealing Broadway                         14    On time
## 13:01  Paignton                                -     Cancelled
## 13:02  London Paddington                       10    On time
## 11:15  Ascot                                   BUS   On time
## 11:30  Ascot                                   BUS   On time
## 11:30  North Camp                              BUS   On time
## 11:45  Ascot                                   BUS   On time
## 11:45  North Camp                              BUS   On time
## 12:00  Ascot                                   BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 12:15  Ascot                                   BUS   On time
## 12:30  Ascot                                   BUS   On time
## 12:35  North Camp                              BUS   On time
## 12:45  Ascot                                   BUS   On time
## 13:00  Ascot                                   BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
