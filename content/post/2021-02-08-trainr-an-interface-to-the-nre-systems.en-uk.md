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

## Example (Last rendered on 2021-12-18 22:03)

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
## Reading (RDG) Station Board on 2021-12-18 22:03:22
## Time   From                                    Plat  Expected
## 22:09  Bristol Temple Meads                    10    22:13
## 22:11  London Waterloo                         4     On time
## 22:13  London Paddington                       14    On time
## 22:14  London Paddington                       12B   On time
## 22:17  London Paddington                       8B    22:40
## 22:19  Basingstoke                             2     On time
## 22:22  Newbury                                 1     On time
## 22:25  Gatwick Airport                         15B   On time
## 22:25  London Paddington                       9     On time
## 22:27  Didcot Parkway                          13    On time
## 22:32  Oxford                                  14A   On time
## 22:36  Cheltenham Spa                          10    On time
## 22:41  London Waterloo                         5     On time
## 22:41  Manchester Piccadilly                   8B    22:50
## 22:43  London Paddington                       14    On time
## 22:44  London Paddington                       12    On time
## 22:50  Basingstoke                             2     On time
## 22:51  London Paddington                       10    On time
## 22:53  London Paddington                       9     On time
## 23:04  Hereford                                8A    On time
## 23:04  Redhill                                 14B   On time
## 23:10  Newbury                                 3     On time
## 23:11  London Waterloo                         4     On time
## 23:11  Penzance                                11    On time
## 23:15  London Paddington                       10    On time
## 23:17  London Paddington                       7A    On time
## 23:25  Basingstoke                             3     On time
## 23:28  Didcot Parkway                          7     On time
## 23:29  London Paddington                       8     On time
## 23:41  London Waterloo                         6     On time
## 23:43  London Paddington                       9     On time
## 23:46  London Paddington                       8     On time
## 23:52  Basingstoke                             8     On time
## 23:52  Taunton                                 10    On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-18 22:03:26
## Time   To                                      Plat  Expected
## 22:05  Basingstoke                             2     On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         5     On time
## 22:15  Ealing Broadway                         15    On time
## 22:15  London Paddington                       10    On time
## 22:19  Worcester Shrub Hill                    8B    22:41
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          12B   On time
## 22:34  London Paddington                       14A   On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10    On time
## 22:42  London Waterloo                         4     On time
## 22:52  Ealing Broadway                         14    On time
## 22:52  Southampton Central                     8B    On time
## 22:55  Bristol Temple Meads                    9     On time
## 23:05  Basingstoke                             2     On time
## 23:05  Didcot Parkway                          12    On time
## 23:06  London Paddington                       8A    On time
## 23:12  Newbury                                 1     On time
## 23:13  London Paddington                       11    On time
## 23:15  London Waterloo                         5     On time
## 23:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:48  Didcot Parkway                          8     On time
## 23:52  Staines                                 6     On time
## 23:54  London Paddington                       10    On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
