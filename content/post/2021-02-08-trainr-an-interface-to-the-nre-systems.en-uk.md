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

## Example (Last rendered on 2023-01-29 14:05)

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
## Reading (RDG) Station Board on 2023-01-29 14:05:01
## Time   From                                    Plat  Expected
## 13:44  Cardiff Central                         11    14:01
## 13:56  Great Malvern                           10A   On time
## 13:58  Penzance                                11    14:05
## 14:09  Bristol Temple Meads                    10    14:18
## 14:09  London Paddington                       7     14:12
## 14:10  Didcot Parkway                          13A   On time
## 14:12  London Paddington                       9     14:15
## 14:18  London Paddington                       12B   Delayed
## 14:19  Newbury                                 1     On time
## 14:26  Abbey Wood                              14    14:28
## 14:27  London Paddington                       7     On time
## 14:32  Basingstoke                             2     On time
## 14:39  Manchester Piccadilly                   13    On time
## 14:44  Cardiff Central                         10    On time
## 14:47  London Paddington                       9B    On time
## 14:49  Salisbury                               1     On time
## 14:54  London Paddington                       9     On time
## 14:56  Abbey Wood                              14    On time
## 14:57  London Paddington                       7     On time
## 14:57  Penzance                                11    On time
## 14:58  Hereford                                10    On time
## 15:06  Bournemouth                             8     On time
## 15:09  London Paddington                       7     On time
## 15:09  Weston-super-Mare                       10    On time
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15A   On time
## 15:13  London Paddington                       12B   On time
## 15:18  Bedwyn                                  3     On time
## 15:24  London Paddington                       9     On time
## 15:26  Abbey Wood                              14    On time
## 15:27  London Paddington                       7     On time
## 15:32  Basingstoke                             2     On time
## 15:35  Exeter St Davids                        11    On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:45  Cardiff Central                         10    On time
## 15:47  Salisbury                               1     On time
## 15:54  London Paddington                       9     On time
## 15:56  Great Malvern                           10    On time
## 15:58  Abbey Wood                              14    On time
## 15:58  Exeter St Davids                        11    On time
## 14:03  Bracknell                               BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:12  North Camp                              BUS   On time
## 14:19  Bracknell                               BUS   On time
## 14:32  North Camp                              BUS   On time
## 14:33  Bracknell                               BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 14:49  Bracknell                               BUS   On time
## 15:03  Bracknell                               BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:19  Bracknell                               BUS   On time
## 15:27  North Camp                              BUS   On time
## 15:33  Bracknell                               BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:49  Bracknell                               BUS   On time
## 16:03  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-29 14:05:05
## Time   To                                      Plat  Expected
## 13:52  London Paddington                       11    14:04
## 14:00  London Paddington                       11    14:09
## 14:02  London Paddington                       10A   Delayed
## 14:10  Cardiff Central                         7     14:13
## 14:12  Salisbury                               1     On time
## 14:13  London Paddington                       10    14:19
## 14:14  Ealing Broadway                         13A   On time
## 14:14  Hereford                                9     14:16
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 14:22  Abbey Wood                              14    On time
## 14:25  Didcot Parkway                          12B   Delayed
## 14:28  Penzance                                7     On time
## 14:37  Basingstoke                             2     On time
## 14:40  Cardiff Central                         9     On time
## 14:43  Newbury                                 1     On time
## 14:50  Oxford                                  9B    On time
## 14:52  Abbey Wood                              14    On time
## 14:52  London Paddington                       10    On time
## 14:56  Taunton                                 9     On time
## 15:00  London Paddington                       11    On time
## 15:01  Exeter St Davids                        7     On time
## 15:02  London Paddington                       10    On time
## 15:10  Cardiff Central                         7     On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:13  London Paddington                       10    On time
## 15:14  Ealing Broadway                         15A   On time
## 15:14  Great Malvern                           9B    On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 15:22  Abbey Wood                              14    On time
## 15:25  Didcot Parkway                          12B   On time
## 15:26  Bath Spa                                9     On time
## 15:28  Plymouth                                7     On time
## 15:37  Basingstoke                             2     On time
## 15:43  Bedwyn                                  3     On time
## 15:43  London Paddington                       11    On time
## 15:52  Abbey Wood                              14    On time
## 15:52  Bournemouth                             7     On time
## 15:52  London Paddington                       10    On time
## 15:56  Taunton                                 9     On time
## 16:00  London Paddington                       11    On time
## 16:02  London Paddington                       10    On time
## 14:05  Bracknell                               BUS   On time
## 14:21  Bracknell                               BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:35  Bracknell                               BUS   On time
## 14:35  North Camp                              BUS   On time
## 14:51  Bracknell                               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:05  Bracknell                               BUS   On time
## 15:21  Bracknell                               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  North Camp                              BUS   On time
## 15:35  Bracknell                               BUS   On time
## 15:45  North Camp                              BUS   On time
## 15:51  Bracknell                               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
