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

## Example (Last rendered on 2023-02-05 14:03)

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
## Reading (RDG) Station Board on 2023-02-05 14:03:21
## Time   From                                    Plat  Expected
## 13:58  Penzance                                11    14:12
## 14:06  Great Malvern                           -     Cancelled
## 14:10  Didcot Parkway                          15    On time
## 14:12  London Paddington                       9     14:22
## 14:14  London Paddington                       13    On time
## 14:18  London Paddington                       7     Delayed
## 14:20  Newbury                                 1     On time
## 14:23  Bristol Temple Meads                    11    On time
## 14:26  London Paddington                       7     On time
## 14:28  London Paddington                       14    On time
## 14:29  Oxford                                  10    On time
## 14:32  Basingstoke                             2     On time
## 14:35  Swansea                                 11    14:38
## 14:38  London Paddington                       -     Cancelled
## 14:39  Manchester Piccadilly                   13    On time
## 14:47  London Paddington                       9     On time
## 14:49  Salisbury                               1     On time
## 14:57  London Paddington                       7     On time
## 14:57  Penzance                                11    On time
## 14:58  London Paddington                       14    On time
## 15:06  Bournemouth                             8     On time
## 15:06  Hereford                                10    On time
## 15:12  London Paddington                       9     On time
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       12    On time
## 15:18  Bedwyn                                  3     On time
## 15:18  London Paddington                       7     On time
## 15:23  Bristol Temple Meads                    11    15:45
## 15:26  London Paddington                       7     On time
## 15:28  London Paddington                       14    On time
## 15:29  Oxford                                  10    On time
## 15:32  Basingstoke                             2     On time
## 15:38  Exeter St Davids                        11    On time
## 15:38  London Paddington                       7     On time
## 15:39  Manchester Piccadilly                   8     On time
## 15:43  Carmarthen                              10    15:47
## 15:47  London Paddington                       9     On time
## 15:47  Salisbury                               1     On time
## 15:58  Exeter St Davids                        -     Cancelled
## 15:58  London Paddington                       14    On time
## 14:03  Bracknell                               BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:12  North Camp                              BUS   On time
## 14:19  Bracknell                               BUS   On time
## 14:32  North Camp                              BUS   On time
## 14:33  Bracknell                               BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 14:49  Bracknell                               BUS   On time
## 14:50  Chippenham                              BUS   On time
## 15:00  Swindon                                 BUS   On time
## 15:03  Bracknell                               BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:19  Bracknell                               BUS   On time
## 15:27  North Camp                              BUS   On time
## 15:33  Bracknell                               BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:49  Bracknell                               BUS   On time
## 15:50  Chippenham                              BUS   On time
## 16:00  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-05 14:03:26
## Time   To                                      Plat  Expected
## 14:02  London Paddington                       11    14:13
## 14:10  London Paddington                       -     Cancelled
## 14:12  Salisbury                               3     On time
## 14:14  Ealing Broadway                         15    On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 14:19  Swansea                                 7     Delayed
## 14:20  Hereford                                9     14:23
## 14:23  Ealing Broadway                         14    On time
## 14:25  London Paddington                       11    On time
## 14:26  Didcot Parkway                          13    On time
## 14:28  Penzance                                7     On time
## 14:32  London Paddington                       10    On time
## 14:37  Basingstoke                             2     On time
## 14:42  Bristol Temple Meads                    -     Cancelled
## 14:42  London Paddington                       11    On time
## 14:45  Newbury                                 1     On time
## 14:52  Oxford                                  9     On time
## 14:53  Ealing Broadway                         14    On time
## 15:02  Exeter St Davids                        7     On time
## 15:02  London Paddington                       11    On time
## 15:10  London Paddington                       10    On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:14  Ealing Broadway                         15    On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 15:19  Swansea                                 7     On time
## 15:20  Great Malvern                           9     On time
## 15:23  Ealing Broadway                         14    On time
## 15:25  Didcot Parkway                          12    On time
## 15:25  London Paddington                       11    15:46
## 15:28  Plymouth                                7     On time
## 15:32  London Paddington                       10    On time
## 15:37  Basingstoke                             2     On time
## 15:42  Bristol Temple Meads                    7     On time
## 15:42  London Paddington                       11    On time
## 15:45  Bedwyn                                  3     On time
## 15:48  London Paddington                       10    On time
## 15:52  Bournemouth                             8     On time
## 15:52  Oxford                                  9     On time
## 15:53  Ealing Broadway                         14    On time
## 16:02  London Paddington                       -     Cancelled
## 14:05  Bracknell                               BUS   On time
## 14:05  Swindon                                 BUS   On time
## 14:15  Chippenham                              BUS   On time
## 14:21  Bracknell                               BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:35  Bracknell                               BUS   On time
## 14:35  North Camp                              BUS   On time
## 14:51  Bracknell                               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:05  Bracknell                               BUS   On time
## 15:05  Swindon                                 BUS   On time
## 15:15  Chippenham                              BUS   On time
## 15:21  Bracknell                               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  North Camp                              BUS   On time
## 15:35  Bracknell                               BUS   On time
## 15:45  North Camp                              BUS   On time
## 15:51  Bracknell                               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
