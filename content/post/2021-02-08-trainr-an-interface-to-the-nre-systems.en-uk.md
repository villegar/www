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

## Example (Last rendered on 2021-12-05 20:03)

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
## Reading (RDG) Station Board on 2021-12-05 20:03:32
## Time   From                                    Plat  Expected
## 19:56  Hereford                                13    19:58
## 19:58  Penzance                                11    20:00
## 20:07  London Paddington                       9     20:10
## 20:08  Redhill                                 15    On time
## 20:12  London Paddington                       8B    20:15
## 20:13  Didcot Parkway                          14A   On time
## 20:14  London Paddington                       13    On time
## 20:20  Newbury                                 1     On time
## 20:23  London Paddington                       12B   On time
## 20:26  London Paddington                       7     On time
## 20:27  London Waterloo                         6     On time
## 20:33  Basingstoke                             2     On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   8     20:42
## 20:40  Plymouth                                11    On time
## 20:43  Swansea                                 10    20:50
## 20:46  London Paddington                       14    On time
## 20:53  London Paddington                       9     On time
## 20:56  Great Malvern                           12A   On time
## 20:57  London Waterloo                         4     On time
## 20:58  Penzance                                11    On time
## 21:07  London Paddington                       9     On time
## 21:07  Southampton Central                     8     On time
## 21:08  Redhill                                 15B   On time
## 21:11  London Paddington                       7     On time
## 21:12  Taunton                                 10A   On time
## 21:13  Didcot Parkway                          13A   On time
## 21:16  London Paddington                       14    On time
## 21:19  Bedwyn                                  1     On time
## 21:23  London Paddington                       12B   On time
## 21:26  London Paddington                       7B    On time
## 21:27  London Waterloo                         6     On time
## 21:33  Basingstoke                             2     On time
## 21:39  Gatwick Airport                         15    On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:43  Swansea                                 10    21:50
## 21:46  London Paddington                       14    On time
## 21:52  London Paddington                       9     On time
## 21:57  London Waterloo                         4     On time
## 21:58  London Paddington                       8     On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-05 20:03:35
## Time   To                                      Plat  Expected
## 20:03  London Paddington                       11    On time
## 20:05  London Paddington                       13    On time
## 20:09  Swansea                                 9     20:11
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         14A   On time
## 20:14  Great Malvern                           8B    20:16
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:21  London Waterloo                         4     On time
## 20:22  Ealing Broadway                         13    On time
## 20:26  Didcot Parkway                          12B   On time
## 20:33  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:40  London Paddington                       11    On time
## 20:42  Newbury                                 1     On time
## 20:47  London Paddington                       10    20:54
## 20:51  Ealing Broadway                         14    On time
## 20:51  London Waterloo                         6     On time
## 20:52  Southampton Central                     8     On time
## 20:55  Weston-super-Mare                       9     On time
## 21:03  London Paddington                       11    On time
## 21:05  London Paddington                       12A   On time
## 21:09  Swansea                                 9     On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Ealing Broadway                         13A   On time
## 21:14  Worcester Shrub Hill                    7     On time
## 21:15  London Paddington                       10A   On time
## 21:21  London Waterloo                         4     On time
## 21:22  Ealing Broadway                         14    On time
## 21:25  Didcot Parkway                          12B   On time
## 21:27  Exeter St Davids                        7B    On time
## 21:38  Basingstoke                             2     On time
## 21:44  Bedwyn                                  1     On time
## 21:47  London Paddington                       10    21:54
## 21:51  Ealing Broadway                         14    On time
## 21:51  London Waterloo                         6     On time
## 21:52  Southampton Central                     8     On time
## 21:54  Oxford                                  9     On time
## 22:00  Bristol Temple Meads                    8     On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
