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

## Example (Last rendered on 2023-04-02 08:03)

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
## Reading (RDG) Station Board on 2023-04-02 08:03:49
## Time   From                                    Plat  Expected
## 08:18  London Paddington                       7     09:18
## 08:39  London Paddington                       7     09:35
## 08:54  Bristol Temple Meads                    -     09:03
## 08:56  London Paddington                       9     Delayed
## 09:08  Didcot Parkway                          14    09:15
## 09:11  London Paddington                       9     Delayed
## 09:15  Ealing Broadway                         7     On time
## 09:15  Newbury                                 14    On time
## 09:17  London Paddington                       10    Delayed
## 09:23  London Paddington                       7     Delayed
## 09:28  Swindon                                 13    On time
## 09:32  Basingstoke                             2     On time
## 09:38  Bristol Parkway                         15    Delayed
## 09:51  Maidenhead                              7B    On time
## 09:56  London Paddington                       9     On time
## 09:58  Didcot Parkway                          15    On time
## 10:02  Didcot Parkway                          14    On time
## 10:06  Southampton Central                     12B   On time
## 10:10  Weston-super-Mare                       14    On time
## 10:16  London Paddington                       8     On time
## 10:18  Bedwyn                                  12    On time
## 10:19  London Paddington                       9     On time
## 10:25  Swansea                                 15    10:39
## 10:26  London Paddington                       7     On time
## 10:32  Basingstoke                             2     On time
## 10:35  Exeter St Davids                        14    On time
## 10:39  Didcot Parkway                          13    On time
## 10:42  Bristol Parkway                         15    10:54
## 10:42  London Paddington                       9     On time
## 10:53  London Paddington                       9     On time
## 10:59  London Paddington                       7     On time
## 09:03  Bracknell                               -     Cancelled
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:15  North Camp                              BUS   On time
## 09:19  Bracknell                               BUS   On time
## 09:33  Bracknell                               BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:49  Bracknell                               BUS   On time
## 10:03  Bracknell                               BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:12  North Camp                              BUS   On time
## 10:19  Bracknell                               BUS   On time
## 10:32  North Camp                              BUS   On time
## 10:33  Bracknell                               -     Cancelled
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:49  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-02 08:03:54
## Time   To                                      Plat  Expected
## 08:21  Penzance                                7     09:19
## 08:40  Exeter St Davids                        7     09:36
##        via Bristol                             
## 08:59  Swansea                                 9     Delayed
## 09:10  Ealing Broadway                         14    09:16
## 09:15  Didcot Parkway                          8     On time
## 09:18  Didcot Parkway                          7     On time
## 09:18  Didcot Parkway                          9     Delayed
## 09:19  Penzance                                10    Delayed
## 09:20  Maidenhead                              14    On time
## 09:30  London Paddington                       13    On time
## 09:35  Weston-super-Mare                       7     Delayed
## 09:37  Basingstoke                             2     On time
## 09:43  Bedwyn                                  1     On time
## 09:44  London Paddington                       15    Delayed
## 09:52  Bournemouth                             8     On time
## 09:58  Carmarthen                              9     On time
## 10:05  London Paddington                       14    On time
## 10:11  London Paddington                       14    On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Didcot Parkway                          12B   On time
## 10:20  Didcot Parkway                          9     On time
## 10:28  Didcot Parkway                          8     On time
## 10:28  London Paddington                       15    10:40
## 10:28  Penzance                                7     On time
## 10:37  Basingstoke                             2     On time
## 10:40  London Paddington                       14    On time
## 10:43  Bristol Parkway                         9     On time
## 10:43  Newbury                                 3     On time
## 10:44  London Paddington                       15    10:55
## 10:55  Weston-super-Mare                       9     On time
## 11:01  Paignton                                7     On time
## 09:05  Bracknell                               -     Cancelled
## 09:21  Bracknell                               BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:30  North Camp                              BUS   On time
## 09:35  Bracknell                               BUS   On time
## 09:45  North Camp                              BUS   On time
## 09:51  Bracknell                               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:05  Bracknell                               BUS   On time
## 10:21  Bracknell                               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:35  Bracknell                               BUS   On time
## 10:35  North Camp                              BUS   On time
## 10:51  Bracknell                               -     Cancelled
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
