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

## Example (Last rendered on 2021-06-06 20:24)

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
## Reading (RDG) Station Board on 2021-06-06 20:24:37
## Time   From                                    Plat  Expected
## 21:19  Bedwyn                                  1     21:26
## 21:26  London Paddington                       7B    On time
## 21:31  London Paddington                       9     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Guildford                               15    On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:46  London Paddington                       14    On time
## 21:47  Swansea                                 10    21:50
## 21:52  London Paddington                       9     On time
## 21:59  Worcestershire Parkway                  10A   On time
## 22:00  London Paddington                       9     On time
## 22:05  Plymouth                                11A   22:18
## 22:12  Weston-super-Mare                       10A   On time
## 22:13  Didcot Parkway                          13    On time
## 22:16  London Paddington                       14    On time
## 22:17  London Paddington                       12    On time
## 22:24  Newbury                                 1     On time
## 22:26  London Paddington                       8B    On time
## 22:33  Basingstoke                             13    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:45  Guildford                               5     On time
## 22:45  London Paddington                       14    On time
## 22:47  Carmarthen                              10A   On time
## 22:50  Penzance                                11    On time
## 22:53  Worcestershire Parkway                  10    On time
## 23:10  Didcot Parkway                          15B   On time
## 23:10  London Paddington                       13    On time
## 23:11  London Paddington                       8     On time
## 23:13  London Paddington                       12    On time
## 23:17  Bedwyn                                  14    On time
## 21:27  Virginia Water                          BUS   On time
## 21:46  Virginia Water                          BUS   On time
## 21:57  Virginia Water                          BUS   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 22:16  Virginia Water                          BUS   On time
## 22:46  Virginia Water                          BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 23:16  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-06-06 20:24:39
## Time   To                                      Plat  Expected
## 21:27  Exeter St Davids                        7B    On time
## 21:30  Ealing Broadway                         14    On time
## 21:38  Basingstoke                             2     On time
## 21:39  Oxford                                  9     On time
## 21:44  Bedwyn                                  1     On time
## 21:49  London Paddington                       10    21:51
## 21:52  Southampton Central                     8     On time
## 21:54  Bristol Temple Meads                    9     On time
## 22:00  Ealing Broadway                         14    On time
## 22:00  London Paddington                       10A   On time
## 22:09  Swansea                                 9     On time
## 22:12  London Paddington                       10A   On time
## 22:14  Ealing Broadway                         13    On time
## 22:15  London Paddington                       11A   22:19
## 22:17  Didcot Parkway                          12    On time
## 22:27  Oxford                                  8B    On time
## 22:30  Ealing Broadway                         14    On time
## 22:44  Newbury                                 1     On time
## 22:48  London Paddington                       10A   On time
## 22:55  London Paddington                       11    On time
## 22:59  Ealing Broadway                         14    On time
## 23:01  London Paddington                       10    On time
## 23:03  Guildford                               5     On time
## 23:12  Ealing Broadway                         15B   On time
## 23:15  Bristol Parkway                         8     On time
## 23:20  Didcot Parkway                          12    On time
## 21:34  Virginia Water                          BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 22:04  Virginia Water                          BUS   On time
## 22:34  Virginia Water                          BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
## 23:04  Virginia Water                          BUS   On time
```
