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

## Example (Last rendered on 2021-12-20 22:03)

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
## Reading (RDG) Station Board on 2021-12-20 22:03:09
## Time   From                                    Plat  Expected
## 21:56  Great Malvern                           10A   21:52
## 22:00  Paignton                                11    21:56
## 22:05  Didcot Parkway                          15    22:02
## 22:08  Exeter St Davids                        10A   On time
## 22:10  London Paddington                       13    On time
## 22:14  London Paddington                       7     On time
## 22:14  Newbury                                 1     On time
## 22:15  London Paddington                       14    On time
## 22:17  London Paddington                       9     On time
## 22:20  London Paddington                       8B    On time
## 22:20  Newbury                                 11    On time
## 22:25  Oxford                                  13A   On time
## 22:26  London Paddington                       9B    On time
## 22:32  Cheltenham Spa                          11    22:36
## 22:34  Shalford                                14A   On time
## 22:40  Basingstoke                             2     On time
## 22:41  Birmingham New Street                   7B    On time
## 22:41  London Waterloo                         6     On time
## 22:45  Didcot Parkway                          15    On time
## 22:45  London Paddington                       14    On time
## 22:45  Swansea                                 10    22:47
## 22:47  London Paddington                       12    On time
## 22:49  London Paddington                       9     On time
## 22:50  Salisbury                               11    On time
## 22:54  London Paddington                       8     On time
## 22:59  Worcester Foregate Street               15    On time
## 23:02  London Paddington                       9     On time
## 23:03  Basingstoke                             2     On time
## 23:10  Penzance                                15    On time
## 23:12  London Waterloo                         5     On time
## 23:14  Newbury                                 3     On time
## 23:15  Gatwick Airport                         8     On time
## 23:16  London Paddington                       7     On time
## 23:18  London Paddington                       9     On time
## 23:21  Didcot Parkway                          14    On time
## 23:23  London Paddington                       9     On time
## 23:26  Basingstoke                             8     On time
## 23:35  Oxford                                  15A   On time
## 23:41  London Waterloo                         5     On time
## 23:42  London Paddington                       14    On time
## 23:44  Didcot Parkway                          15    On time
## 23:49  Basingstoke                             7     On time
## 23:50  Birmingham New Street                   3     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-20 22:03:13
## Time   To                                      Plat  Expected
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       10A   On time
## 22:10  London Paddington                       11    On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         4     On time
## 22:15  London Paddington                       10A   On time
## 22:16  Ealing Broadway                         15    On time
## 22:18  Didcot Parkway                          7     On time
## 22:19  Swansea                                 9     On time
## 22:22  Ealing Broadway                         14    On time
## 22:22  Worcester Shrub Hill                    8B    On time
## 22:25  London Paddington                       11    On time
## 22:27  Plymouth                                9B    On time
##        via Bristol                             
## 22:29  Basingstoke                             2     On time
## 22:35  London Paddington                       13A   On time
## 22:43  London Paddington                       11    On time
## 22:48  Didcot Parkway                          12    On time
## 22:48  London Paddington                       10    On time
## 22:49  Southampton Central                     7B    On time
## 22:50  Ealing Broadway                         14    On time
## 22:52  Basingstoke                             2     On time
## 22:55  Oxford                                  9     On time
## 23:01  London Paddington                       15    On time
## 23:02  Bedwyn                                  8     On time
## 23:02  London Waterloo                         6     On time
## 23:04  Bristol Temple Meads                    9     On time
## 23:19  London Paddington                       15    On time
## 23:20  Swansea                                 9     On time
## 23:22  Ealing Broadway                         14    On time
## 23:28  Worcestershire Parkway                  9     On time
## 23:32  Didcot Parkway                          7     On time
## 23:33  Gatwick Airport                         13A   On time
##        via Guildford                           
## 23:34  Basingstoke                             2     On time
## 23:38  London Paddington                       15A   On time
## 23:52  Ascot                                   5     On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
