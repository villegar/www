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

## Example (Last rendered on 2021-02-28 12:09)

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
## Reading (RDG) Station Board on 2021-02-28 12:09:38
## Time   From                                    Plat  Expected
## 12:07  London Paddington                       9     On time
## 12:09  Bristol Temple Meads                    12    12:11
## 12:10  Didcot Parkway                          15    On time
## 12:13  London Paddington                       14    12:06
## 12:15  London Paddington                       9     On time
## 12:18  London Paddington                       8B    On time
## 12:20  Newbury                                 3     On time
## 12:32  Ascot                                   4     On time
## 12:33  Basingstoke                             2     On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:43  London Paddington                       14    On time
## 12:45  Salisbury                               1     On time
## 12:46  Swansea                                 15    On time
## 12:53  London Paddington                       8     On time
## 12:57  Oxford                                  15A   On time
## 13:02  Ascot                                   4     On time
## 13:06  Eastleigh                               8B    On time
## 13:07  London Paddington                       9     On time
## 13:08  Reigate                                 6     On time
## 13:10  Didcot Parkway                          15    On time
## 13:13  London Paddington                       14    On time
## 13:14  Weston-super-Mare                       13    On time
## 13:15  London Paddington                       9     On time
## 13:19  London Paddington                       8     On time
## 13:21  Bedwyn                                  3     On time
## 13:26  London Paddington                       7     On time
## 13:28  Penzance                                13    On time
## 13:32  Ascot                                   4     On time
## 13:33  Basingstoke                             2     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Westbury                                10    On time
## 13:41  Bristol Temple Meads                    13    On time
## 13:43  London Paddington                       14    On time
## 13:45  Salisbury                               1     On time
## 13:47  Swansea                                 15    On time
## 13:50  London Paddington                       8     On time
## 13:57  Oxford                                  15    On time
## 14:03  London Paddington                       9     On time
## 14:05  Ascot                                   4     On time
## 14:07  Reigate                                 6     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-28 12:09:41
## Time   To                                      Plat  Expected
## 12:10  Carmarthen                              9     On time
## 12:11  London Paddington                       12    12:12
## 12:12  Ealing Broadway                         15    On time
## 12:12  Salisbury                               1     On time
## 12:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 12:20  Oxford                                  8B    On time
## 12:22  Ealing Broadway                         14    On time
## 12:24  Ascot                                   5     On time
## 12:28  Didcot Parkway                          9     On time
## 12:35  Newbury                                 3     On time
## 12:38  Basingstoke                             2     On time
## 12:41  Reigate                                 6     On time
## 12:47  London Paddington                       15    On time
## 12:51  Ascot                                   4     On time
## 12:52  Ealing Broadway                         14    On time
## 12:54  Weston-super-Mare                       8     On time
## 13:01  London Paddington                       15A   On time
## 13:10  Swansea                                 9     On time
## 13:12  Ealing Broadway                         15    On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:15  London Paddington                       13    On time
## 13:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 13:20  Oxford                                  8     On time
## 13:22  Ealing Broadway                         14    On time
## 13:24  Ascot                                   4     On time
## 13:28  Plymouth                                7     On time
## 13:30  Didcot Parkway                          9     On time
## 13:35  Bedwyn                                  3     On time
## 13:35  London Paddington                       13    On time
## 13:38  Basingstoke                             2     On time
## 13:41  Reigate                                 6     On time
## 13:42  London Paddington                       10    On time
## 13:45  London Paddington                       13    On time
## 13:49  London Paddington                       15    On time
## 13:51  Ascot                                   4     On time
## 13:51  Bristol Temple Meads                    8     On time
## 13:52  Ealing Broadway                         14    On time
## 13:52  Eastleigh                               7     On time
## 14:01  London Paddington                       15    On time
## 14:06  Penzance                                9     On time
```
