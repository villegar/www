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

## Example (Last rendered on 2023-04-02 10:03)

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
## Reading (RDG) Station Board on 2023-04-02 10:03:20
## Time   From                                    Plat  Expected
## 10:02  Didcot Parkway                          -     10:55
## 10:42  Bristol Parkway                         15    11:02
## 10:42  London Paddington                       9     11:18
## 11:00  Didcot Parkway                          15    11:14
## 11:06  Bournemouth                             12    11:12
## 11:07  London Paddington                       9     11:14
## 11:10  Didcot Parkway                          15    11:14
## 11:14  Bristol Temple Meads                    14A   On time
## 11:15  London Paddington                       8     11:17
## 11:17  Swansea                                 15    11:26
## 11:19  Bedwyn                                  1     11:24
## 11:19  London Paddington                       9     11:25
## 11:26  London Paddington                       7     11:32
## 11:33  Basingstoke                             2     On time
## 11:34  Plymouth                                14    On time
## 11:39  Didcot Parkway                          7     On time
## 11:45  Swansea                                 15    11:49
## 11:53  London Paddington                       9     On time
## 11:58  Plymouth                                14    On time
## 12:03  Didcot Parkway                          15    On time
## 12:07  London Paddington                       9     On time
## 12:10  Didcot Parkway                          15    On time
## 12:13  London Paddington                       8     On time
## 12:14  Bristol Temple Meads                    14    On time
## 12:19  London Paddington                       9     On time
## 12:19  Newbury                                 1     On time
## 12:26  London Paddington                       7     On time
## 12:32  Basingstoke                             2     On time
## 12:32  Cheltenham Spa                          15    Delayed
## 12:39  Didcot Parkway                          12    On time
## 12:45  Swansea                                 15    On time
## 12:53  London Paddington                       9     On time
## 12:53  Penzance                                14    On time
## 12:59  London Paddington                       7     On time
## 11:03  Bracknell                               BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:19  Bracknell                               BUS   On time
## 11:27  North Camp                              BUS   On time
## 11:33  Bracknell                               BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 11:49  Bracknell                               BUS   On time
## 12:03  Bracknell                               BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:12  North Camp                              BUS   On time
## 12:19  Bracknell                               BUS   On time
## 12:32  North Camp                              BUS   On time
## 12:33  Bracknell                               BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 12:49  Bracknell                               -     Cancelled
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-02 10:03:25
## Time   To                                      Plat  Expected
## 10:05  London Paddington                       -     Cancelled
## 10:43  Swindon                                 9     11:19
## 10:44  London Paddington                       15    11:03
## 10:55  Weston-super-Mare                       9B    11:15
## 11:05  London Paddington                       15    11:15
## 11:09  Swansea                                 9     11:15
## 11:14  Ealing Broadway                         15    11:15
## 11:15  Didcot Parkway                          12    On time
## 11:18  London Paddington                       14A   On time
## 11:22  Didcot Parkway                          9     11:26
## 11:25  London Paddington                       15    11:27
## 11:28  Didcot Parkway                          8     On time
## 11:28  Plymouth                                7     11:33
## 11:37  Basingstoke                             2     On time
## 11:40  London Paddington                       14    On time
## 11:43  Bedwyn                                  1     On time
## 11:46  London Paddington                       15    11:50
## 11:52  Bournemouth                             7     On time
## 11:55  Bristol Temple Meads                    9     On time
## 12:00  London Paddington                       14    On time
## 12:05  London Paddington                       15    On time
## 12:09  Carmarthen                              9     On time
## 12:14  Ealing Broadway                         15    On time
## 12:15  Didcot Parkway                          12    On time
## 12:18  London Paddington                       14    On time
## 12:22  Didcot Parkway                          9     On time
## 12:28  Didcot Parkway                          8     On time
## 12:28  Penzance                                7     On time
## 12:34  London Paddington                       15    Delayed
## 12:37  Basingstoke                             2     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       15    On time
## 12:55  London Paddington                       14    On time
## 12:55  Weston-super-Mare                       9     On time
## 13:01  Paignton                                7     On time
## 11:05  Bracknell                               BUS   On time
## 11:21  Bracknell                               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  North Camp                              BUS   On time
## 11:35  Bracknell                               BUS   On time
## 11:45  North Camp                              BUS   On time
## 11:51  Bracknell                               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:05  Bracknell                               BUS   On time
## 12:21  Bracknell                               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:35  Bracknell                               BUS   On time
## 12:35  North Camp                              BUS   On time
## 12:51  Bracknell                               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
