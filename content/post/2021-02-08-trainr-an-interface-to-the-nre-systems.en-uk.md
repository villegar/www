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

## Example (Last rendered on 2023-02-05 12:03)

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
## Reading (RDG) Station Board on 2023-02-05 12:03:33
## Time   From                                    Plat  Expected
## 11:39  Swansea                                 10    12:05
## 11:41  London Paddington                       -     12:02
## 11:47  London Paddington                       7     Delayed
## 11:58  Plymouth                                11    On time
## 12:06  Great Malvern                           10A   On time
## 12:12  London Paddington                       9B    12:15
## 12:13  Didcot Parkway                          15    On time
## 12:13  London Paddington                       12B   On time
## 12:18  London Paddington                       7B    On time
## 12:19  Newbury                                 1     On time
## 12:23  Bristol Temple Meads                    11    On time
## 12:26  London Paddington                       7     On time
## 12:28  London Paddington                       14    On time
## 12:32  Basingstoke                             2     On time
## 12:35  Swansea                                 11    On time
## 12:38  London Paddington                       7     12:47
## 12:39  Manchester Piccadilly                   12    On time
## 12:47  London Paddington                       9B    On time
## 12:47  Salisbury                               1     On time
## 12:53  Penzance                                11    On time
## 12:57  London Paddington                       7     On time
## 12:58  London Paddington                       14    On time
## 13:06  Bournemouth                             8     On time
## 13:06  Great Malvern                           10A   On time
## 13:12  London Paddington                       9B    On time
## 13:13  Didcot Parkway                          15    On time
## 13:13  London Paddington                       13B   On time
## 13:17  Bedwyn                                  1     13:20
## 13:18  London Paddington                       7     On time
## 13:26  London Paddington                       7     On time
## 13:27  Paignton                                11    On time
## 13:28  London Paddington                       14    On time
## 13:29  Oxford                                  10A   On time
## 13:32  Basingstoke                             2     On time
## 13:35  Bristol Temple Meads                    10    On time
## 13:38  London Paddington                       7     On time
## 13:38  Swansea                                 11    On time
## 13:39  Manchester Piccadilly                   8     On time
## 13:47  London Paddington                       9     On time
## 13:47  Salisbury                               1     On time
## 13:58  London Paddington                       14    On time
## 13:58  Penzance                                11    On time
## 12:03  Bracknell                               BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:12  North Camp                              BUS   On time
## 12:19  Bracknell                               BUS   On time
## 12:32  North Camp                              BUS   On time
## 12:33  Bracknell                               BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 12:49  Bracknell                               BUS   On time
## 12:50  Chippenham                              BUS   On time
## 13:00  Swindon                                 BUS   On time
## 13:03  Bracknell                               BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:19  Bracknell                               BUS   On time
## 13:27  North Camp                              BUS   On time
## 13:33  Bracknell                               BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 13:49  Bracknell                               BUS   On time
## 13:50  Chippenham                              BUS   On time
## 14:00  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-05 12:03:37
## Time   To                                      Plat  Expected
## 11:43  London Paddington                       10    12:13
## 12:02  London Paddington                       11    On time
## 12:10  London Paddington                       10A   On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         15    On time
## 12:15  Manchester Piccadilly                   15    On time
##        via Coventry & Wilmslow                 
## 12:19  Swansea                                 7B    On time
## 12:20  Hereford                                9B    On time
## 12:23  Ealing Broadway                         14    On time
## 12:25  London Paddington                       11    On time
## 12:26  Didcot Parkway                          12B   On time
## 12:28  Penzance                                7     On time
## 12:32  London Paddington                       9A    On time
## 12:37  Basingstoke                             2     On time
## 12:42  Bristol Temple Meads                    7     12:48
## 12:42  London Paddington                       11    On time
## 12:46  Newbury                                 1     On time
## 12:52  Oxford                                  9B    On time
## 12:53  Ealing Broadway                         14    On time
## 13:01  Paignton                                7     On time
## 13:02  London Paddington                       11    On time
## 13:10  London Paddington                       10A   On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:14  Ealing Broadway                         15    On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 13:19  Carmarthen                              7     On time
## 13:20  Great Malvern                           9B    On time
## 13:23  Ealing Broadway                         14    On time
## 13:26  Didcot Parkway                          13B   On time
## 13:28  Plymouth                                7     On time
## 13:32  London Paddington                       10A   On time
## 13:35  London Paddington                       11    On time
## 13:37  Basingstoke                             2     On time
## 13:42  Bristol Temple Meads                    7     On time
## 13:45  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:48  London Paddington                       11    On time
## 13:52  Bournemouth                             8     On time
## 13:52  Oxford                                  9     On time
## 13:53  Ealing Broadway                         14    On time
## 14:02  London Paddington                       11    On time
## 12:05  Bracknell                               BUS   On time
## 12:05  Swindon                                 BUS   On time
## 12:15  Chippenham                              BUS   On time
## 12:21  Bracknell                               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:35  Bracknell                               BUS   On time
## 12:35  North Camp                              BUS   On time
## 12:51  Bracknell                               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:05  Bracknell                               BUS   On time
## 13:05  Swindon                                 BUS   On time
## 13:15  Chippenham                              BUS   On time
## 13:21  Bracknell                               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  North Camp                              BUS   On time
## 13:35  Bracknell                               BUS   On time
## 13:45  North Camp                              BUS   On time
## 13:51  Bracknell                               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
