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

## Example (Last rendered on 2022-10-09 16:05)

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
## Reading (RDG) Station Board on 2022-10-09 16:05:06
## Time   From                                    Plat  Expected
## 16:56  Bournemouth                             8     On time
## 16:59  London Paddington                       9     17:05
## 17:01  London Paddington                       7     17:03
## 17:07  Ascot                                   4     On time
## 17:09  London Paddington                       14    17:11
## 17:10  Bristol Temple Meads                    10    On time
## 17:10  Redhill                                 6     17:22
## 17:12  London Paddington                       9     On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       12    On time
## 17:15  Penzance                                11    On time
## 17:20  Bedwyn                                  3     On time
## 17:23  London Paddington                       9     On time
## 17:35  Ascot                                   4     On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  London Paddington                       14    On time
## 17:39  Manchester Piccadilly                   13    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:41  Westbury                                11    On time
## 17:42  London Paddington                       9B    On time
## 17:46  Carmarthen                              11    17:50
## 17:53  London Paddington                       9     On time
## 17:57  Hereford                                10    On time
## 17:59  London Paddington                       9B    On time
## 18:01  London Paddington                       8     On time
## 18:05  Ascot                                   4     On time
## 18:06  Bristol Temple Meads                    10    On time
## 18:08  Redhill                                 6     On time
## 18:09  London Paddington                       14    On time
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       12    On time
## 18:14  Plymouth                                11    On time
## 18:21  Newbury                                 1     On time
## 18:25  London Paddington                       9     On time
## 18:33  Cheltenham Spa                          10    On time
## 18:35  Ascot                                   4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  London Paddington                       14    On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:42  London Paddington                       8B    On time
## 18:44  Swansea                                 10    On time
## 18:53  London Paddington                       9     On time
## 18:56  Great Malvern                           10    On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:20  Basingstoke                             BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:20  Basingstoke                             BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:00  Winchester                              BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-09 16:05:10
## Time   To                                      Plat  Expected
## 17:06  Penzance                                9     On time
## 17:10  Swansea                                 7     On time
## 17:14  Great Malvern                           9     On time
## 17:14  London Paddington                       15    On time
## 17:15  London Paddington                       10    On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Stoke-on-Trent                      
## 17:17  London Paddington                       11    On time
## 17:18  Gatwick Airport                         5     17:28
##        via Guildford                           
## 17:21  Ascot                                   4     On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12    On time
## 17:31  Ealing Broadway                         14    On time
## 17:41  Redhill                                 -     Cancelled
## 17:43  Bedwyn                                  3     On time
## 17:43  London Paddington                       11    On time
## 17:45  London Paddington                       10    On time
## 17:48  London Paddington                       11    17:51
## 17:48  Oxford                                  9B    On time
## 17:52  Ascot                                   4     On time
## 17:55  Bristol Temple Meads                    9     On time
## 18:01  Cheltenham Spa                          9B    On time
## 18:01  Ealing Broadway                         14    On time
## 18:01  London Paddington                       10    On time
## 18:10  Swansea                                 8     On time
## 18:14  Great Malvern                           9B    On time
## 18:14  London Paddington                       15    On time
## 18:15  London Paddington                       10    On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Stoke-on-Trent                      
## 18:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:21  Ascot                                   4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:25  Penzance                                8     On time
## 18:28  Bristol Temple Meads                    9     On time
## 18:31  Ealing Broadway                         14    On time
## 18:38  London Paddington                       10    On time
## 18:39  Redhill                                 -     On time
## 18:43  Newbury                                 1     On time
## 18:45  London Paddington                       11    On time
## 18:46  Bournemouth                             13    On time
## 18:48  London Paddington                       10    On time
## 18:48  Oxford                                  8B    On time
## 18:52  Ascot                                   4     On time
## 18:55  Bristol Temple Meads                    9     On time
## 19:01  Ealing Broadway                         14    On time
## 19:02  London Paddington                       10    On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:38  Basingstoke                             BUS   On time
## 17:52  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Basingstoke                             BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
