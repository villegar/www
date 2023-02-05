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

## Example (Last rendered on 2023-02-05 10:03)

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
## Reading (RDG) Station Board on 2023-02-05 10:03:12
## Time   From                                    Plat  Expected
## 09:05  Bristol Temple Meads                    11    10:29
## 09:18  London Paddington                       7     Delayed
## 09:26  London Paddington                       7     10:25
## 09:38  London Paddington                       7     10:14
## 09:58  Didcot Parkway                          15    On time
## 10:04  Worcester Foregate Street               11    On time
## 10:06  Southampton Central                     12B   On time
## 10:12  London Paddington                       9     10:15
## 10:16  London Paddington                       13    On time
## 10:18  Bedwyn                                  -     Cancelled
## 10:18  London Paddington                       7     Delayed
## 10:21  Weston-super-Mare                       11    Delayed
## 10:26  London Paddington                       7     Delayed
## 10:28  London Paddington                       14    On time
## 10:32  Basingstoke                             2     10:47
## 10:36  Exeter St Davids                        11    10:50
## 10:38  London Paddington                       7     Delayed
## 10:39  Birmingham New Street                   13    On time
## 10:47  London Paddington                       9     On time
## 10:47  Salisbury                               1     On time
## 10:50  Swansea                                 11    Delayed
## 10:57  London Paddington                       7     Delayed
## 10:58  London Paddington                       14    On time
## 11:06  Bournemouth                             8     On time
## 11:06  Great Malvern                           10    On time
## 11:12  London Paddington                       9     On time
## 11:13  Didcot Parkway                          15    On time
## 11:15  London Paddington                       12    On time
## 11:18  London Paddington                       7     Delayed
## 11:19  Bedwyn                                  1     On time
## 11:23  Bristol Temple Meads                    11    On time
## 11:28  London Paddington                       14    On time
## 11:29  Oxford                                  10    On time
## 11:33  Basingstoke                             2     On time
## 11:34  Plymouth                                11    On time
## 11:38  London Paddington                       7     Delayed
## 11:39  Manchester Piccadilly                   8     On time
## 11:39  Swansea                                 10    On time
## 11:47  London Paddington                       9     On time
## 11:47  Salisbury                               1     On time
## 11:58  London Paddington                       14    On time
## 11:58  Plymouth                                11    On time
## 10:03  Bracknell                               BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:12  North Camp                              BUS   On time
## 10:19  Bracknell                               BUS   On time
## 10:32  North Camp                              BUS   On time
## 10:33  Bracknell                               BUS   On time
## 10:34  Chippenham                              BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:49  Bracknell                               BUS   On time
## 11:00  Swindon                                 BUS   On time
## 11:03  Bracknell                               BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:19  Bracknell                               BUS   On time
## 11:27  North Camp                              BUS   On time
## 11:33  Bracknell                               BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 11:49  Bracknell                               BUS   On time
## 11:50  Chippenham                              BUS   On time
## 12:00  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-05 10:03:18
## Time   To                                      Plat  Expected
## 09:19  Penzance                                7     Delayed
## 09:28  Carmarthen                              7     10:26
## 09:42  Bristol Temple Meads                    7     10:15
## 09:45  Bedwyn                                  12B   Delayed
## 10:10  London Paddington                       11    On time
## 10:12  Salisbury                               10    On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Wilmslow                 
## 10:19  Swansea                                 7     Delayed
## 10:20  Hereford                                9     On time
## 10:23  Ealing Broadway                         14    On time
## 10:25  London Paddington                       11    Delayed
## 10:26  Didcot Parkway                          13    On time
## 10:28  Penzance                                7     Delayed
## 10:37  Basingstoke                             2     On time
## 10:42  Bristol Temple Meads                    7     Delayed
## 10:42  London Paddington                       11    10:51
## 10:45  Newbury                                 3     On time
## 10:52  Oxford                                  9     On time
## 10:53  Ealing Broadway                         14    On time
## 10:55  London Paddington                       11    Delayed
## 11:02  Paignton                                7     Delayed
## 11:10  London Paddington                       10    On time
## 11:12  Salisbury                               1     On time
## 11:14  Ealing Broadway                         15    On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 11:19  Carmarthen                              7     Delayed
## 11:20  Great Malvern                           9     On time
## 11:23  Ealing Broadway                         14    On time
## 11:25  London Paddington                       11    On time
## 11:26  Didcot Parkway                          12    On time
## 11:28  Plymouth                                7     On time
## 11:32  London Paddington                       10    On time
## 11:37  Basingstoke                             2     On time
## 11:40  London Paddington                       11    On time
## 11:42  Bristol Temple Meads                    7     Delayed
## 11:43  London Paddington                       10    On time
## 11:45  Bedwyn                                  1     On time
## 11:52  Bournemouth                             8     On time
## 11:52  Oxford                                  9     On time
## 11:53  Ealing Broadway                         14    On time
## 12:02  London Paddington                       11    12:07
## 10:05  Bracknell                               BUS   On time
## 10:08  Swindon                                 BUS   On time
## 10:18  Chippenham                              BUS   On time
## 10:21  Bracknell                               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:35  Bracknell                               BUS   On time
## 10:35  North Camp                              BUS   On time
## 10:51  Bracknell                               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:05  Bracknell                               BUS   On time
## 11:05  Swindon                                 BUS   On time
## 11:15  Chippenham                              BUS   On time
## 11:21  Bracknell                               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  North Camp                              BUS   On time
## 11:35  Bracknell                               BUS   On time
## 11:45  North Camp                              BUS   On time
## 11:51  Bracknell                               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
