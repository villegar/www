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

## Example (Last rendered on 2021-08-22 20:04)

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
## Reading (RDG) Station Board on 2021-08-22 20:04:55
## Time   From                                    Plat  Expected
## 20:58  Penzance                                11    21:04
## 21:07  Bournemouth                             8     On time
## 21:07  London Paddington                       9     On time
## 21:07  Redhill                                 15B   On time
## 21:10  London Paddington                       9     On time
## 21:12  Bath Spa                                10    On time
## 21:13  Didcot Parkway                          13    On time
## 21:13  London Paddington                       14    On time
## 21:14  London Paddington                       12    On time
## 21:19  Bedwyn                                  1     21:24
## 21:26  London Paddington                       7B    On time
## 21:32  London Waterloo                         6     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Gatwick Airport                         15    On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:42  London Paddington                       9B    On time
## 21:43  London Paddington                       14    On time
## 21:48  Swansea                                 10    On time
## 21:53  London Paddington                       -     Cancelled
## 21:59  Great Malvern                           10A   On time
## 22:02  London Waterloo                         6     On time
## 22:05  Plymouth                                11    On time
## 22:06  London Paddington                       9     On time
## 22:09  Bath Spa                                -     Cancelled
## 22:13  Didcot Parkway                          13    On time
## 22:13  London Paddington                       14    On time
## 22:13  London Paddington                       9     On time
## 22:14  London Paddington                       12    On time
## 22:24  Newbury                                 1     On time
## 22:32  London Waterloo                         6     On time
## 22:33  Basingstoke                             12    On time
## 22:34  London Paddington                       14    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:45  Gatwick Airport                         15B   On time
## 22:49  Carmarthen                              10A   On time
## 22:49  Penzance                                13    On time
## 22:52  Great Malvern                           15A   On time
## 23:02  London Waterloo                         6     On time
## 23:03  London Paddington                       14    On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-22 20:04:58
## Time   To                                      Plat  Expected
## 20:58  London Paddington                       11    21:05
## 21:09  Swansea                                 9     On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:13  London Paddington                       10    On time
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    On time
## 21:14  Worcester Shrub Hill                    9     On time
## 21:24  London Waterloo                         4     On time
## 21:25  Ealing Broadway                         14    On time
## 21:27  Exeter St Davids                        7B    On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:44  Oxford                                  9B    On time
## 21:50  London Paddington                       10    On time
## 21:52  Southampton Central                     8     On time
## 21:54  Bath Spa                                -     Cancelled
## 21:54  London Waterloo                         6     On time
## 21:55  Ealing Broadway                         14    On time
## 22:00  London Paddington                       10A   On time
## 22:09  Swansea                                 9     On time
## 22:10  London Paddington                       -     Cancelled
## 22:12  London Paddington                       11    On time
## 22:13  Worcester Shrub Hill                    9     On time
## 22:14  Didcot Parkway                          12    On time
## 22:14  Ealing Broadway                         13    On time
## 22:24  London Waterloo                         6     On time
## 22:25  Ealing Broadway                         14    On time
## 22:44  Newbury                                 1     On time
## 22:50  London Paddington                       10A   On time
## 22:51  London Paddington                       13    On time
## 22:54  London Paddington                       15A   On time
## 22:54  London Waterloo                         6     On time
## 22:59  Ealing Broadway                         14    On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
