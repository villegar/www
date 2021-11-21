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

## Example (Last rendered on 2021-11-21 10:03)

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
## Reading (RDG) Station Board on 2021-11-21 10:03:34
## Time   From                                    Plat  Expected
## 09:58  Didcot Parkway                          13A   10:00
## 09:59  London Paddington                       8     On time
## 10:05  Clapham Junction                        4     On time
## 10:08  Eastleigh                               12    On time
## 10:09  Ash                                     6     On time
## 10:11  London Paddington                       9     On time
## 10:13  London Paddington                       14    On time
## 10:14  Bedwyn                                  15    On time
## 10:23  Slough                                  12    On time
## 10:26  London Paddington                       7     On time
## 10:30  Cardiff Central                         10    On time
## 10:33  Basingstoke                             2     10:41
## 10:35  Clapham Junction                        4     On time
## 10:39  Birmingham New Street                   13    On time
## 10:42  Exeter St Davids                        11    On time
## 10:44  London Paddington                       14    On time
## 10:45  Salisbury                               1     On time
## 10:49  Bristol Parkway                         10A   On time
## 10:54  London Paddington                       9B    On time
## 10:57  Great Malvern                           11    On time
## 10:59  London Paddington                       8     On time
## 11:05  Clapham Junction                        4     On time
## 11:08  Eastleigh                               7     On time
## 11:09  Ash                                     6     On time
## 11:09  Bristol Parkway                         11    On time
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       9     On time
## 11:13  London Paddington                       14    On time
## 11:19  Bedwyn                                  1     On time
## 11:23  Slough                                  12    On time
## 11:27  London Paddington                       7     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Clapham Junction                        4     On time
## 11:39  Manchester Piccadilly                   7     On time
## 11:43  Swansea                                 11    On time
## 11:44  London Paddington                       14    On time
## 11:47  Salisbury                               1     On time
## 11:54  London Paddington                       9     On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-21 10:03:36
## Time   To                                      Plat  Expected
## 10:05  Carmarthen                              8     On time
## 10:06  Ealing Broadway                         14    On time
## 10:12  Salisbury                               1     On time
## 10:13  Hereford                                9     On time
## 10:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 10:21  Clapham Junction                        4     On time
## 10:25  Didcot Parkway                          12    On time
## 10:25  Slough                                  13A   On time
## 10:27  Penzance                                7     On time
## 10:36  Ealing Broadway                         14    On time
## 10:38  Basingstoke                             2     On time
## 10:40  London Paddington                       10    On time
## 10:41  Ash                                     6     On time
## 10:44  Newbury                                 3     On time
## 10:45  London Paddington                       11    On time
## 10:50  London Paddington                       10A   On time
## 10:51  Clapham Junction                        4     On time
## 10:55  Weston-super-Mare                       9B    On time
## 11:01  London Paddington                       11    On time
## 11:06  Ealing Broadway                         14    On time
## 11:09  Swansea                                 8     On time
## 11:12  Salisbury                               1     On time
## 11:14  Great Malvern                           9     On time
## 11:15  London Paddington                       11    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:21  Clapham Junction                        4     On time
## 11:25  Didcot Parkway                          12    On time
## 11:25  Slough                                  15    On time
## 11:30  Plymouth                                7     On time
## 11:36  Ealing Broadway                         14    On time
## 11:38  Basingstoke                             2     On time
## 11:41  Ash                                     6     On time
## 11:44  Bedwyn                                  1     On time
## 11:49  London Paddington                       11    On time
## 11:51  Clapham Junction                        4     On time
## 11:52  Eastleigh                               7     On time
## 11:55  Paignton                                9     On time
##        via Bristol                             
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
