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

## Example (Last rendered on 2023-01-01 20:04)

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
## Reading (RDG) Station Board on 2023-01-01 20:04:18
## Time   From                                    Plat  Expected
## 20:04  Abbey Wood                              14    On time
## 20:07  London Paddington                       8     20:13
## 20:08  Redhill                                 15    On time
## 20:10  Exeter St Davids                        10    20:22
## 20:12  London Paddington                       9B    On time
## 20:13  Didcot Parkway                          13A   On time
## 20:14  Penzance                                11    20:20
## 20:19  London Paddington                       12B   On time
## 20:19  London Waterloo                         -     Cancelled
## 20:27  Didcot Parkway                          10A   On time
## 20:27  London Paddington                       7     20:35
## 20:32  Basingstoke                             2     On time
## 20:33  Abbey Wood                              14    20:36
## 20:34  Newbury                                 1     On time
## 20:38  Gatwick Airport                         13    20:40
## 20:39  Manchester Piccadilly                   8     On time
## 20:49  London Paddington                       9B    On time
## 20:49  London Waterloo                         -     On time
## 20:49  Swansea                                 10    On time
## 20:53  London Paddington                       -     Cancelled
## 21:00  Great Malvern                           -     Cancelled
## 21:03  Abbey Wood                              14    On time
## 21:06  Bournemouth                             8     On time
## 21:07  London Paddington                       -     Cancelled
## 21:10  Redhill                                 15B   On time
## 21:11  Bristol Temple Meads                    10    On time
## 21:12  London Paddington                       12B   On time
## 21:12  London Paddington                       9B    On time
## 21:13  Didcot Parkway                          13A   On time
## 21:15  Penzance                                -     Cancelled
## 21:19  London Waterloo                         -     21:23
## 21:26  London Paddington                       7B    On time
## 21:28  Bedwyn                                  1     On time
## 21:33  Abbey Wood                              14    On time
## 21:33  Basingstoke                             -     Cancelled
## 21:39  Manchester Piccadilly                   8     On time
## 21:40  Gatwick Airport                         15    On time
## 21:46  London Paddington                       10A   On time
## 21:48  Swansea                                 -     Cancelled
## 21:49  London Waterloo                         -     On time
## 21:53  Great Malvern                           -     Cancelled
## 21:53  London Paddington                       -     Cancelled
## 22:03  Abbey Wood                              14    On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-01 20:04:22
## Time   To                                      Plat  Expected
## 20:09  Swansea                                 8     20:14
## 20:11  London Paddington                       10    20:23
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         13A   On time
## 20:14  Great Malvern                           9B    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:18  London Paddington                       11    20:21
## 20:24  Abbey Wood                              14    On time
## 20:26  London Waterloo                         6     On time
## 20:27  London Paddington                       10A   On time
## 20:28  Didcot Parkway                          12B   On time
## 20:28  Plymouth                                7     20:36
## 20:37  Basingstoke                             -     Cancelled
## 20:43  Newbury                                 1     On time
## 20:49  Didcot Parkway                          9B    On time
## 20:50  London Paddington                       10    On time
## 20:52  Bournemouth                             8     On time
## 20:54  Abbey Wood                              14    On time
## 20:55  Weston-super-Mare                       -     Cancelled
## 20:58  Clapham Junction                        -     Cancelled
## 21:02  London Paddington                       -     Cancelled
## 21:09  Swansea                                 -     Cancelled
## 21:11  London Paddington                       10    On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Didcot Parkway                          12B   On time
## 21:14  Ealing Broadway                         13A   On time
## 21:17  London Paddington                       -     Cancelled
## 21:17  Worcester Shrub Hill                    9B    On time
## 21:24  Ealing Broadway                         14    On time
## 21:26  Feltham                                 -     On time
## 21:28  Exeter St Davids                        7B    On time
## 21:37  Basingstoke                             -     Cancelled
## 21:43  Bedwyn                                  1     On time
## 21:46  Didcot Parkway                          10A   On time
## 21:50  London Paddington                       -     Cancelled
## 21:52  Southampton Central                     8     On time
## 21:54  Ealing Broadway                         14    On time
## 21:55  Bristol Temple Meads                    -     Cancelled
## 21:55  London Paddington                       -     Cancelled
## 22:00  Staines                                 -     On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
