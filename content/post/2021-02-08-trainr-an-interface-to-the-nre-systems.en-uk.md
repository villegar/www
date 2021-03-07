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

## Example (Last rendered on 2021-03-07 10:10)

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
## Reading (RDG) Station Board on 2021-03-07 10:10:22
## Time   From                                    Plat  Expected
## 10:08  Southampton Central                     12B   On time
## 10:13  Ash                                     4     10:10
## 10:13  Bedwyn                                  14    On time
## 10:15  Ealing Broadway                         15    10:10
## 10:20  Ealing Broadway                         8     On time
## 10:28  Didcot Parkway                          15    On time
## 10:33  Basingstoke                             2     On time
## 10:35  Cardiff Central                         9     10:37
## 10:39  Birmingham New Street                   7     On time
## 10:40  Ealing Broadway                         10    On time
## 10:41  Exeter St Davids                        13    On time
## 10:45  Ealing Broadway                         14    On time
## 11:00  Great Malvern                           11    On time
## 11:10  Bournemouth                             12B   On time
## 11:15  Ealing Broadway                         14    On time
## 11:16  Ash                                     4     On time
## 11:20  Ealing Broadway                         12    On time
## 11:21  Bedwyn                                  3     On time
## 11:28  Didcot Parkway                          15    On time
## 11:33  Basingstoke                             2     On time
## 11:39  Manchester Piccadilly                   12B   On time
## 11:45  Ealing Broadway                         14    On time
## 11:48  Ealing Broadway                         10    On time
## 11:50  Port Talbot Parkway                     9     On time
## 11:58  Plymouth                                11    On time
## 12:00  Great Malvern                           8     On time
## 10:15  Virginia Water                          BUS   On time
## 10:25  Virginia Water                          BUS   On time
## 10:45  Virginia Water                          BUS   On time
## 10:55  Virginia Water                          BUS   On time
## 11:15  Virginia Water                          BUS   On time
## 11:25  Virginia Water                          BUS   On time
## 11:45  Virginia Water                          BUS   On time
## 11:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-07 10:10:24
## Time   To                                      Plat  Expected
## 10:12  Hereford                                9B    On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:22  Ealing Broadway                         15    On time
## 10:27  Penzance                                7B    On time
## 10:30  Didcot Parkway                          8     On time
## 10:30  Ealing Broadway                         15    On time
## 10:35  Newbury                                 3     On time
## 10:38  Basingstoke                             2     On time
## 10:41  Ash                                     4     On time
## 10:50  Ealing Broadway                         10    On time
## 10:52  Ealing Broadway                         14    On time
## 10:55  Bristol Temple Meads                    8     On time
## 11:09  Port Talbot Parkway                     9     On time
## 11:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 11:18  Worcester Shrub Hill                    13    On time
## 11:22  Ealing Broadway                         14    On time
## 11:27  Plymouth                                11    On time
## 11:30  Didcot Parkway                          12    On time
## 11:30  Ealing Broadway                         15    On time
## 11:35  Bedwyn                                  3     On time
## 11:38  Basingstoke                             2     On time
## 11:41  Ash                                     4     On time
## 11:52  Bournemouth                             12B   On time
## 11:52  Ealing Broadway                         14    On time
## 11:55  Bristol Temple Meads                    8     On time
## 12:07  Ealing Broadway                         10    On time
## 12:09  Port Talbot Parkway                     9     On time
## 10:26  Virginia Water                          BUS   On time
## 10:36  Virginia Water                          BUS   On time
## 10:56  Virginia Water                          BUS   On time
## 11:06  Virginia Water                          BUS   On time
## 11:26  Virginia Water                          BUS   On time
## 11:36  Virginia Water                          BUS   On time
## 11:56  Virginia Water                          BUS   On time
## 12:06  Virginia Water                          BUS   On time
```
