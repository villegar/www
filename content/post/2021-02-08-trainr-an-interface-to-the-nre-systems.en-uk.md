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

## Example (Last rendered on 2021-10-17 14:03)

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
## Reading (RDG) Station Board on 2021-10-17 14:03:39
## Time   From                                    Plat  Expected
## 14:57  Penzance                                11    15:00
## 14:58  Hereford                                10    On time
## 15:00  London Paddington                       7B    On time
## 15:06  London Paddington                       9     On time
## 15:07  Bournemouth                             8     On time
## 15:09  Weston-super-Mare                       11A   15:14
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       14    On time
## 15:15  London Paddington                       12    On time
## 15:19  Bedwyn                                  3     On time
## 15:21  Swansea                                 10    15:29
## 15:25  London Paddington                       7     On time
## 15:33  Basingstoke                             2     On time
## 15:39  Oxford                                  7     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:43  London Paddington                       14    On time
## 15:54  London Paddington                       9B    On time
## 15:55  Hereford                                10    On time
## 15:58  Exeter St Davids                        11    On time
## 16:07  London Paddington                       9     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       9B    On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12    On time
## 16:17  Swansea                                 11    16:20
## 16:23  London Paddington                       9     On time
## 16:26  London Paddington                       7     On time
## 16:33  Basingstoke                             2     On time
## 16:39  Oxford                                  13    On time
## 16:43  London Paddington                       9     On time
## 16:43  London Paddington                       14    On time
## 16:43  Swindon                                 10    On time
## 16:52  London Paddington                       9     On time
## 16:58  Great Malvern                           10A   On time
## 16:58  Penzance                                11    On time
## 17:00  London Paddington                       7B    On time
## 15:03  Bracknell                               BUS   On time
## 15:19  Bracknell                               BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
## 15:33  Bracknell                               BUS   On time
## 15:45  North Camp                              BUS   On time
## 15:49  Bracknell                               BUS   On time
## 16:03  Bracknell                               BUS   On time
## 16:19  Bracknell                               BUS   On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 16:32  North Camp                              BUS   On time
## 16:33  Bracknell                               BUS   On time
## 16:49  Bracknell                               BUS   On time
## 16:50  North Camp                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-17 14:03:43
## Time   To                                      Plat  Expected
## 14:57  London Paddington                       11    15:01
## 15:00  London Paddington                       10    15:03
## 15:03  Exeter St Davids                        7B    On time
## 15:09  Swansea                                 9     On time
## 15:11  London Paddington                       11A   15:15
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           9B    On time
## 15:15  Oxford                                  8     On time
## 15:22  Ealing Broadway                         14    On time
## 15:25  Didcot Parkway                          12    On time
## 15:25  London Paddington                       10    15:30
## 15:28  Plymouth                                7     On time
## 15:38  Basingstoke                             2     On time
## 15:43  London Paddington                       10    On time
## 15:44  Bedwyn                                  3     On time
## 15:52  Bournemouth                             7     On time
## 15:52  Ealing Broadway                         14    On time
## 15:55  Taunton                                 9B    On time
## 15:58  London Paddington                       11    On time
## 15:59  London Paddington                       10    On time
## 16:09  Swansea                                 9     On time
## 16:11  London Paddington                       10    On time
## 16:14  Ealing Broadway                         15    On time
## 16:15  Hereford                                9B    On time
## 16:15  Oxford                                  13B   On time
## 16:20  London Paddington                       11    16:20
## 16:22  Ealing Broadway                         14    On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:27  Plymouth                                7     On time
## 16:38  Basingstoke                             2     On time
## 16:44  London Paddington                       10    On time
## 16:44  Newbury                                 3     On time
## 16:44  Swindon                                 9     On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  Exeter St Davids                        9     On time
##        via Bristol                             
## 16:59  London Paddington                       11    On time
## 17:00  London Paddington                       10A   On time
## 17:02  Plymouth                                7B    On time
## 15:16  Bracknell                               BUS   On time
## 15:31  Bracknell                               BUS   On time
## 15:35  North Camp                              BUS   On time
## 15:46  Bracknell                               BUS   On time
## 15:50  North Camp                              BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 16:01  Bracknell                               BUS   On time
## 16:16  Bracknell                               BUS   On time
## 16:31  Bracknell                               BUS   On time
## 16:40  North Camp                              BUS   On time
## 16:46  Bracknell                               BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:01  Bracknell                               BUS   On time
```
