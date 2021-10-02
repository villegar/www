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

## Example (Last rendered on 2021-10-02 20:03)

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
## Reading (RDG) Station Board on 2021-10-02 20:03:54
## Time   From                                    Plat  Expected
## 20:54  Great Malvern                           10A   21:03
## 21:01  Didcot Parkway                          15A   On time
## 21:05  Bournemouth                             13    On time
## 21:11  London Paddington                       9     On time
## 21:13  London Paddington                       14    On time
## 21:16  Bristol Temple Meads                    10    21:25
## 21:17  London Paddington                       8     21:21
## 21:25  London Paddington                       9     On time
## 21:25  Oxford                                  10    On time
## 21:26  Newbury                                 11    On time
## 21:33  Cheltenham Spa                          10    On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Newbury                                 1     On time
## 21:43  London Paddington                       14    On time
## 21:44  London Paddington                       12    On time
## 21:50  Basingstoke                             2     On time
## 21:50  Swansea                                 10    On time
## 21:52  Redhill                                 15B   On time
## 21:54  Worcester Foregate Street               11    On time
## 21:57  Gatwick Airport                         15B   On time
## 22:04  Penzance                                11    On time
## 22:09  Taunton                                 10    On time
## 22:13  London Paddington                       14    On time
## 22:17  London Paddington                       8     On time
## 22:22  Newbury                                 7A    On time
## 22:25  Gatwick Airport                         15B   On time
## 22:25  London Paddington                       9     On time
## 22:32  Oxford                                  14    On time
## 22:36  Cheltenham Spa                          10    On time
## 22:41  Manchester Piccadilly                   8B    On time
## 22:43  London Paddington                       14    On time
## 22:50  Basingstoke                             15    On time
## 22:53  London Paddington                       13    On time
## 22:55  London Paddington                       9     On time
## 23:01  Didcot Parkway                          15    On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
## 21:08  Virginia Water                          BUS   On time
## 21:27  Virginia Water                          BUS   On time
## 21:38  Virginia Water                          BUS   On time
## 21:57  Virginia Water                          BUS   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 22:03  Virginia Water                          BUS   On time
## 22:27  Virginia Water                          BUS   On time
## 22:33  Virginia Water                          BUS   On time
## 22:57  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-02 20:03:57
## Time   To                                      Plat  Expected
## 20:56  London Paddington                       10A   21:04
## 21:10  Newbury                                 1     On time
## 21:13  Swansea                                 9     On time
## 21:15  Birmingham New Street                   13    On time
##        via Coventry                            
## 21:15  Ealing Broadway                         15A   On time
## 21:18  London Paddington                       10    21:26
## 21:19  Oxford                                  8     21:22
## 21:22  Ealing Broadway                         14    On time
## 21:26  London Paddington                       10    On time
## 21:27  Bristol Temple Meads                    9     On time
## 21:32  London Paddington                       11    On time
## 21:33  Gatwick Airport                         4     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       10    On time
## 21:51  London Paddington                       10    On time
## 21:52  Bournemouth                             7B    On time
## 21:52  Ealing Broadway                         14    On time
## 21:56  London Paddington                       11    On time
## 21:57  Didcot Parkway                          12    On time
## 22:10  London Paddington                       11    On time
## 22:10  Newbury                                 1     On time
## 22:15  Ealing Broadway                         15    On time
## 22:15  London Paddington                       10    On time
## 22:19  Worcester Shrub Hill                    8     On time
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:34  London Paddington                       14    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10    On time
## 22:52  Ealing Broadway                         14    On time
## 22:52  Southampton Central                     8B    On time
## 22:57  Bristol Parkway                         9     On time
## 21:13  Virginia Water                          BUS   On time
## 21:23  Virginia Water                          BUS   On time
## 21:43  Virginia Water                          BUS   On time
## 21:53  Virginia Water                          BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 22:13  Virginia Water                          BUS   On time
## 22:23  Virginia Water                          BUS   On time
## 22:43  Virginia Water                          BUS   On time
## 22:53  Virginia Water                          BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
