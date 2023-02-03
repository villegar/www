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

## Example (Last rendered on 2023-02-03 08:03)

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
## Reading (RDG) Station Board on 2023-02-03 08:03:47
## Time   From                                    Plat  Expected
## 08:11  London Waterloo                         4     08:13
## 08:13  Abbey Wood                              14    On time
## 08:16  Redhill                                 6     On time
## 08:25  Oxford                                  12    On time
## 08:28  Abbey Wood                              14    On time
## 08:39  Bristol Temple Meads                    11    On time
## 08:42  Basingstoke                             2     On time
## 08:42  London Waterloo                         6     On time
## 08:45  Abbey Wood                              14    On time
## 08:55  London Paddington                       8     On time
## 08:56  Abbey Wood                              13    On time
## 09:13  Abbey Wood                              14    On time
## 09:13  Basingstoke                             2     On time
## 09:16  London Waterloo                         4     On time
## 09:24  Oxford                                  15    On time
## 09:26  Abbey Wood                              13    On time
## 09:38  Abbey Wood                              14    On time
## 09:40  Bristol Temple Meads                    10    On time
## 09:41  London Waterloo                         6     On time
## 09:56  London Paddington                       9     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-03 08:03:50
## Time   To                                      Plat  Expected
## 08:07  Basingstoke                             15B   On time
## 08:10  Abbey Wood                              13    On time
## 08:11  London Waterloo                         6     On time
## 08:25  Abbey Wood                              14    On time
## 08:41  London Paddington                       11    On time
## 08:42  Abbey Wood                              14    On time
## 08:42  London Waterloo                         4     On time
## 08:42  Oxford                                  12B   On time
## 08:57  Abbey Wood                              14    On time
## 08:57  Bristol Temple Meads                    8     On time
## 09:07  Basingstoke                             2     On time
## 09:10  London Waterloo                         6     On time
## 09:18  Abbey Wood                              13    On time
## 09:27  Abbey Wood                              14    On time
## 09:42  London Waterloo                         4     On time
## 09:42  Oxford                                  15B   On time
## 09:43  London Paddington                       10    On time
## 09:48  Abbey Wood                              13    On time
## 09:57  Abbey Wood                              14    On time
## 09:58  Bristol Temple Meads                    9     On time
```
