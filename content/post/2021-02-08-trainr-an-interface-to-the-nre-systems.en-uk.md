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

## Example (Last rendered on 2022-08-20 14:04)

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
## Reading (RDG) Station Board on 2022-08-20 14:04:33
## Time   From                                    Plat  Expected
## 15:09  London Paddington                       14    On time
## 15:11  London Paddington                       8     On time
## 15:19  Cardiff Central                         11    On time
## 15:25  Oxford                                  10    On time
## 15:37  London Paddington                       9     On time
## 15:39  Didcot Parkway                          10    On time
## 15:39  London Paddington                       14    On time
## 15:40  Manchester Piccadilly                   8B    On time
## 15:44  Exeter St Davids                        11    Delayed
## 15:46  London Paddington                       9     On time
## 15:49  Cardiff Central                         10    On time
## 15:57  Basingstoke                             2     On time
## 15:58  London Paddington                       9     On time
## 16:07  Didcot Parkway                          15    On time
## 16:09  London Paddington                       14    On time
## 16:11  London Paddington                       9     On time
## 16:19  Cardiff Central                         11    On time
## 16:24  Oxford                                  10    On time
## 16:39  Didcot Parkway                          10    On time
## 16:39  London Paddington                       14    On time
## 16:39  Manchester Piccadilly                   7B    On time
## 16:44  Basingstoke                             2     On time
## 16:44  Exeter St Davids                        11    On time
## 16:46  London Paddington                       9     On time
## 16:49  Cardiff Central                         10    On time
## 16:52  London Paddington                       8     On time
## 16:59  London Paddington                       9     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-20 14:04:38
## Time   To                                      Plat  Expected
## 15:13  Cardiff Central                         8     On time
## 15:15  Birmingham New Street                   13    On time
##        via Coventry                            
## 15:22  London Paddington                       11    On time
## 15:27  Ealing Broadway                         14    On time
## 15:27  London Paddington                       10    On time
## 15:35  Basingstoke                             2     On time
## 15:39  Cardiff Central                         9     On time
## 15:42  London Paddington                       10    On time
## 15:46  London Paddington                       11    Delayed
## 15:48  Oxford                                  9     On time
## 15:50  London Paddington                       10    On time
## 15:51  Didcot Parkway                          15A   On time
## 15:52  Southampton Central                     8B    On time
## 15:57  Ealing Broadway                         14    On time
## 15:58  Didcot Parkway                          9     On time
## 16:13  Cardiff Central                         9     On time
## 16:21  London Paddington                       11    On time
## 16:27  Ealing Broadway                         14    On time
## 16:27  London Paddington                       10    On time
## 16:33  Basingstoke                             2     On time
## 16:41  London Paddington                       10    On time
## 16:46  London Paddington                       11    On time
## 16:48  Oxford                                  9     On time
## 16:50  Didcot Parkway                          15    On time
## 16:50  London Paddington                       10    On time
## 16:52  Southampton Central                     7B    On time
## 16:54  Cardiff Central                         8     On time
## 16:57  Ealing Broadway                         14    On time
## 16:59  Didcot Parkway                          9     On time
## 17:03  London Paddington                       15    On time
```
