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

## Example (Last rendered on 2023-02-05 16:03)

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
## Reading (RDG) Station Board on 2023-02-05 16:03:26
## Time   From                                    Plat  Expected
## 15:43  Carmarthen                              10    16:03
## 16:06  Great Malvern                           10A   On time
## 16:12  London Paddington                       9B    Delayed
## 16:12  Newbury                                 3     16:16
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       12B   On time
## 16:18  London Paddington                       7     On time
## 16:23  Bristol Temple Meads                    11    On time
## 16:26  London Paddington                       7     On time
## 16:28  London Paddington                       14    On time
## 16:29  Oxford                                  10A   On time
## 16:32  Basingstoke                             2     On time
## 16:35  Swansea                                 11    17:30
## 16:38  London Paddington                       7     16:52
## 16:39  Manchester Piccadilly                   13    On time
## 16:47  London Paddington                       9B    On time
## 16:47  Salisbury                               1     On time
## 16:57  London Paddington                       7B    On time
## 16:58  London Paddington                       14    On time
## 16:58  Penzance                                11    17:08
## 17:06  Bournemouth                             8     On time
## 17:06  Hereford                                10    On time
## 17:12  London Paddington                       9     On time
## 17:12  London Paddington                       12B   On time
## 17:13  Didcot Parkway                          15    On time
## 17:23  Bedwyn                                  3     On time
## 17:24  Bristol Temple Meads                    11    On time
## 17:26  London Paddington                       7     On time
## 17:28  London Paddington                       14    On time
## 17:29  Oxford                                  10A   On time
## 17:32  Basingstoke                             2     On time
## 17:38  London Paddington                       7     On time
## 17:38  Paignton                                11    On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:43  Swansea                                 10    On time
## 17:47  London Paddington                       9B    On time
## 17:57  Plymouth                                11    On time
## 17:58  London Paddington                       14    On time
## 16:03  Bracknell                               BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:12  North Camp                              BUS   On time
## 16:19  Bracknell                               BUS   On time
## 16:32  North Camp                              BUS   On time
## 16:33  Bracknell                               BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:49  Bracknell                               BUS   On time
## 16:50  Chippenham                              BUS   On time
## 17:00  Swindon                                 BUS   On time
## 17:03  Bracknell                               BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:19  Bracknell                               BUS   On time
## 17:27  North Camp                              BUS   On time
## 17:33  Bracknell                               BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 17:49  Bracknell                               BUS   On time
## 17:50  Chippenham                              BUS   On time
## 18:00  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-05 16:03:30
## Time   To                                      Plat  Expected
## 15:48  London Paddington                       10    16:04
## 16:02  London Paddington                       15    On time
## 16:10  London Paddington                       10A   On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 16:19  Swansea                                 7     On time
## 16:20  Hereford                                9B    Delayed
## 16:23  Ealing Broadway                         14    On time
## 16:25  Didcot Parkway                          12B   On time
## 16:25  London Paddington                       11    On time
## 16:28  Penzance                                7     On time
## 16:32  London Paddington                       10A   On time
## 16:37  Basingstoke                             2     On time
## 16:42  Plymouth                                7     16:53
##        via Bristol                             
## 16:45  Newbury                                 3     On time
## 16:52  Oxford                                  9B    On time
## 16:53  Ealing Broadway                         14    On time
## 17:02  London Paddington                       11    17:09
## 17:02  Plymouth                                7B    On time
## 17:10  London Paddington                       10    On time
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15    On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 17:19  Swansea                                 7B    On time
## 17:20  Great Malvern                           9     On time
## 17:23  Ealing Broadway                         14    On time
## 17:25  Didcot Parkway                          12B   On time
## 17:25  London Paddington                       11    On time
## 17:28  Penzance                                7     On time
## 17:32  London Paddington                       10A   On time
## 17:37  Basingstoke                             2     On time
## 17:42  London Paddington                       11    On time
## 17:42  Weston-super-Mare                       7     On time
## 17:45  Bedwyn                                  3     On time
## 17:48  London Paddington                       10    On time
## 17:52  Bournemouth                             8B    On time
## 17:52  Oxford                                  9B    On time
## 17:53  Ealing Broadway                         14    On time
## 18:02  London Paddington                       11    On time
## 16:05  Bracknell                               BUS   On time
## 16:05  Swindon                                 BUS   On time
## 16:15  Chippenham                              BUS   On time
## 16:21  Bracknell                               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:35  Bracknell                               BUS   On time
## 16:35  North Camp                              BUS   On time
## 16:51  Bracknell                               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:05  Bracknell                               BUS   On time
## 17:05  Swindon                                 BUS   On time
## 17:15  Chippenham                              BUS   On time
## 17:21  Bracknell                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  North Camp                              BUS   On time
## 17:35  Bracknell                               BUS   On time
## 17:45  North Camp                              BUS   On time
## 17:51  Bracknell                               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
