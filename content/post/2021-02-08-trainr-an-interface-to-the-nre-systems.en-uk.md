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

## Example (Last rendered on 2023-04-02 16:07)

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
## Reading (RDG) Station Board on 2023-04-02 16:07:36
## Time   From                                    Plat  Expected
## 16:47  Swansea                                 15    17:15
## 16:58  Penzance                                14    17:16
## 17:06  Bournemouth                             12    17:10
## 17:10  Weston-super-Mare                       11    17:12
## 17:13  Didcot Parkway                          15A   On time
## 17:13  London Paddington                       8     On time
## 17:19  London Paddington                       9     On time
## 17:20  Bedwyn                                  3     17:25
## 17:23  London Paddington                       9     17:25
## 17:26  London Paddington                       7     17:34
## 17:32  Basingstoke                             2     17:34
## 17:34  Abbey Wood                              10    On time
## 17:36  Paignton                                11    17:40
## 17:39  Didcot Parkway                          8B    On time
## 17:40  Bristol Temple Meads                    9     On time
## 17:46  Carmarthen                              11    17:48
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Plymouth                                7     On time
## 18:02  Didcot Parkway                          11    On time
## 18:05  Abbey Wood                              10    On time
## 18:08  London Paddington                       9     On time
## 18:08  Plymouth                                11    On time
## 18:13  London Paddington                       8     On time
## 18:14  Didcot Parkway                          7     On time
## 18:21  London Paddington                       7     On time
## 18:21  Newbury                                 1     On time
## 18:24  Swindon                                 11    On time
## 18:32  Basingstoke                             2     On time
## 18:33  Cheltenham Spa                          11    On time
## 18:34  Abbey Wood                              10    On time
## 18:39  Didcot Parkway                          12    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:47  Swansea                                 11    On time
## 18:53  London Paddington                       9     On time
## 18:58  Penzance                                11    On time
## 19:03  Didcot Parkway                          11    On time
## 19:04  Abbey Wood                              10    On time
## 17:19  Bracknell                               BUS   On time
## 17:27  North Camp                              BUS   On time
## 17:33  Bracknell                               BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 17:49  Bracknell                               BUS   On time
## 18:03  Bracknell                               -     Cancelled
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:12  North Camp                              BUS   On time
## 18:19  Bracknell                               BUS   On time
## 18:30  North Camp                              BUS   On time
## 18:33  Bracknell                               -     Cancelled
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:49  Bracknell                               BUS   On time
## 19:03  Bracknell                               BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-02 16:07:41
## Time   To                                      Plat  Expected
## 16:48  London Paddington                       15    17:16
## 17:00  London Paddington                       14    17:17
## 17:09  Swansea                                 9B    On time
## 17:14  Ealing Broadway                         15A   On time
## 17:15  Didcot Parkway                          12    On time
## 17:15  London Paddington                       11    On time
## 17:20  Didcot Parkway                          9     On time
## 17:25  Bristol Temple Meads                    9     17:25
## 17:28  Didcot Parkway                          8     On time
## 17:28  Penzance                                7     17:35
## 17:37  Basingstoke                             2     On time
## 17:40  London Paddington                       11    17:40
## 17:42  London Paddington                       9     On time
## 17:43  Bedwyn                                  3     On time
## 17:48  London Paddington                       11    17:48
## 17:52  Bournemouth                             8B    On time
## 17:54  Abbey Wood                              10    On time
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Cheltenham Spa                          8     On time
## 17:59  London Paddington                       7     On time
## 18:05  London Paddington                       11    On time
## 18:10  Swansea                                 9     On time
## 18:12  London Paddington                       11    On time
## 18:14  Ealing Broadway                         7     On time
## 18:15  Didcot Parkway                          12    On time
## 18:21  Didcot Parkway                          7     On time
## 18:24  Abbey Wood                              10    On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:27  London Paddington                       11    On time
## 18:28  Didcot Parkway                          8     On time
## 18:28  Penzance                                7     On time
## 18:33  London Paddington                       11    On time
## 18:37  Basingstoke                             2     On time
## 18:41  London Paddington                       11    On time
## 18:43  Newbury                                 1     On time
## 18:49  London Paddington                       11    On time
## 18:54  Abbey Wood                              10    On time
## 18:55  Weston-super-Mare                       9     On time
## 19:00  London Paddington                       11    On time
## 19:01  Plymouth                                7     On time
## 19:05  London Paddington                       11    On time
## 17:05  Bracknell                               -     Cancelled
## 17:21  Bracknell                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  North Camp                              BUS   On time
## 17:35  Bracknell                               BUS   On time
## 17:45  North Camp                              BUS   On time
## 17:51  Bracknell                               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:05  Bracknell                               BUS   On time
## 18:21  Bracknell                               -     Cancelled
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:35  Bracknell                               BUS   On time
## 18:40  North Camp                              BUS   On time
## 18:51  Bracknell                               -     Cancelled
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:05  Bracknell                               BUS   On time
```
