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

## Example (Last rendered on 2022-06-25 06:03)

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
## Reading (RDG) Station Board on 2022-06-25 06:03:26
## Time   From                                    Plat  Expected
## 07:56  London Paddington                       9     On time
## 08:07  Didcot Parkway                          15    On time
## 08:09  Oxford                                  10    On time
## 08:14  London Paddington                       9     On time
## 08:23  Bristol Parkway                         10    On time
## 08:37  London Paddington                       8     On time
## 08:39  Bristol Temple Meads                    11    On time
## 08:39  London Paddington                       14    On time
## 08:42  Basingstoke                             2     On time
## 08:43  London Paddington                       9     On time
## 08:55  London Paddington                       8     On time
## 09:01  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-25 06:03:28
## Time   To                                      Plat  Expected
## 07:37  Basingstoke                             15B   On time
## 07:38  Cardiff Central                         9     On time
## 07:49  Oxford                                  8     On time
## 07:51  London Paddington                       13    On time
## 07:52  Didcot Parkway                          15A   On time
## 08:00  Ealing Broadway                         14    On time
## 08:00  Plymouth                                9     On time
##        via Bristol                             
## 08:14  Bristol Parkway                         9     On time
## 08:14  London Paddington                       10    On time
## 08:23  Basingstoke                             -     Cancelled
## 08:25  London Paddington                       10    On time
## 08:27  Ealing Broadway                         14    On time
## 08:39  Cardiff Central                         8     On time
## 08:41  London Paddington                       11    On time
## 08:46  Oxford                                  9     On time
## 08:49  London Paddington                       13    On time
## 08:53  Didcot Parkway                          15A   On time
## 08:57  Ealing Broadway                         14    On time
## 08:57  Plymouth                                8     On time
##        via Bristol
```
