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

## Example (Last rendered on 2023-02-19 20:03)

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
## Reading (RDG) Station Board on 2023-02-19 20:03:33
## Time   From                                    Plat  Expected
## 19:39  Manchester Piccadilly                   7     19:45
## 19:47  Salisbury                               1     Delayed
## 19:56  Hereford                                -     Cancelled
## 20:02  Virginia Water                          4     On time
## 20:07  London Paddington                       8     On time
## 20:08  Guildford                               15    On time
## 20:11  Bristol Temple Meads                    10    20:14
## 20:12  London Paddington                       -     Cancelled
## 20:13  Didcot Parkway                          13    On time
## 20:14  Penzance                                11    20:16
## 20:19  London Paddington                       12    On time
## 20:26  London Paddington                       9     On time
## 20:28  Abbey Wood                              14    On time
## 20:32  Basingstoke                             2     On time
## 20:32  Virginia Water                          4     On time
## 20:38  Guildford                               5     On time
## 20:39  Manchester Piccadilly                   8     20:42
## 20:47  London Paddington                       9     On time
## 20:49  Swansea                                 11    On time
## 20:54  London Paddington                       9     On time
## 20:58  Abbey Wood                              14    On time
## 20:58  Great Malvern                           -     Cancelled
## 21:02  Virginia Water                          4     On time
## 21:06  Eastleigh                               8     On time
## 21:07  London Paddington                       9     On time
## 21:08  Guildford                               15B   On time
## 21:11  Taunton                                 10    On time
## 21:12  London Paddington                       12    On time
## 21:12  London Paddington                       -     Cancelled
## 21:13  Didcot Parkway                          13    On time
## 21:27  London Paddington                       7     On time
## 21:27  Penzance                                11    On time
## 21:28  Abbey Wood                              14    On time
## 21:32  Basingstoke                             2     On time
## 21:32  Virginia Water                          4     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:40  Guildford                               5     On time
## 21:49  Swansea                                 10    On time
## 21:53  Great Malvern                           -     Cancelled
## 21:54  London Paddington                       9     On time
## 21:58  Abbey Wood                              14    On time
## 22:02  Virginia Water                          4     On time
## 20:07  Bedwyn                                  BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 20:56  Newbury                                 BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-19 20:03:38
## Time   To                                      Plat  Expected
## 19:52  Eastleigh                               7     Delayed
## 20:02  London Paddington                       -     Cancelled
## 20:09  Swansea                                 8     On time
## 20:12  Salisbury                               1     On time
## 20:13  Guildford                               5     On time
## 20:14  Ealing Broadway                         13    On time
## 20:14  Great Malvern                           -     Cancelled
## 20:14  London Paddington                       10    20:15
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:17  London Paddington                       11    On time
## 20:24  Abbey Wood                              14    On time
## 20:24  Virginia Water                          4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:28  Plymouth                                9     On time
## 20:37  Basingstoke                             2     On time
## 20:49  Oxford                                  9     On time
## 20:52  Eastleigh                               8     On time
## 20:54  Abbey Wood                              14    On time
## 20:54  Virginia Water                          4     On time
## 20:55  Weston-super-Mare                       9     On time
## 20:56  London Paddington                       11    On time
## 21:02  London Paddington                       -     Cancelled
## 21:09  Swansea                                 9     On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:12  Salisbury                               -     Cancelled
## 21:13  Guildford                               5     On time
## 21:14  Ealing Broadway                         13    On time
## 21:14  London Paddington                       10    On time
## 21:15  Didcot Parkway                          12    On time
## 21:15  Worcester Shrub Hill                    -     Cancelled
## 21:24  Ealing Broadway                         14    On time
## 21:24  Virginia Water                          4     On time
## 21:30  Exeter St Davids                        7     On time
## 21:33  London Paddington                       11    On time
## 21:37  Basingstoke                             2     On time
## 21:52  Eastleigh                               8     On time
## 21:53  Ealing Broadway                         14    On time
## 21:54  Virginia Water                          4     On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:56  London Paddington                       10    On time
## 21:59  London Paddington                       -     Cancelled
## 20:43  Newbury                                 BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:43  Bedwyn                                  BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
