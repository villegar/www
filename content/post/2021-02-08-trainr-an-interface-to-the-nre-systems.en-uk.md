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

## Example (Last rendered on 2021-02-28 10:09)

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
## Reading (RDG) Station Board on 2021-02-28 10:09:38
## Time   From                                    Plat  Expected
## 10:07  London Paddington                       9     On time
## 10:08  Eastleigh                               7B    On time
## 10:13  Bedwyn                                  15    On time
## 10:13  London Paddington                       14    10:06
## 10:16  London Paddington                       8     On time
## 10:18  London Paddington                       9B    On time
## 10:26  Swansea                                 10    On time
## 10:32  Ascot                                   4     On time
## 10:33  Basingstoke                             2     On time
## 10:40  Birmingham New Street                   7     Delayed
## 10:41  Exeter St Davids                        11    On time
## 10:43  London Paddington                       14    On time
## 10:45  Salisbury                               1     On time
## 10:49  London Paddington                       9     On time
## 10:53  London Paddington                       8     On time
## 10:57  Oxford                                  11A   On time
## 11:02  Ascot                                   4     On time
## 11:07  London Paddington                       9     On time
## 11:07  Reigate                                 6     On time
## 11:10  Didcot Parkway                          11    On time
## 11:10  Eastleigh                               8B    On time
## 11:12  London Paddington                       10    On time
## 11:13  London Paddington                       14    On time
## 11:14  Bristol Parkway                         11    On time
## 11:15  London Paddington                       9     On time
## 11:19  London Paddington                       8     On time
## 11:21  Bedwyn                                  3     On time
## 11:24  Worcester Shrub Hill                    10    On time
## 11:32  Ascot                                   4     On time
## 11:33  Basingstoke                             2     On time
## 11:39  Manchester Piccadilly                   8     On time
## 11:43  London Paddington                       14    On time
## 11:45  Salisbury                               1     On time
## 11:46  Swansea                                 11    On time
## 11:53  London Paddington                       7     On time
## 11:57  Oxford                                  15    On time
## 12:02  Ascot                                   4     On time
## 12:03  London Paddington                       8     On time
## 12:07  Reigate                                 6     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-28 10:09:40
## Time   To                                      Plat  Expected
## 10:09  Carmarthen                              9     On time
## 10:12  Salisbury                               1     On time
## 10:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 10:22  Ealing Broadway                         14    On time
## 10:22  Oxford                                  9B    On time
## 10:24  Ascot                                   5     On time
## 10:28  Didcot Parkway                          8     On time
## 10:29  London Paddington                       10    On time
## 10:35  Newbury                                 3     On time
## 10:38  Basingstoke                             2     On time
## 10:41  Reigate                                 6     On time
## 10:43  London Paddington                       11    On time
## 10:51  Ascot                                   4     On time
## 10:52  Ealing Broadway                         14    On time
## 10:52  Plymouth                                9     On time
## 10:54  Weston-super-Mare                       8     On time
## 11:00  London Paddington                       11A   On time
## 11:09  Swansea                                 9     On time
## 11:12  Ealing Broadway                         11    On time
## 11:12  Salisbury                               1     On time
## 11:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 11:16  London Paddington                       11    On time
## 11:17  Westbury                                10    On time
## 11:20  Oxford                                  8     On time
## 11:22  Ealing Broadway                         14    On time
## 11:24  Ascot                                   4     On time
## 11:28  Didcot Parkway                          9     On time
## 11:30  London Paddington                       10    On time
## 11:35  Bedwyn                                  3     On time
## 11:38  Basingstoke                             2     On time
## 11:41  Reigate                                 6     On time
## 11:50  London Paddington                       11    On time
## 11:51  Ascot                                   4     On time
## 11:52  Ealing Broadway                         14    On time
## 11:52  Eastleigh                               8     On time
## 11:54  Paignton                                7     On time
##        via Bristol                             
## 12:01  London Paddington                       15    On time
## 12:06  Penzance                                8     On time
```
