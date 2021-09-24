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

## Example (Last rendered on 2021-09-24 22:05)

Load `trainR` to your working environment:

```r
library(trainR)
```

### Arrivals board at Reading Station (RDG)


```r
rdg_arr <- trainR::GetArrBoardRequest("RDG")
```

```
## Error: [soap:Receiver] Unexpected server error
```

```r
print(rdg_arr)
```

```
## Error in print(rdg_arr): object 'rdg_arr' not found
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-09-24 22:05:13
## Time   To                                      Plat  Expected
## 22:49  Southampton Central                     7     23:06
## 23:01  London Paddington                       15    23:05
## 23:08  Bedwyn                                  3     On time
## 23:15  London Waterloo                         6     On time
## 23:18  Swansea                                 8     On time
## 23:19  London Paddington                       7     23:34
## 23:22  Ealing Broadway                         15    On time
## 23:28  Worcestershire Parkway                  12    On time
## 23:32  Didcot Parkway                          13    23:37
## 23:34  Basingstoke                             2     On time
## 23:34  Gatwick Airport                         4     On time
##        via Guildford                           
## 23:38  London Paddington                       15A   On time
## 23:52  Staines                                 5     On time
## 00:05  Bristol Temple Meads                    13    On time
## 00:08  Oxford                                  12    On time
## 00:17  Newbury                                 2     On time
## 00:18  London Paddington                       14    On time
## 00:29  Didcot Parkway                          13    On time
## 00:43  London Paddington                       15    On time
## 00:49  Penzance                                12    On time
```
