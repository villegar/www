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

## Example (Last rendered on 2022-10-06 18:09)

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
## Reading (RDG) Station Board on 2022-10-06 18:09:52
## Time   From                                    Plat  Expected
## 19:10  London Paddington                       13    19:07
## 19:14  London Waterloo                         5     On time
## 19:15  London Paddington                       14    On time
## 19:41  London Paddington                       13    On time
## 19:41  Manchester Piccadilly                   7     19:50
## 19:43  London Waterloo                         6     On time
## 19:45  London Paddington                       14    On time
## 19:54  Westbury                                -     Cancelled
## 20:07  Bournemouth                             7     On time
## 20:13  London Waterloo                         6     On time
## 20:14  London Paddington                       14    On time
## 20:41  London Waterloo                         4     On time
## 20:43  London Paddington                       14    On time
## 20:43  Manchester Piccadilly                   7     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-06 18:09:55
## Time   To                                      Plat  Expected
## 19:12  London Waterloo                         6     On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:27  London Paddington                       14    On time
## 19:42  London Waterloo                         5     On time
## 19:50  Bournemouth                             7     19:50
## 19:55  London Paddington                       -     Cancelled
## 19:57  London Paddington                       13    On time
## 20:09  London Waterloo                         6     On time
## 20:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 20:27  London Paddington                       14    On time
## 20:42  London Waterloo                         6     On time
## 20:57  London Paddington                       14    On time
```
