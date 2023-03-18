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

## Example (Last rendered on 2023-03-18 08:04)

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
## Reading (RDG) Station Board on 2023-03-18 08:04:55
## Time   From                                    Plat  Expected
## 07:56  London Paddington                       9     08:03
## 08:09  Oxford                                  10A   On time
## 08:13  London Paddington                       13B   On time
## 08:18  London Paddington                       15    On time
## 08:23  Bristol Parkway                         10    On time
## 08:30  Newbury                                 11A   On time
## 08:32  Didcot Parkway                          15A   On time
## 08:32  London Paddington                       8B    On time
## 08:33  Abbey Wood                              14    On time
## 08:36  London Paddington                       9     On time
## 08:39  Bristol Temple Meads                    11    On time
## 08:40  London Paddington                       8     On time
## 08:42  Newbury                                 1     On time
## 08:46  London Paddington                       9     On time
## 08:51  Basingstoke                             2     On time
## 09:03  Abbey Wood                              14    On time
## 09:05  Southampton Central                     8     On time
## 09:10  London Paddington                       12B   On time
## 09:18  Cardiff Central                         10    On time
## 09:19  London Paddington                       15    On time
## 09:24  Oxford                                  10    On time
## 09:25  Newbury                                 11    On time
## 09:26  London Paddington                       9     On time
## 09:31  Didcot Parkway                          15    On time
## 09:33  Abbey Wood                              14    On time
## 09:33  London Paddington                       7     On time
## 09:40  Bristol Temple Meads                    11    On time
## 09:41  Newbury                                 1     On time
## 09:46  London Paddington                       9     On time
## 09:48  Basingstoke                             2     On time
## 09:56  London Paddington                       9     On time
## 10:03  Abbey Wood                              14    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-18 08:05:02
## Time   To                                      Plat  Expected
## 08:00  Exeter St Davids                        9     08:05
##        via Bristol                             
## 08:14  London Paddington                       10A   On time
## 08:23  Didcot Parkway                          13B   On time
## 08:24  Abbey Wood                              15    On time
## 08:25  London Paddington                       10    On time
## 08:31  London Paddington                       11A   On time
## 08:33  Newbury                                 8B    On time
## 08:38  Basingstoke                             12A   On time
## 08:38  Cardiff Central                         9     On time
## 08:41  London Paddington                       11    On time
## 08:42  Exeter St Davids                        8     On time
##        via Bristol                             
## 08:45  Ealing Broadway                         15A   On time
## 08:48  Oxford                                  9     On time
## 08:54  Abbey Wood                              14    On time
## 09:06  Newbury                                 1     On time
## 09:10  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:19  London Paddington                       10    On time
## 09:24  Abbey Wood                              14    On time
## 09:24  Didcot Parkway                          12B   On time
## 09:26  London Paddington                       10    On time
## 09:28  Cardiff Central                         9     On time
## 09:32  London Paddington                       11    On time
## 09:35  Newbury                                 7     On time
## 09:38  Basingstoke                             2     On time
## 09:43  London Paddington                       11    On time
## 09:45  Ealing Broadway                         15    On time
## 09:48  Oxford                                  9     On time
## 09:54  Abbey Wood                              14    On time
## 09:58  Exeter St Davids                        9     On time
##        via Bristol
```
