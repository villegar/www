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

## Example (Last rendered on 2022-11-19 12:07)

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
## Reading (RDG) Station Board on 2022-11-19 12:07:10
## Time   From                                    Plat  Expected
## 12:03  London Paddington                       14    12:05
## 12:07  Didcot Parkway                          15    On time
## 12:09  London Paddington                       9     On time
## 12:09  Plymouth                                11    12:13
## 12:14  London Waterloo                         6     On time
## 12:17  London Paddington                       9     On time
## 12:27  London Paddington                       7     On time
## 12:33  London Paddington                       14    On time
## 12:33  Redhill                                 5     On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:44  London Waterloo                         6     On time
## 12:50  Swansea                                 11    13:01
## 12:51  Basingstoke                             2     On time
## 12:54  Great Malvern                           10A   On time
## 12:55  London Paddington                       9     On time
## 12:59  Plymouth                                11    On time
## 13:01  Didcot Parkway                          15    On time
## 13:03  London Paddington                       14    On time
## 13:05  Bournemouth                             13B   On time
## 13:09  London Paddington                       8     On time
## 13:14  London Waterloo                         6     On time
## 13:17  London Paddington                       9     On time
## 13:27  London Paddington                       7     On time
## 13:33  London Paddington                       14    On time
## 13:33  Redhill                                 5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    10    On time
## 13:46  London Waterloo                         6     On time
## 13:50  Swansea                                 11    On time
## 13:53  Basingstoke                             2     On time
## 13:54  Great Malvern                           10A   On time
## 13:55  London Paddington                       9     On time
## 14:03  Didcot Parkway                          15    On time
## 14:03  London Paddington                       14    On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-19 12:07:13
## Time   To                                      Plat  Expected
## 12:09  London Waterloo                         6     On time
## 12:11  Swansea                                 9     On time
## 12:12  London Paddington                       11    12:14
## 12:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Hereford                                9     On time
## 12:20  Redhill                                 13A   On time
## 12:24  Ealing Broadway                         14    On time
## 12:30  Plymouth                                7     On time
## 12:38  Basingstoke                             2     On time
## 12:39  London Waterloo                         6     On time
## 12:42  London Paddington                       10    On time
## 12:52  Bournemouth                             7     On time
## 12:52  London Paddington                       11    13:02
## 12:54  Ealing Broadway                         14    On time
## 12:57  Bristol Temple Meads                    9     On time
## 12:57  Didcot Parkway                          15    On time
## 12:57  London Paddington                       10A   On time
## 13:05  London Paddington                       11    On time
## 13:09  London Waterloo                         6     On time
## 13:11  Swansea                                 8     On time
## 13:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 13:19  Worcester Foregate Street               9     On time
## 13:20  Redhill                                 5     On time
## 13:24  Ealing Broadway                         14    On time
## 13:30  Plymouth                                7     On time
## 13:38  Basingstoke                             2     On time
## 13:39  London Waterloo                         6     On time
## 13:42  London Paddington                       10    On time
## 13:52  London Paddington                       11    On time
## 13:54  Ealing Broadway                         14    On time
## 13:55  Didcot Parkway                          15    On time
## 13:56  London Paddington                       10A   On time
## 13:57  Bristol Temple Meads                    9     On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
