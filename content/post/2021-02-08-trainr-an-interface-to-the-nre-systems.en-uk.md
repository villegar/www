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

## Example (Last rendered on 2023-04-02 20:03)

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
## Reading (RDG) Station Board on 2023-04-02 20:03:19
## Time   From                                    Plat  Expected
## 20:49  Swansea                                 11    21:12
## 20:58  Penzance                                11    21:02
## 21:02  Didcot Parkway                          9     On time
## 21:04  Abbey Wood                              10    On time
## 21:06  Bournemouth                             8     21:14
## 21:07  London Paddington                       7     On time
## 21:11  Taunton                                 11A   21:15
## 21:15  Didcot Parkway                          7A    On time
## 21:15  London Paddington                       8B    On time
## 21:18  London Paddington                       9     On time
## 21:19  Bedwyn                                  1     21:21
## 21:32  Basingstoke                             2     On time
## 21:34  Abbey Wood                              10    On time
## 21:38  Didcot Parkway                          8     On time
## 21:48  Swansea                                 11    22:11
## 21:53  London Paddington                       9     On time
## 21:57  Didcot Parkway                          11A   On time
## 22:04  Abbey Wood                              10    On time
## 22:04  Plymouth                                11    On time
## 22:07  London Paddington                       8     On time
## 22:10  Weston-super-Mare                       11    On time
## 22:11  London Paddington                       7B    On time
## 22:13  Didcot Parkway                          13    On time
## 22:18  London Paddington                       8B    On time
## 22:24  Newbury                                 1     On time
## 22:29  Henley-on-Thames                        7     On time
## 22:32  Basingstoke                             13    On time
## 22:34  Abbey Wood                              10    On time
## 22:38  London Paddington                       9     On time
## 22:39  Didcot Parkway                          8     On time
## 22:49  Carmarthen                              9A    On time
## 22:50  Penzance                                11    On time
## 21:03  Bracknell                               BUS   On time
## 21:19  Bracknell                               BUS   On time
## 21:22  North Camp                              BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 21:33  Bracknell                               BUS   On time
## 21:49  Bracknell                               BUS   On time
## 22:03  Bracknell                               -     Cancelled
## 22:07  North Camp                              BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:19  Bracknell                               BUS   On time
## 22:24  North Camp                              BUS   On time
## 22:33  Bracknell                               -     Cancelled
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 22:49  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-02 20:03:23
## Time   To                                      Plat  Expected
## 20:50  London Paddington                       11    21:13
## 20:59  London Paddington                       11    21:03
## 21:05  London Paddington                       9     On time
## 21:09  Swansea                                 7     On time
## 21:12  Didcot Parkway                          8     21:14
## 21:12  London Paddington                       11A   21:16
## 21:15  Didcot Parkway                          8B    On time
## 21:18  Ealing Broadway                         7A    On time
## 21:20  Worcester Shrub Hill                    9     On time
## 21:24  Ealing Broadway                         10    On time
## 21:28  Exeter St Davids                        7B    On time
## 21:37  Basingstoke                             2     On time
## 21:43  Bedwyn                                  1     On time
## 21:50  London Paddington                       11    22:12
## 21:52  Southampton Central                     8     On time
## 21:54  Ealing Broadway                         10    On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:58  London Paddington                       11A   On time
## 22:05  London Paddington                       11    On time
## 22:09  Swansea                                 8     On time
## 22:11  London Paddington                       11    On time
## 22:12  Didcot Parkway                          7B    On time
## 22:18  Didcot Parkway                          8B    On time
## 22:28  Ealing Broadway                         10    On time
## 22:39  Bristol Temple Meads                    9     On time
## 22:43  Newbury                                 1     On time
## 22:50  London Paddington                       9A    On time
## 22:53  London Paddington                       11    On time
## 22:58  Ealing Broadway                         10    On time
## 21:05  Bracknell                               -     Cancelled
## 21:21  Bracknell                               BUS   On time
## 21:35  Bracknell                               BUS   On time
## 21:35  North Camp                              BUS   On time
## 21:50  North Camp                              -     Cancelled
## 21:51  Bracknell                               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:05  Bracknell                               BUS   On time
## 22:21  Bracknell                               -     Cancelled
## 22:35  Bracknell                               BUS   On time
## 22:54  Bracknell                               -     Cancelled
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
