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

## Example (Last rendered on 2021-02-28 18:13)

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
## Reading (RDG) Station Board on 2021-02-28 18:13:42
## Time   From                                    Plat  Expected
## 18:10  Didcot Parkway                          15    18:12
## 18:14  Bristol Temple Meads                    13    On time
## 18:15  London Paddington                       8     On time
## 18:18  London Paddington                       9B    On time
## 18:23  London Paddington                       9B    On time
## 18:23  Newbury                                 1     On time
## 18:25  London Paddington                       7     On time
## 18:28  Plymouth                                14    On time
## 18:32  Ascot                                   4     On time
## 18:32  Basingstoke                             2     On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:41  Bristol Temple Meads                    12A   On time
## 18:43  London Paddington                       14    On time
## 18:46  Swansea                                 15    On time
## 18:53  London Paddington                       8     On time
## 18:57  Oxford                                  15    On time
## 19:02  Ascot                                   4     On time
## 19:07  London Paddington                       9     On time
## 19:07  Reigate                                 6     On time
## 19:09  Eastleigh                               8     On time
## 19:10  Didcot Parkway                          15    On time
## 19:13  London Paddington                       14    On time
## 19:15  London Paddington                       12    On time
## 19:17  Paignton                                15    On time
## 19:18  London Paddington                       9     On time
## 19:21  Bedwyn                                  1     On time
## 19:22  Penzance                                15    On time
## 19:28  London Paddington                       9     On time
## 19:32  Ascot                                   6     On time
## 19:33  Basingstoke                             2     On time
## 19:39  Manchester Piccadilly                   8     On time
## 19:41  Bristol Temple Meads                    12    On time
## 19:43  London Paddington                       14    On time
## 19:46  London Paddington                       9     On time
## 19:49  Carmarthen                              15    On time
## 19:53  London Paddington                       9     On time
## 19:57  Oxford                                  14    On time
## 20:02  Ascot                                   4     On time
## 20:07  London Paddington                       8     On time
## 20:07  Reigate                                 5     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-28 18:13:44
## Time   To                                      Plat  Expected
## 18:14  Ealing Broadway                         15    On time
## 18:15  London Paddington                       13    On time
## 18:15  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 18:20  Oxford                                  9B    On time
## 18:22  Ealing Broadway                         14    On time
## 18:24  Ascot                                   5     On time
## 18:24  Penzance                                9B    On time
## 18:27  Plymouth                                7     On time
##        via Bristol                             
## 18:31  Didcot Parkway                          8     On time
## 18:35  London Paddington                       14    On time
## 18:38  Basingstoke                             2     On time
## 18:41  Reigate                                 6     On time
## 18:45  London Paddington                       12A   On time
## 18:49  London Paddington                       15    On time
## 18:50  Newbury                                 1     On time
## 18:51  Ascot                                   4     On time
## 18:52  Ealing Broadway                         14    On time
## 18:54  Weston-super-Mare                       8     On time
## 19:01  London Paddington                       15    On time
## 19:10  Swansea                                 9     On time
## 19:14  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:19  London Paddington                       15    On time
## 19:20  Oxford                                  9     On time
## 19:21  Reigate                                 6     On time
## 19:22  Ealing Broadway                         14    On time
## 19:24  Ascot                                   4     On time
## 19:25  London Paddington                       15    On time
## 19:28  Didcot Parkway                          12    On time
## 19:30  Hereford                                9     On time
## 19:35  Bedwyn                                  1     On time
## 19:38  Basingstoke                             2     On time
## 19:45  London Paddington                       12    On time
## 19:47  Oxford                                  9     On time
## 19:51  Ascot                                   6     On time
## 19:52  Ealing Broadway                         14    On time
## 19:52  Eastleigh                               8     On time
## 19:54  Bristol Temple Meads                    9     On time
## 19:55  London Paddington                       15    On time
## 20:01  London Paddington                       14    On time
## 20:09  Swansea                                 8     On time
```
