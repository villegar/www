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

## Example (Last rendered on 2021-03-14 20:07)

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
## Reading (RDG) Station Board on 2021-03-14 20:07:55
## Time   From                                    Plat  Expected
## 19:58  Hereford                                10A   20:30
## 19:59  London Paddington                       9B    On time
## 20:12  London Paddington                       9B    On time
## 20:13  Didcot Parkway                          15    On time
## 20:14  London Paddington                       15    20:07
## 20:16  Slough                                  12    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   7B    On time
## 20:40  Plymouth                                11    On time
## 20:44  London Paddington                       14    On time
## 20:49  Swansea                                 10    On time
## 20:54  London Paddington                       9     On time
## 20:58  Plymouth                                11    On time
## 20:59  London Paddington                       9     On time
## 20:59  Worcester Foregate Street               10A   On time
## 21:07  Bournemouth                             7B    On time
## 21:07  Gatwick Airport                         5     On time
## 21:11  London Paddington                       9     On time
## 21:12  Taunton                                 10    On time
## 21:13  Didcot Parkway                          13    On time
## 21:14  London Paddington                       14    On time
## 21:16  Slough                                  12    On time
## 21:21  Bedwyn                                  1     On time
## 21:26  London Paddington                       7     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Redhill                                 15    On time
## 21:44  London Paddington                       14    On time
## 21:48  Swansea                                 10    On time
## 21:54  London Paddington                       9     On time
## 21:59  Hereford                                10A   On time
## 20:15  Virginia Water                          BUS   On time
## 20:25  Virginia Water                          BUS   On time
## 20:45  Virginia Water                          BUS   On time
## 20:55  Virginia Water                          BUS   On time
## 21:15  Virginia Water                          BUS   On time
## 21:25  Virginia Water                          BUS   On time
## 21:45  Virginia Water                          BUS   On time
## 21:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-14 20:07:58
## Time   To                                      Plat  Expected
## 20:06  Ealing Broadway                         14    On time
## 20:07  London Paddington                       10A   20:31
## 20:09  Swansea                                 9B    On time
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Great Malvern                           9B    On time
## 20:15  Manchester Piccadilly                   13B   On time
## 20:15  Slough                                  15    On time
## 20:25  Didcot Parkway                          12    On time
## 20:27  Plymouth                                7     On time
## 20:36  Ealing Broadway                         15    On time
## 20:38  Basingstoke                             2     On time
## 20:42  Newbury                                 1     On time
## 20:45  London Paddington                       11    On time
## 20:50  London Paddington                       10    On time
## 20:52  Bournemouth                             7B    On time
## 20:55  Weston-super-Mare                       9     On time
## 21:05  London Paddington                       11    On time
## 21:06  Ealing Broadway                         14    On time
## 21:07  London Paddington                       10A   On time
## 21:09  Swansea                                 9     On time
## 21:12  Birmingham New Street                   7B    On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Worcester Shrub Hill                    9     On time
## 21:15  Slough                                  13    On time
## 21:17  Didcot Parkway                          12    On time
## 21:20  London Paddington                       10    On time
## 21:27  Exeter St Davids                        7     On time
## 21:36  Ealing Broadway                         14    On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:50  London Paddington                       10    On time
## 21:52  Southampton Central                     7B    On time
## 21:55  Bristol Temple Meads                    9     On time
## 22:05  London Paddington                       10A   On time
## 22:06  Ealing Broadway                         14    On time
## 20:06  Virginia Water                          BUS   On time
## 20:26  Virginia Water                          BUS   On time
## 20:36  Virginia Water                          BUS   On time
## 20:56  Virginia Water                          BUS   On time
## 21:06  Virginia Water                          BUS   On time
## 21:26  Virginia Water                          BUS   On time
## 21:36  Virginia Water                          BUS   On time
## 21:56  Virginia Water                          BUS   On time
## 22:06  Virginia Water                          BUS   On time
```
