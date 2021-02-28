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

## Example (Last rendered on 2021-02-28 20:07)

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
## Reading (RDG) Station Board on 2021-02-28 20:07:25
## Time   From                                    Plat  Expected
## 20:07  London Paddington                       8     On time
## 20:07  Reigate                                 6     20:04
## 20:10  Didcot Parkway                          13    On time
## 20:13  London Paddington                       14    20:07
## 20:14  London Paddington                       12    On time
## 20:18  London Paddington                       8B    On time
## 20:18  Penzance                                13    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:32  Ascot                                   6     On time
## 20:33  Basingstoke                             2     On time
## 20:35  Westbury                                11A   On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:43  London Paddington                       14    On time
## 20:49  Swansea                                 15    On time
## 20:52  Plymouth                                13A   On time
## 20:54  London Paddington                       12    On time
## 20:59  Oxford                                  15A   On time
## 21:02  Ascot                                   4     On time
## 21:07  Eastleigh                               7B    On time
## 21:07  London Paddington                       7B    On time
## 21:07  Reigate                                 5     On time
## 21:11  Didcot Parkway                          15    On time
## 21:12  London Paddington                       7B    On time
## 21:13  London Paddington                       14    On time
## 21:14  London Paddington                       12    On time
## 21:15  Taunton                                 13A   On time
## 21:21  Bedwyn                                  3     On time
## 21:23  London Paddington                       7B    On time
## 21:29  Penzance                                15    On time
## 21:32  Ascot                                   6     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:39  Reigate                                 15    On time
## 21:43  London Paddington                       14    On time
## 21:50  Swansea                                 15    On time
## 21:53  London Paddington                       7     On time
## 21:59  Oxford                                  15    On time
## 22:02  Ascot                                   6     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-28 20:07:27
## Time   To                                      Plat  Expected
## 20:09  Swansea                                 8     On time
## 20:12  Reigate                                 6     On time
## 20:14  Ealing Broadway                         13    On time
## 20:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 20:20  London Paddington                       13    On time
## 20:20  Oxford                                  8B    On time
## 20:22  Ealing Broadway                         14    On time
## 20:24  Ascot                                   5     On time
## 20:27  Plymouth                                7     On time
## 20:28  Didcot Parkway                          12    On time
## 20:37  London Paddington                       11A   On time
## 20:38  Basingstoke                             2     On time
## 20:42  Newbury                                 1     On time
## 20:51  Ascot                                   6     On time
## 20:52  Ealing Broadway                         14    On time
## 20:52  Eastleigh                               7     On time
## 20:55  London Paddington                       15    On time
## 20:56  Weston-super-Mare                       12    On time
## 20:58  London Paddington                       13A   On time
## 21:01  London Paddington                       15A   On time
## 21:09  Swansea                                 7B    On time
## 21:12  Birmingham New Street                   7B    On time
##        via Coventry                            
## 21:13  Reigate                                 5     On time
## 21:14  Ealing Broadway                         15    On time
## 21:17  London Paddington                       13A   On time
## 21:19  Oxford                                  7B    On time
## 21:24  Ascot                                   4     On time
## 21:25  Ealing Broadway                         14    On time
## 21:25  Exeter St Davids                        7B    On time
## 21:28  Didcot Parkway                          12    On time
## 21:31  London Paddington                       15    On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  3     On time
## 21:51  Ascot                                   6     On time
## 21:52  Eastleigh                               7B    On time
## 21:52  London Paddington                       15    On time
## 21:54  Bristol Temple Meads                    7     On time
## 21:55  Ealing Broadway                         14    On time
## 22:00  London Paddington                       15    On time
```
