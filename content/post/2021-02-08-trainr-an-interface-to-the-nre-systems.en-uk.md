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

## Example (Last rendered on 2022-03-27 20:04)

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
## Reading (RDG) Station Board on 2022-03-27 20:04:11
## Time   From                                    Plat  Expected
## 20:56  Great Malvern                           10A   21:00
## 21:05  Ascot                                   5     21:01
## 21:07  Eastleigh                               8     On time
## 21:07  London Paddington                       9B    21:11
## 21:08  Guildford                               15B   On time
## 21:11  Bristol Temple Meads                    10    21:14
## 21:12  London Paddington                       9     21:16
## 21:13  Didcot Parkway                          13    On time
## 21:14  London Paddington                       12    On time
## 21:14  London Paddington                       14    On time
## 21:19  Bedwyn                                  1     On time
## 21:26  London Paddington                       7B    On time
## 21:33  Basingstoke                             2     On time
## 21:35  Ascot                                   6     On time
## 21:39  Manchester Piccadilly                   8     21:45
## 21:41  Guildford                               5     On time
## 21:44  London Paddington                       14    On time
## 21:51  Port Talbot Parkway                     11    22:04
## 21:53  London Paddington                       9     On time
## 21:57  Great Malvern                           10A   On time
## 22:05  Ascot                                   6     On time
## 22:05  Plymouth                                11    22:07
## 22:06  London Paddington                       9B    On time
## 22:09  Weston-super-Mare                       -     Cancelled
## 22:12  London Paddington                       8B    On time
## 22:12  London Paddington                       12    On time
## 22:13  Didcot Parkway                          13    On time
## 22:14  London Paddington                       14    On time
## 22:23  London Paddington                       9     On time
## 22:24  Newbury                                 1     On time
## 22:33  London Paddington                       14    On time
## 22:34  Basingstoke                             2     On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:50  Guildford                               5     On time
## 22:50  Penzance                                11    On time
## 22:54  Great Malvern                           10A   On time
## 23:03  London Paddington                       14    On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:15  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-27 20:04:15
## Time   To                                      Plat  Expected
## 21:01  London Paddington                       10A   On time
## 21:09  Port Talbot Parkway                     9B    21:12
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:13  Guildford                               5     On time
## 21:13  London Paddington                       10    21:17
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    On time
## 21:15  Oxford                                  9     21:17
## 21:25  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        7B    On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:49  Ascot                                   6     On time
## 21:52  Eastleigh                               8     On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:55  Ealing Broadway                         14    On time
## 21:55  London Paddington                       11    22:05
## 21:59  London Paddington                       10A   On time
## 22:09  Port Talbot Parkway                     9B    On time
## 22:10  London Paddington                       -     Cancelled
## 22:12  London Paddington                       11    On time
## 22:13  Didcot Parkway                          12    On time
## 22:13  Worcester Shrub Hill                    8B    On time
## 22:24  Bristol Temple Meads                    9     On time
## 22:25  Ealing Broadway                         14    On time
## 22:44  Newbury                                 2     On time
## 22:53  London Paddington                       11    On time
## 22:54  Ascot                                   6     On time
## 22:54  London Paddington                       10A   On time
## 22:59  Ealing Broadway                         14    On time
## 23:03  Guildford                               5     On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
