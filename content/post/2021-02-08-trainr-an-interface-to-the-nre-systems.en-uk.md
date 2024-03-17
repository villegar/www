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

## Example (Last rendered on 2024-03-17 17:06)

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
## Reading (RDG) Station Board on 2024-03-17 17:06:39.970957
## Time   From                                    Plat  Expected
## 16:50  Bristol Parkway                         10    17:11
## 16:57  Hereford                                11    17:16
## 16:58  Exeter St Davids                        15    On time
## 17:00  London Paddington                       7     17:04
## 17:03  London Paddington                       9     17:08
## 17:06  Abbey Wood                              14    17:11
## 17:07  Bournemouth                             8B    17:04
## 17:09  Weston-super-Mare                       10    17:19
## 17:16  Swindon                                 11A   17:18
## 17:20  Bedwyn                                  3     17:22
## 17:28  London Paddington                       7     On time
## 17:30  London Paddington                       9     On time
## 17:33  Basingstoke                             2     On time
## 17:35  Didcot Parkway                          12    On time
## 17:36  Abbey Wood                              14    17:39
## 17:36  Exeter St Davids                        11    17:38
## 17:39  Oxford                                  8     On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:45  London Paddington                       13B   On time
## 17:50  Cardiff Central                         11A   On time
## 17:57  Hereford                                10A   18:00
## 17:58  Exeter St Davids                        15    On time
## 18:01  London Paddington                       9     On time
## 18:03  London Paddington                       7     On time
## 18:06  Abbey Wood                              14    On time
## 18:06  Bournemouth                             8B    On time
## 18:09  Bristol Temple Meads                    11    On time
## 18:13  London Paddington                       9     On time
## 18:16  Swindon                                 10A   On time
## 18:21  Newbury                                 1     On time
## 18:28  London Paddington                       7     On time
## 18:29  Cheltenham Spa                          10    On time
## 18:30  London Paddington                       9     On time
## 18:33  Basingstoke                             2     On time
## 18:35  Didcot Parkway                          13    On time
## 18:36  Abbey Wood                              14    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:40  Oxford                                  7B    On time
## 18:45  London Paddington                       12B   On time
## 18:50  Cardiff Central                         11    On time
## 18:58  Exeter St Davids                        15    On time
## 18:58  London Paddington                       8     On time
## 19:00  London Paddington                       7     On time
## 19:03  London Paddington                       9     On time
## 17:09  Bracknell                               BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:27  Bracknell                               BUS   On time
## 17:32  North Camp                              BUS   On time
## 17:39  Bracknell                               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 17:57  Bracknell                               BUS   On time
## 18:09  Bracknell                               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:20  North Camp                              BUS   On time
## 18:27  Bracknell                               BUS   On time
## 18:37  North Camp                              BUS   On time
## 18:39  Bracknell                               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:57  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-17 17:06:41.623951
## Time   To                                      Plat  Expected
## 16:58  London Paddington                       10    17:12
## 17:01  Exeter St Davids                        7     17:06
## 17:05  Cardiff Central                         9     17:09
## 17:05  London Paddington                       15    On time
## 17:08  London Paddington                       11    17:17
## 17:12  Salisbury                               2     On time
## 17:14  London Paddington                       10    17:20
## 17:14  Oxford                                  8B    On time
## 17:15  Great Malvern                           9B    17:21
## 17:17  London Paddington                       11A   17:19
## 17:25  Didcot Parkway                          12A   On time
## 17:29  Exeter St Davids                        7     On time
## 17:32  Abbey Wood                              14    On time
## 17:32  Bristol Temple Meads                    9     On time
## 17:38  Basingstoke                             2     On time
## 17:38  London Paddington                       11    17:38
## 17:44  London Paddington                       10    On time
## 17:45  Bedwyn                                  3     On time
## 17:46  Swindon                                 13B   On time
## 17:52  Bournemouth                             8     On time
## 17:58  London Paddington                       11A   On time
## 18:00  Cheltenham Spa                          8     On time
## 18:02  Abbey Wood                              14    On time
## 18:05  London Paddington                       15    On time
## 18:05  Weston-super-Mare                       9     On time
## 18:08  London Paddington                       10A   On time
## 18:10  Cardiff Central                         7     On time
## 18:14  London Paddington                       11    On time
## 18:14  Oxford                                  8B    On time
## 18:15  Great Malvern                           9     On time
## 18:17  London Paddington                       10A   On time
## 18:25  Didcot Parkway                          12A   On time
## 18:29  Exeter St Davids                        7     On time
## 18:32  Abbey Wood                              14    On time
## 18:32  Bristol Temple Meads                    9     On time
## 18:36  London Paddington                       10    On time
## 18:38  Basingstoke                             2     On time
## 18:43  Newbury                                 1     On time
## 18:44  London Paddington                       11    On time
## 18:46  Swindon                                 12B   On time
## 18:52  Bournemouth                             7B    On time
## 18:58  London Paddington                       11    On time
## 19:00  Weston-super-Mare                       8     On time
## 19:01  Exeter St Davids                        7     On time
## 19:02  Abbey Wood                              14    On time
## 19:05  Cardiff Central                         9     On time
## 19:05  London Paddington                       15    On time
## 17:07  Bracknell                               BUS   On time
## 17:23  Bracknell                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:32  North Camp                              BUS   On time
## 17:37  Bracknell                               BUS   On time
## 17:53  Bracknell                               BUS   On time
## 17:55  North Camp                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:07  Bracknell                               BUS   On time
## 18:23  Bracknell                               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:37  Bracknell                               BUS   On time
## 18:38  North Camp                              BUS   On time
## 18:53  Bracknell                               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
