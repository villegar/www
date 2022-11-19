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

## Example (Last rendered on 2022-11-19 10:04)

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
## Reading (RDG) Station Board on 2022-11-19 10:04:20
## Time   From                                    Plat  Expected
## 10:01  Didcot Parkway                          15    10:03
## 10:03  London Paddington                       14    On time
## 10:09  London Paddington                       9     On time
## 10:17  London Paddington                       9     On time
## 10:18  London Waterloo                         6     On time
## 10:21  London Paddington                       7     On time
## 10:33  London Paddington                       14    On time
## 10:33  Redhill                                 5     On time
## 10:40  Bristol Temple Meads                    10    On time
## 10:41  Manchester Piccadilly                   7B    On time
## 10:44  London Waterloo                         6     On time
## 10:50  Basingstoke                             2     On time
## 10:50  Carmarthen                              11    On time
## 10:54  Great Malvern                           10A   On time
## 10:55  London Paddington                       9     On time
## 11:03  London Paddington                       14    On time
## 11:05  Bournemouth                             13B   On time
## 11:06  Didcot Parkway                          12    On time
## 11:09  London Paddington                       8     On time
## 11:09  Plymouth                                11    On time
## 11:14  London Waterloo                         4     On time
## 11:17  London Paddington                       9     On time
## 11:21  London Paddington                       7     On time
## 11:33  London Paddington                       14    On time
## 11:33  Redhill                                 5     On time
## 11:39  Manchester Piccadilly                   13    On time
## 11:40  Bristol Temple Meads                    10    On time
## 11:44  London Waterloo                         6     On time
## 11:50  Swansea                                 11    On time
## 11:54  Great Malvern                           10    On time
## 11:55  London Paddington                       9     On time
## 11:56  Basingstoke                             2     On time
## 12:03  London Paddington                       14    On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-19 10:04:25
## Time   To                                      Plat  Expected
## 10:09  London Waterloo                         6     On time
## 10:11  Swansea                                 9     On time
## 10:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9     On time
## 10:20  Redhill                                 5     On time
## 10:23  Plymouth                                7     On time
## 10:24  Ealing Broadway                         14    On time
## 10:38  Basingstoke                             2     On time
## 10:39  London Waterloo                         6     On time
## 10:42  London Paddington                       10    On time
## 10:51  Bournemouth                             7B    On time
## 10:52  Didcot Parkway                          15    On time
## 10:52  London Paddington                       11    On time
## 10:54  Ealing Broadway                         14    On time
## 10:56  London Paddington                       10A   On time
## 10:57  Bristol Temple Meads                    9     On time
## 11:09  London Waterloo                         6     On time
## 11:11  Swansea                                 8     On time
## 11:12  London Paddington                       11    On time
## 11:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Great Malvern                           9     On time
## 11:20  Redhill                                 5     On time
## 11:24  Ealing Broadway                         14    On time
## 11:24  Plymouth                                7     On time
## 11:38  Basingstoke                             2     On time
## 11:39  London Waterloo                         4     On time
## 11:42  London Paddington                       10    On time
## 11:52  London Paddington                       11    On time
## 11:53  Didcot Parkway                          12    On time
## 11:54  Ealing Broadway                         14    On time
## 11:57  Bristol Temple Meads                    9     On time
## 11:57  London Paddington                       10    On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
