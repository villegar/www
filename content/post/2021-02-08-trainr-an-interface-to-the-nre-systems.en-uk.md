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

## Example (Last rendered on 2021-03-07 20:07)

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
## Reading (RDG) Station Board on 2021-03-07 20:07:39
## Time   From                                    Plat  Expected
## 20:14  Bristol Temple Meads                    9     On time
## 20:15  Ealing Broadway                         14    20:07
## 20:16  Ash                                     4     On time
## 20:20  Ealing Broadway                         12    On time
## 20:20  Newbury                                 1     On time
## 20:25  Penzance                                11    On time
## 20:28  Didcot Parkway                          15    On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   13B   On time
## 20:45  Ealing Broadway                         14    On time
## 20:48  Ealing Broadway                         10    On time
## 20:50  Port Talbot Parkway                     9     On time
## 21:00  Worcester Foregate Street               15    On time
## 21:05  Penzance                                11    On time
## 21:07  Bournemouth                             7B    On time
## 21:15  Ealing Broadway                         14    On time
## 21:16  Ash                                     4     On time
## 21:16  Bristol Temple Meads                    12    On time
## 21:20  Ealing Broadway                         13    On time
## 21:28  Didcot Parkway                          15    On time
## 21:29  Bedwyn                                  1     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:45  Ealing Broadway                         14    On time
## 21:47  Ealing Broadway                         10    On time
## 21:50  Port Talbot Parkway                     9     On time
## 22:00  Hereford                                8     On time
## 20:15  Virginia Water                          BUS   On time
## 20:25  Virginia Water                          BUS   On time
## 20:45  Virginia Water                          BUS   On time
## 20:55  Virginia Water                          BUS   On time
## 21:15  Virginia Water                          BUS   On time
## 21:25  Virginia Water                          BUS   On time
## 21:45  Virginia Water                          BUS   On time
## 21:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-07 20:07:41
## Time   To                                      Plat  Expected
## 20:07  Ealing Broadway                         10    On time
## 20:09  Port Talbot Parkway                     9B    On time
## 20:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 20:18  Great Malvern                           7B    On time
## 20:22  Ealing Broadway                         14    On time
## 20:30  Didcot Parkway                          12    On time
## 20:32  Ealing Broadway                         15    On time
## 20:38  Basingstoke                             2     On time
## 20:41  Ash                                     4     On time
## 20:42  Newbury                                 1     On time
## 20:52  Bournemouth                             13B   On time
## 20:52  Ealing Broadway                         14    On time
## 20:55  Plymouth                                11    On time
## 20:55  Weston-super-Mare                       8B    On time
## 21:12  Birmingham New Street                   7B    On time
##        via Coventry                            
## 21:12  Ealing Broadway                         10    On time
## 21:15  Cardiff Central                         9     On time
## 21:18  Worcester Shrub Hill                    8     On time
## 21:25  Ealing Broadway                         14    On time
## 21:30  Didcot Parkway                          13    On time
## 21:32  Ealing Broadway                         15    On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:50  Ash                                     4     On time
## 21:52  Southampton Central                     7B    On time
## 21:55  Ealing Broadway                         14    On time
## 21:55  Exeter St Davids                        11    On time
## 21:58  Bristol Parkway                         12    On time
## 20:06  Virginia Water                          BUS   On time
## 20:26  Virginia Water                          BUS   On time
## 20:36  Virginia Water                          BUS   On time
## 20:56  Virginia Water                          BUS   On time
## 21:06  Virginia Water                          BUS   On time
## 21:26  Virginia Water                          BUS   On time
## 21:36  Virginia Water                          BUS   On time
## 21:56  Virginia Water                          BUS   On time
## 22:06  Virginia Water                          BUS   On time
```
