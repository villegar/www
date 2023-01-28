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

## Example (Last rendered on 2023-01-28 18:03)

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
## Reading (RDG) Station Board on 2023-01-28 18:03:55
## Time   From                                    Plat  Expected
## 17:55  London Paddington                       8     18:03
## 17:58  Plymouth                                11    On time
## 18:01  Didcot Parkway                          15    On time
## 18:03  Abbey Wood                              14    18:05
## 18:10  Bristol Temple Meads                    10    On time
## 18:10  London Paddington                       12    18:13
## 18:11  London Paddington                       9     18:15
## 18:17  London Paddington                       9     On time
## 18:21  Bristol Parkway                         11    On time
## 18:23  Basingstoke                             2     On time
## 18:25  London Paddington                       9     On time
## 18:25  Oxford                                  10A   On time
## 18:27  London Paddington                       7     On time
## 18:29  Newbury                                 11    On time
## 18:31  Didcot Parkway                          15    On time
## 18:33  Abbey Wood                              14    On time
## 18:33  Cheltenham Spa                          10A   On time
## 18:33  London Paddington                       7     On time
## 18:40  Bath Spa                                11    On time
## 18:41  London Paddington                       9     On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       12    On time
## 18:46  Swansea                                 10    On time
## 18:47  London Paddington                       9B    On time
## 18:50  Basingstoke                             2     On time
## 18:51  London Paddington                       8B    On time
## 18:54  Great Malvern                           10    On time
## 18:55  London Paddington                       9     On time
## 18:56  Salisbury                               7     On time
## 18:59  Penzance                                11    On time
## 19:01  Didcot Parkway                          15    On time
## 19:03  Abbey Wood                              14    On time
## 19:06  Bournemouth                             13B   On time
## 19:10  Bristol Temple Meads                    10    On time
## 19:11  London Paddington                       9     On time
## 19:12  London Paddington                       12    On time
## 19:17  London Paddington                       9     On time
## 19:22  Basingstoke                             2     On time
## 19:25  London Paddington                       9     On time
## 19:26  Oxford                                  10    On time
## 19:27  London Paddington                       7     On time
## 19:27  Newbury                                 11    On time
## 19:31  Didcot Parkway                          15    On time
## 19:32  London Paddington                       7     On time
## 19:33  Abbey Wood                              14    On time
## 19:38  London Paddington                       9     On time
## 19:40  Bath Spa                                10    On time
## 19:40  Manchester Piccadilly                   13    On time
## 19:40  Newbury                                 1     On time
## 19:43  London Paddington                       12    On time
## 19:46  Swansea                                 10    On time
## 19:47  London Paddington                       7     On time
## 19:49  London Paddington                       8     On time
## 19:51  Basingstoke                             2     On time
## 19:51  London Paddington                       9     On time
## 19:54  Great Malvern                           10    On time
## 19:55  London Paddington                       8     On time
## 19:56  Salisbury                               3     On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:05  Bracknell                               BUS   On time
## 18:22  Bracknell                               BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:35  Bracknell                               BUS   On time
## 18:38  North Camp                              BUS   On time
## 18:52  Bracknell                               BUS   On time
## 18:58  North Camp                              BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:05  Bracknell                               BUS   On time
## 19:22  Bracknell                               BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:35  Bracknell                               BUS   On time
## 19:38  North Camp                              BUS   On time
## 19:52  Bracknell                               -     Cancelled
## 19:56  North Camp                              BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-28 18:04:00
## Time   To                                      Plat  Expected
## 18:00  Weston-super-Mare                       8     18:04
## 18:05  Basingstoke                             2     On time
## 18:05  London Paddington                       11    On time
## 18:10  Newbury                                 1     On time
## 18:12  London Paddington                       10    On time
## 18:13  Swansea                                 9     18:16
## 18:15  Ealing Broadway                         15    On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 18:18  Yeovil Junction                         3     On time
## 18:19  Worcester Foregate Street               9     On time
## 18:23  Didcot Parkway                          12    On time
## 18:24  Abbey Wood                              14    On time
## 18:24  London Paddington                       11    On time
## 18:27  Bath Spa                                9     On time
## 18:27  London Paddington                       10A   On time
## 18:29  Penzance                                7     On time
## 18:32  London Paddington                       11    On time
## 18:34  Newbury                                 7     On time
## 18:35  London Paddington                       10A   On time
## 18:37  Basingstoke                             2     On time
## 18:42  London Paddington                       11    On time
## 18:43  Swansea                                 9     On time
## 18:45  Ealing Broadway                         15    On time
## 18:49  Oxford                                  9B    On time
## 18:50  London Paddington                       10    On time
## 18:52  Winchester                              7     On time
## 18:53  Cheltenham Spa                          8B    On time
## 18:53  Didcot Parkway                          12    On time
## 18:54  Abbey Wood                              14    On time
## 18:56  London Paddington                       10    On time
## 18:57  Taunton                                 9     On time
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    On time
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       10    On time
## 19:13  Swansea                                 9     On time
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 19:19  Hereford                                9     On time
## 19:23  Didcot Parkway                          12    On time
## 19:24  Abbey Wood                              14    On time
## 19:24  Salisbury                               7     On time
## 19:27  Bath Spa                                9     On time
## 19:28  London Paddington                       10    On time
## 19:29  Plymouth                                7     On time
## 19:32  London Paddington                       11    On time
## 19:34  Newbury                                 7     On time
## 19:37  Basingstoke                             2     On time
## 19:41  Bristol Parkway                         9     On time
## 19:42  London Paddington                       10    On time
## 19:45  Ealing Broadway                         15    On time
## 19:48  London Paddington                       10    On time
## 19:51  Oxford                                  8     On time
## 19:53  Cheltenham Spa                          9     On time
## 19:54  Abbey Wood                              14    On time
## 19:55  Didcot Parkway                          12    On time
## 19:56  London Paddington                       10    On time
## 19:58  Taunton                                 8     On time
## 18:05  North Camp                              BUS   On time
## 18:12  Bracknell                               -     Cancelled
## 18:22  North Camp                              BUS   On time
## 18:25  Bracknell                               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:42  Bracknell                               BUS   On time
## 18:55  Bracknell                               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:12  Bracknell                               BUS   On time
## 19:15  North Camp                              BUS   On time
## 19:25  Bracknell                               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:35  North Camp                              BUS   On time
## 19:42  Bracknell                               BUS   On time
## 19:55  Bracknell                               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
