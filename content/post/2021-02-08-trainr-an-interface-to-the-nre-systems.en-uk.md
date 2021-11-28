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

## Example (Last rendered on 2021-11-28 16:03)

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
## Reading (RDG) Station Board on 2021-11-28 16:03:30
## Time   From                                    Plat  Expected
## 15:39  Manchester Piccadilly                   13    16:08
## 15:43  Swansea                                 11    16:07
## 15:55  Hereford                                10    16:03
## 15:58  Exeter St Davids                        11    16:01
## 15:59  London Paddington                       8     16:18
## 16:08  Redhill                                 6     On time
## 16:09  Bristol Temple Meads                    11    16:15
## 16:12  London Paddington                       9B    On time
## 16:12  Newbury                                 3     16:15
## 16:13  Didcot Parkway                          15    16:19
## 16:13  London Paddington                       14    On time
## 16:23  Slough                                  12    On time
## 16:24  London Paddington                       9     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  Manchester Piccadilly                   13B   17:04
## 16:43  Swansea                                 10    16:54
## 16:44  London Paddington                       14    On time
## 16:54  London Paddington                       9     On time
## 16:58  Bournemouth                             13    On time
## 16:58  Great Malvern                           10    On time
## 16:58  Penzance                                11    17:15
## 16:59  London Paddington                       8     On time
## 17:05  London Waterloo                         -     Cancelled
## 17:09  Weston-super-Mare                       11    On time
## 17:12  London Paddington                       9     On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       14    On time
## 17:13  Redhill                                 6     On time
## 17:20  Bedwyn                                  3     On time
## 17:23  Slough                                  12    On time
## 17:24  London Paddington                       9     On time
## 17:27  London Paddington                       7     On time
## 17:38  Exeter St Davids                        12    On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   13    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:43  Swansea                                 11    17:46
## 17:44  London Paddington                       14    On time
## 17:54  London Paddington                       9     On time
## 16:18  Basingstoke                             BUS   On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 16:26  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:56  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:00  Winchester                              BUS   On time
## 17:18  Bramley (Hampshire)                     BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
## 17:26  Staines                                 BUS   On time
## 17:27  Staines                                 BUS   On time
## 17:56  Staines                                 BUS   On time
## 17:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-28 16:03:34
## Time   To                                      Plat  Expected
## 15:49  London Paddington                       11    16:08
## 16:05  Ealing Broadway                         14    On time
## 16:05  London Paddington                       11    On time
## 16:07  London Paddington                       10    On time
## 16:09  Swansea                                 8     16:19
## 16:14  Hereford                                9B    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:19  London Paddington                       11    On time
## 16:25  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:25  Slough                                  15    On time
## 16:30  Penzance                                7     On time
## 16:36  Ealing Broadway                         14    On time
## 16:38  Redhill                                 6     On time
## 16:44  Newbury                                 3     On time
## 16:46  Bournemouth                             13B   17:05
## 16:49  London Paddington                       10    16:55
## 16:55  Exeter St Davids                        9     On time
##        via Bristol                             
## 17:03  Plymouth                                7B    On time
## 17:05  London Paddington                       11    17:16
## 17:06  Ealing Broadway                         14    On time
## 17:07  London Paddington                       10    On time
## 17:09  Swansea                                 8     On time
## 17:14  Great Malvern                           9     On time
## 17:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 17:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:19  London Paddington                       11    On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12    On time
## 17:25  Slough                                  15    On time
## 17:30  Penzance                                7     On time
## 17:36  Ealing Broadway                         14    On time
## 17:41  Redhill                                 6     On time
## 17:42  London Paddington                       12    On time
## 17:44  Bedwyn                                  3     On time
## 17:45  London Paddington                       10    On time
## 17:49  London Paddington                       11    On time
## 17:55  Weston-super-Mare                       9     On time
## 16:25  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:38  Basingstoke                             BUS   On time
## 16:55  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:25  Staines                                 BUS   On time
## 17:27  Staines                                 BUS   On time
## 17:38  Bramley (Hampshire)                     BUS   On time
## 17:52  Winchester                              BUS   On time
## 17:55  Staines                                 BUS   On time
## 17:57  Staines                                 BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
