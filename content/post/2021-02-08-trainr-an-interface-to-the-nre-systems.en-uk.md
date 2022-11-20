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

## Example (Last rendered on 2022-11-20 22:09)

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
## Reading (RDG) Station Board on 2022-11-20 22:09:29
## Time   From                                    Plat  Expected
## 22:05  Plymouth                                11    On time
## 22:06  London Paddington                       9     22:09
## 22:07  London Paddington                       14    22:09
## 22:09  Weston-super-Mare                       10    On time
## 22:12  London Paddington                       9B    22:15
## 22:13  Didcot Parkway                          13    22:15
## 22:16  London Paddington                       12    On time
## 22:23  London Paddington                       9     On time
## 22:24  Newbury                                 1     On time
## 22:35  Clapham Junction                        6     On time
## 22:39  Manchester Piccadilly                   8     22:46
## 22:42  London Paddington                       9     On time
## 22:45  Gatwick Airport                         15B   On time
## 22:49  Carmarthen                              10A   On time
## 22:52  Plymouth                                8     On time
## 22:54  Great Malvern                           15    On time
## 23:05  Clapham Junction                        6     On time
## 23:08  Didcot Parkway                          8     On time
## 23:12  London Paddington                       9     On time
## 23:14  Bedwyn                                  8     On time
## 23:18  London Paddington                       9     On time
## 23:31  London Paddington                       7     On time
## 23:35  Clapham Junction                        6     On time
## 23:35  Plymouth                                11A   On time
## 23:41  London Paddington                       7     On time
## 23:45  Gatwick Airport                         8     On time
## 23:46  Newbury                                 1     On time
## 00:05  Clapham Junction                        5     On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:20  Basingstoke                             BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:20  Basingstoke                             BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-20 22:09:33
## Time   To                                      Plat  Expected
## 22:09  Swansea                                 9     22:10
## 22:12  London Paddington                       11    On time
## 22:14  Worcester Shrub Hill                    9B    22:16
## 22:15  London Paddington                       10    On time
## 22:16  Didcot Parkway                          12    On time
## 22:21  Clapham Junction                        6     On time
## 22:24  Bristol Temple Meads                    9     On time
## 22:30  Ealing Broadway                         14    On time
## 22:43  Newbury                                 1     On time
## 22:54  Clapham Junction                        6     On time
## 22:54  London Paddington                       15    On time
## 23:00  London Paddington                       10A   On time
## 23:02  London Paddington                       8     On time
## 23:03  Redhill                                 5     On time
## 23:04  Ealing Broadway                         9     On time
## 23:10  Ealing Broadway                         8     On time
## 23:15  Bristol Parkway                         9     On time
## 23:20  Didcot Parkway                          7     On time
## 23:37  Bristol Temple Meads                    7     On time
## 23:38  London Paddington                       11A   On time
## 23:40  Ealing Broadway                         9     On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:48  Chippenham                              BUS   On time
```
