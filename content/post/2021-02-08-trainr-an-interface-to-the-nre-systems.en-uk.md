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

## Example (Last rendered on 2023-02-12 20:03)

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
## Reading (RDG) Station Board on 2023-02-12 20:03:35
## Time   From                                    Plat  Expected
## 19:54  London Paddington                       9     20:05
## 19:56  Hereford                                -     Cancelled
## 20:06  London Waterloo                         4     20:03
## 20:08  Redhill                                 15    On time
## 20:09  London Paddington                       9     20:11
## 20:10  Exeter St Davids                        10    20:13
## 20:12  London Paddington                       8B    20:15
## 20:13  Didcot Parkway                          13    On time
## 20:18  London Paddington                       12    On time
## 20:20  Newbury                                 1     On time
## 20:21  London Waterloo                         6     On time
## 20:26  Abbey Wood                              14    On time
## 20:27  London Paddington                       7     On time
## 20:32  Basingstoke                             2     On time
## 20:37  London Waterloo                         4     On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   8B    On time
## 20:41  Plymouth                                10    On time
## 20:47  London Paddington                       9     On time
## 20:49  Swansea                                 11    On time
## 20:54  London Paddington                       9     On time
## 20:56  Abbey Wood                              14    On time
## 20:57  Worcester Shrub Hill                    10    On time
## 20:58  Penzance                                11    On time
## 21:06  Bournemouth                             8B    On time
## 21:06  London Waterloo                         4     On time
## 21:08  Redhill                                 15B   On time
## 21:09  London Paddington                       9     On time
## 21:11  Taunton                                 11    On time
## 21:12  London Paddington                       12    On time
## 21:13  Didcot Parkway                          13    On time
## 21:15  London Paddington                       7     On time
## 21:19  Bedwyn                                  1     On time
## 21:26  Abbey Wood                              14    On time
## 21:27  London Paddington                       7     On time
## 21:32  Basingstoke                             2     On time
## 21:36  London Waterloo                         4     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:40  Gatwick Airport                         15    On time
## 21:47  Swansea                                 9     On time
## 21:53  Great Malvern                           11    On time
## 21:54  London Paddington                       9     On time
## 21:56  Abbey Wood                              14    On time
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
## Reading (RDG) Station Board on 2023-02-12 20:03:41
## Time   To                                      Plat  Expected
## 19:56  Bristol Temple Meads                    9     20:06
## 20:02  London Paddington                       -     Cancelled
## 20:10  Swansea                                 9     20:12
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:13  London Paddington                       10    20:14
## 20:14  Ealing Broadway                         13    On time
## 20:14  Great Malvern                           8B    20:16
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:21  Abbey Wood                              14    On time
## 20:24  London Waterloo                         4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:28  Plymouth                                7     On time
## 20:37  Basingstoke                             2     On time
## 20:43  London Paddington                       10    On time
## 20:43  Newbury                                 1     On time
## 20:50  Oxford                                  9     On time
## 20:52  Abbey Wood                              14    On time
## 20:52  Bournemouth                             8B    On time
## 20:52  London Paddington                       11    On time
## 20:54  London Waterloo                         4     On time
## 20:56  Weston-super-Mare                       9     On time
## 21:00  London Paddington                       11    On time
## 21:02  London Paddington                       10    On time
## 21:12  Birmingham New Street                   8B    On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:13  London Paddington                       11    On time
## 21:14  Ealing Broadway                         13    On time
## 21:14  Swansea                                 9     On time
## 21:15  Didcot Parkway                          12    On time
## 21:17  Worcester Shrub Hill                    7     On time
## 21:22  Ealing Broadway                         14    On time
## 21:24  London Waterloo                         4     On time
## 21:28  Exeter St Davids                        7     On time
## 21:37  Basingstoke                             2     On time
## 21:43  Bedwyn                                  1     On time
## 21:50  London Paddington                       9     On time
## 21:52  Ealing Broadway                         14    On time
## 21:52  Southampton Central                     8     On time
## 21:54  London Waterloo                         4     On time
## 21:55  London Paddington                       11    On time
## 21:56  Bristol Temple Meads                    9     On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
