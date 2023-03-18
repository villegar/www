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

## Example (Last rendered on 2023-03-18 12:04)

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
## Reading (RDG) Station Board on 2023-03-18 12:04:11
## Time   From                                    Plat  Expected
## 12:10  London Paddington                       12B   On time
## 12:15  Cardiff Central                         11    12:20
## 12:24  Oxford                                  10    On time
## 12:31  Didcot Parkway                          14A   On time
## 12:31  Newbury                                 11A   On time
## 12:33  Abbey Wood                              14    12:35
## 12:33  London Paddington                       7B    On time
## 12:37  London Paddington                       9     12:46
## 12:39  Manchester Piccadilly                   7     On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:42  Newbury                                 1     On time
## 12:46  London Paddington                       9     On time
## 12:51  Basingstoke                             2     On time
## 12:54  London Paddington                       9     On time
## 13:03  Abbey Wood                              14    On time
## 13:05  Southampton Central                     13    On time
## 13:11  London Paddington                       12B   On time
## 13:17  Cardiff Central                         11    On time
## 13:24  Oxford                                  10    On time
## 13:31  Newbury                                 11A   On time
## 13:32  London Paddington                       8B    On time
## 13:33  Abbey Wood                              14    On time
## 13:33  Didcot Parkway                          15A   On time
## 13:37  London Paddington                       9     On time
## 13:39  Exeter St Davids                        10    On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:41  Newbury                                 1     On time
## 13:46  London Paddington                       9     On time
## 13:51  Basingstoke                             2     On time
## 13:56  London Paddington                       9     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-18 12:04:16
## Time   To                                      Plat  Expected
## 12:07  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 12:12  Newbury                                 1     On time
## 12:17  London Paddington                       11    12:21
## 12:23  Didcot Parkway                          12B   On time
## 12:24  Abbey Wood                              15    On time
## 12:26  London Paddington                       10    On time
## 12:32  London Paddington                       11A   On time
## 12:35  Newbury                                 7B    On time
## 12:38  Basingstoke                             2     On time
## 12:39  Cardiff Central                         9     12:47
## 12:42  London Paddington                       10    On time
## 12:45  Ealing Broadway                         14A   On time
## 12:49  Oxford                                  9     On time
## 12:52  Southampton Central                     7     On time
## 12:54  Abbey Wood                              15    On time
## 12:57  Bristol Temple Meads                    9     On time
## 13:10  Newbury                                 1     On time
## 13:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 13:20  London Paddington                       11    On time
## 13:23  Didcot Parkway                          12B   On time
## 13:24  Abbey Wood                              15    On time
## 13:26  London Paddington                       10    On time
## 13:32  London Paddington                       11A   On time
## 13:34  Newbury                                 8B    On time
## 13:38  Basingstoke                             2     On time
## 13:39  Cardiff Central                         9     On time
## 13:42  London Paddington                       10    On time
## 13:45  Ealing Broadway                         15A   On time
## 13:48  Oxford                                  9     On time
## 13:51  London Paddington                       15    On time
## 13:54  Abbey Wood                              14    On time
## 13:58  Exeter St Davids                        9     On time
##        via Bristol
```
