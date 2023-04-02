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

## Example (Last rendered on 2023-04-02 14:03)

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
## Reading (RDG) Station Board on 2023-04-02 14:03:19
## Time   From                                    Plat  Expected
## 14:45  Carmarthen                              15    15:36
## 14:57  Penzance                                14    15:24
## 14:59  London Paddington                       7     15:23
## 15:03  Didcot Parkway                          15    On time
## 15:06  Bournemouth                             12    15:12
## 15:06  London Paddington                       9     15:25
## 15:10  Weston-super-Mare                       -     15:36
## 15:13  London Paddington                       8     On time
## 15:14  Didcot Parkway                          15A   On time
## 15:18  Bedwyn                                  3     On time
## 15:19  London Paddington                       7     15:21
## 15:23  London Paddington                       9     On time
## 15:26  London Paddington                       7     15:30
## 15:32  Basingstoke                             2     On time
## 15:35  Exeter St Davids                        -     15:47
## 15:39  Didcot Parkway                          7     On time
## 15:47  Swansea                                 15    15:49
## 15:53  London Paddington                       9B    On time
## 15:58  Exeter St Davids                        14    On time
## 16:03  Didcot Parkway                          15    On time
## 16:07  London Paddington                       9     On time
## 16:10  Bristol Temple Meads                    -     Cancelled
## 16:12  Newbury                                 3     On time
## 16:13  London Paddington                       8     On time
## 16:14  Didcot Parkway                          15A   On time
## 16:19  London Paddington                       7     On time
## 16:23  London Paddington                       9     On time
## 16:26  London Paddington                       7     On time
## 16:32  Basingstoke                             2     On time
## 16:33  Gloucester                              15    On time
## 16:39  Didcot Parkway                          13    On time
## 16:42  Bristol Temple Meads                    14    On time
## 16:47  Swansea                                 15    16:51
## 16:53  London Paddington                       9     On time
## 16:58  Penzance                                14    17:09
## 17:00  London Paddington                       7B    On time
## 15:03  Bracknell                               BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:19  Bracknell                               BUS   On time
## 15:27  North Camp                              BUS   On time
## 15:33  Bracknell                               BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:49  Bracknell                               BUS   On time
## 16:03  Bracknell                               BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:12  North Camp                              BUS   On time
## 16:19  Bracknell                               -     Cancelled
## 16:32  North Camp                              BUS   On time
## 16:33  Bracknell                               BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:49  Bracknell                               -     Cancelled
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-02 14:03:25
## Time   To                                      Plat  Expected
## 14:46  London Paddington                       15    15:37
## 15:00  London Paddington                       14    15:25
## 15:01  Exeter St Davids                        7     15:24
## 15:05  London Paddington                       15    On time
## 15:09  Swansea                                 9     15:26
## 15:12  London Paddington                       -     15:37
## 15:15  Didcot Parkway                          12    On time
## 15:15  Ealing Broadway                         15A   On time
## 15:20  Didcot Parkway                          7     15:22
## 15:25  Bristol Temple Meads                    9     On time
## 15:28  Didcot Parkway                          8     On time
## 15:28  Plymouth                                7     15:31
## 15:37  Basingstoke                             2     On time
## 15:40  London Paddington                       -     15:48
## 15:43  Bedwyn                                  3     On time
## 15:48  London Paddington                       15    15:50
## 15:52  Bournemouth                             7     On time
## 15:55  Taunton                                 9B    On time
## 16:00  London Paddington                       14    On time
## 16:05  London Paddington                       15    On time
## 16:09  Swansea                                 9     On time
## 16:12  London Paddington                       -     Cancelled
## 16:15  Didcot Parkway                          12    On time
## 16:15  Ealing Broadway                         15A   On time
## 16:20  Didcot Parkway                          7     On time
## 16:25  Bristol Temple Meads                    9     On time
## 16:28  Didcot Parkway                          8     On time
## 16:28  Penzance                                7     On time
## 16:34  London Paddington                       15    On time
## 16:37  Basingstoke                             2     On time
## 16:43  Newbury                                 3     On time
## 16:44  London Paddington                       14    On time
## 16:48  London Paddington                       15    16:52
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 17:00  London Paddington                       14    17:10
## 17:01  Plymouth                                7B    On time
## 15:05  Bracknell                               BUS   On time
## 15:21  Bracknell                               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  North Camp                              BUS   On time
## 15:35  Bracknell                               BUS   On time
## 15:45  North Camp                              BUS   On time
## 15:51  Bracknell                               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:05  Bracknell                               BUS   On time
## 16:21  Bracknell                               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:35  Bracknell                               -     Cancelled
## 16:35  North Camp                              BUS   On time
## 16:51  Bracknell                               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
