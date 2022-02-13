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

## Example (Last rendered on 2022-02-13 10:03)

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
## Reading (RDG) Station Board on 2022-02-13 10:03:54
## Time   From                                    Plat  Expected
## 09:58  Didcot Parkway                          15    On time
## 09:59  Worcester Foregate Street               10A   On time
## 10:01  London Paddington                       9     On time
## 10:08  Southampton Central                     8B    On time
## 10:09  Weston-super-Mare                       10    10:13
## 10:14  Bedwyn                                  3     On time
## 10:14  London Paddington                       14    On time
## 10:16  London Paddington                       13    On time
## 10:20  London Paddington                       9     On time
## 10:25  Swansea                                 11    On time
## 10:28  London Paddington                       7     On time
## 10:33  Basingstoke                             1     On time
## 10:36  London Paddington                       9     On time
## 10:39  Birmingham New Street                   13    11:16
## 10:42  Exeter St Davids                        11    On time
## 10:44  London Paddington                       14    On time
## 10:47  Salisbury                               1     On time
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:56  Great Malvern                           11    On time
## 10:58  London Paddington                       7     On time
## 11:01  London Paddington                       9     On time
## 11:05  Bristol Temple Meads                    10    On time
## 11:08  Bournemouth                             7     On time
## 11:10  Didcot Parkway                          15    On time
## 11:14  London Paddington                       14    On time
## 11:14  Swansea                                 11    On time
## 11:15  London Paddington                       12    On time
## 11:19  Bedwyn                                  1     On time
## 11:19  London Paddington                       9     On time
## 11:28  London Paddington                       7     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Exeter St Davids                        11    On time
## 11:39  Manchester Piccadilly                   7     On time
## 11:44  London Paddington                       14    On time
## 11:45  Swansea                                 11    On time
## 11:47  Salisbury                               1     On time
## 11:53  London Paddington                       9     On time
## 11:56  Great Malvern                           10    On time
## 11:58  Exeter St Davids                        11    On time
## 10:12  Ascot                                   BUS   On time
## 10:13  North Camp                              BUS   On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 10:26  Ascot                                   BUS   On time
## 10:27  North Camp                              BUS   On time
## 10:42  Ascot                                   BUS   On time
## 10:56  Ascot                                   BUS   On time
## 11:12  Ascot                                   BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
## 11:22  North Camp                              BUS   On time
## 11:26  Ascot                                   BUS   On time
## 11:42  Ascot                                   BUS   On time
## 11:56  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-13 10:03:57
## Time   To                                      Plat  Expected
## 10:02  London Paddington                       10A   On time
## 10:03  Carmarthen                              9     On time
## 10:06  London Paddington                       15    On time
## 10:12  Salisbury                               1     On time
## 10:15  London Paddington                       10    On time
## 10:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Wilmslow                 
## 10:21  Hereford                                9     On time
## 10:26  Didcot Parkway                          13    On time
## 10:28  Ealing Broadway                         14    On time
## 10:29  Exeter St Davids                        7     On time
## 10:32  London Paddington                       11    On time
## 10:38  Basingstoke                             1     On time
## 10:40  Swindon                                 9     On time
## 10:44  Newbury                                 2     On time
## 10:47  London Paddington                       11    On time
## 10:55  Weston-super-Mare                       9     On time
## 10:58  Ealing Broadway                         14    On time
## 11:00  London Paddington                       10    On time
## 11:02  London Paddington                       11    On time
## 11:03  Exeter St Davids                        7     On time
## 11:09  Swansea                                 9     On time
## 11:12  Ealing Broadway                         15    On time
## 11:12  Salisbury                               1     On time
## 11:15  London Paddington                       10    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 11:17  London Paddington                       11    On time
## 11:21  Great Malvern                           9     On time
## 11:26  Didcot Parkway                          12    On time
## 11:28  Ealing Broadway                         14    On time
## 11:29  Exeter St Davids                        7     On time
## 11:35  London Paddington                       11    On time
## 11:38  Basingstoke                             2     On time
## 11:44  Bedwyn                                  1     On time
## 11:50  London Paddington                       11    On time
## 11:52  Bournemouth                             7     On time
## 11:55  Bristol Temple Meads                    9     On time
## 11:58  Ealing Broadway                         14    On time
## 12:00  London Paddington                       11    On time
## 12:02  London Paddington                       10    On time
## 10:15  Ascot                                   BUS   On time
## 10:30  Ascot                                   BUS   On time
## 10:35  North Camp                              BUS   On time
## 10:45  Ascot                                   BUS   On time
## 11:00  Ascot                                   BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 11:15  Ascot                                   BUS   On time
## 11:30  Ascot                                   BUS   On time
## 11:30  North Camp                              BUS   On time
## 11:45  Ascot                                   BUS   On time
## 11:45  North Camp                              BUS   On time
## 12:00  Ascot                                   BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
