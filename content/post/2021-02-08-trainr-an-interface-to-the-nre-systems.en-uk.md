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

## Example (Last rendered on 2021-04-24 22:07)

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
## Reading (RDG) Station Board on 2021-04-24 22:07:04
## Time   From                                    Plat  Expected
## 22:44  London Paddington                       12    On time
## 23:00  Basingstoke                             13    23:05
## 23:01  Didcot Parkway                          15    23:06
## 23:06  Hereford                                14    On time
## 23:10  Newbury                                 12    On time
## 23:14  London Paddington                       14    On time
## 23:31  London Paddington                       12    On time
## 23:43  London Paddington                       13    On time
## 23:46  London Paddington                       12    On time
## 23:56  Taunton                                 15    On time
## 23:58  London Paddington                       12    On time
## 00:06  Basingstoke                             12B   On time
## 00:08  Didcot Parkway                          15A   On time
## 00:14  Newbury                                 13    On time
## 23:09  Wokingham                               BUS   On time
## 23:23  Wokingham                               BUS   On time
## 23:29  Wokingham                               BUS   On time
## 00:03  Wokingham                               BUS   On time
## 00:09  Wokingham                               BUS   On time
## 00:22  Wokingham                               BUS   On time
## 00:23  Wokingham                               BUS   On time
## 00:39  Wokingham                               BUS   On time
## 00:50  Slough                                  BUS   On time
## 01:03  Wokingham                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-24 22:07:07
## Time   To                                      Plat  Expected
## 23:05  Didcot Parkway                          12    On time
## 23:08  Basingstoke                             13B   On time
## 23:08  London Paddington                       14    On time
## 23:14  Newbury                                 13B   On time
## 23:48  Didcot Parkway                          12    On time
## 23:59  London Paddington                       15    On time
## 00:02  Bristol Parkway                         12    On time
## 00:17  Ealing Broadway                         15A   On time
## 23:15  Wokingham                               BUS   On time
## 23:20  Wokingham                               BUS   On time
## 23:34  Wokingham                               BUS   On time
## 23:52  Wokingham                               BUS   On time
```
