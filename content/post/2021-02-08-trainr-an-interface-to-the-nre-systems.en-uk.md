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

## Example (Last rendered on 2021-02-19 22:07)

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
## Reading (RDG) Station Board on 2021-02-19 22:07:49
## Time   From                                    Plat  Expected
## 21:56  Basingstoke                             12B   On time
## 22:07  Didcot Parkway                          15    22:00
## 22:08  Bristol Temple Meads                    10A   On time
## 22:10  London Waterloo                         4     On time
## 22:11  London Paddington                       9     On time
## 22:13  London Paddington                       14    On time
## 22:13  Newbury                                 1     On time
## 22:14  London Paddington                       13    On time
## 22:16  London Paddington                       9B    On time
## 22:20  Bedwyn                                  11A   On time
## 22:24  London Paddington                       9     On time
## 22:30  Cheltenham Spa                          10    On time
## 22:40  London Waterloo                         6     On time
## 22:41  Manchester Piccadilly                   7B    On time
## 22:43  London Paddington                       14    On time
## 22:44  London Paddington                       12    On time
## 22:48  Oxford                                  15    On time
## 22:50  Salisbury                               11    On time
## 22:57  Worcester Foregate Street               15    On time
## 23:05  Basingstoke                             15    On time
## 23:10  Penzance                                10    On time
## 23:13  London Paddington                       13    On time
## 23:15  Gatwick Airport                         15    On time
## 23:15  London Paddington                       14    On time
## 23:15  London Waterloo                         6     On time
## 23:20  Newbury                                 15A   On time
## 23:31  London Paddington                       13    On time
## 23:33  Oxford                                  15    On time
## 23:43  London Paddington                       10    On time
## 23:46  Didcot Parkway                          15    On time
## 23:50  Manchester Piccadilly                   7     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-19 22:07:51
## Time   To                                      Plat  Expected
## 22:05  Basingstoke                             1     On time
## 22:09  Oxford                                  12B   On time
## 22:10  London Paddington                       10A   On time
## 22:10  Newbury                                 2     On time
## 22:12  London Waterloo                         6     On time
## 22:13  Swansea                                 9     On time
## 22:15  Ealing Broadway                         15    On time
## 22:18  Worcester Shrub Hill                    9B    On time
## 22:21  London Paddington                       11A   On time
## 22:22  Ealing Broadway                         14    On time
## 22:25  Exeter St Davids                        9     On time
##        via Bristol                             
## 22:35  London Paddington                       10    On time
## 22:46  Didcot Parkway                          12    On time
## 22:48  Ealing Broadway                         13    On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Ealing Broadway                         14    On time
## 22:59  London Paddington                       15    On time
## 23:12  Ascot                                   6     On time
## 23:19  London Paddington                       10    On time
## 23:22  Ealing Broadway                         15A   On time
## 23:32  Didcot Parkway                          13    On time
## 23:34  Redhill                                 14A   On time
```
