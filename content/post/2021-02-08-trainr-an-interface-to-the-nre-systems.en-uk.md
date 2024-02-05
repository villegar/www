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

## Example (Last rendered on 2024-02-05 17:06)

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
## Reading (RDG) Station Board on 2024-02-05 17:06:23.03259
## Time   From                                    Plat  Expected
## 17:11  Abbey Wood                              14    On time
## 17:16  London Waterloo                         6     On time
## 17:26  Basingstoke                             15    On time
## 17:31  Didcot Parkway                          12    On time
## 17:31  Redhill                                 15    On time
## 17:34  Abbey Wood                              13    On time
## 17:34  Newbury                                 7     On time
## 17:41  Abbey Wood                              14    On time
## 17:42  Bristol Temple Meads                    10    On time
## 17:42  London Waterloo                         4     17:47
## 17:53  London Paddington                       9     On time
## 17:58  London Paddington                       9     On time
## 18:04  Abbey Wood                              13    On time
## 18:12  Abbey Wood                              14    On time
## 18:14  London Waterloo                         6     On time
## 18:20  Basingstoke                             2     On time
## 18:27  Didcot Parkway                          15    On time
## 18:34  Abbey Wood                              13    On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:42  Abbey Wood                              14    On time
## 18:53  London Paddington                       9     On time
## 19:04  Abbey Wood                              13    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-02-05 17:06:24.552939
## Time   To                                      Plat  Expected
## 17:09  London Waterloo                         6     On time
## 17:15  Abbey Wood                              13    On time
## 17:15  Basingstoke                             2     On time
## 17:20  Redhill                                 4     On time
## 17:32  Abbey Wood                              14    On time
## 17:39  London Waterloo                         6     On time
## 17:45  London Paddington                       10    On time
## 17:46  Abbey Wood                              13    On time
## 17:55  Bristol Temple Meads                    9     On time
## 17:58  Didcot Parkway                          12A   On time
## 17:59  Abbey Wood                              14    On time
## 18:00  Oxford                                  9     On time
## 18:06  Newbury                                 7     On time
## 18:09  London Waterloo                         4     On time
## 18:15  Abbey Wood                              13    On time
## 18:28  Abbey Wood                              14    On time
## 18:32  Basingstoke                             2     On time
## 18:39  London Waterloo                         6     On time
## 18:43  London Paddington                       10    On time
## 18:45  Abbey Wood                              13    On time
## 18:55  Cardiff Central                         9     On time
## 18:59  Abbey Wood                              14    On time
## 19:00  Didcot Parkway                          15A   On time
```
