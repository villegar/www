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

## Example (Last rendered on 2022-10-09 12:08)

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
## Reading (RDG) Station Board on 2022-10-09 12:08:49
## Time   From                                    Plat  Expected
## 12:57  Bournemouth                             8B    12:52
## 13:01  London Paddington                       7     13:05
## 13:08  Redhill                                 6     13:12
## 13:09  London Paddington                       14    13:11
## 13:10  Bristol Temple Meads                    10    13:15
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       9     On time
## 13:13  London Paddington                       13    On time
## 13:14  Penzance                                11    13:18
## 13:17  Bedwyn                                  1     13:19
## 13:35  Ascot                                   4     On time
## 13:38  Gatwick Airport                         5     13:42
## 13:39  London Paddington                       14    On time
## 13:39  Manchester Piccadilly                   12    On time
## 13:40  Bristol Temple Meads                    10    On time
## 13:40  Westbury                                11    On time
## 13:45  Swansea                                 11    On time
## 13:53  London Paddington                       9     On time
## 13:56  Great Malvern                           10    On time
## 13:59  London Paddington                       7     On time
## 14:01  London Paddington                       8     On time
## 14:05  Ascot                                   4     On time
## 14:08  Redhill                                 15    On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:09  London Paddington                       14    On time
## 14:10  Didcot Parkway                          13    On time
## 14:12  London Paddington                       9     On time
## 14:15  Penzance                                11    On time
## 14:19  London Paddington                       13    On time
## 14:19  Newbury                                 1     On time
## 14:26  London Paddington                       7     On time
## 14:35  Ascot                                   4     On time
## 14:38  Gatwick Airport                         5     On time
## 14:39  London Paddington                       14    On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:44  Carmarthen                              10    On time
## 14:53  London Paddington                       9     On time
## 14:58  Great Malvern                           10    On time
## 14:59  London Paddington                       9     On time
## 15:05  Ascot                                   4     On time
## 13:20  Basingstoke                             BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:20  Basingstoke                             BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 15:00  Winchester                              BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-09 12:08:53
## Time   To                                      Plat  Expected
## 13:10  Swansea                                 7     On time
## 13:14  Great Malvern                           9     On time
## 13:14  London Paddington                       15    On time
## 13:15  London Paddington                       10    13:16
## 13:15  Manchester Piccadilly                   8B    On time
##        via Stoke-on-Trent                      
## 13:17  London Paddington                       11    13:19
## 13:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:21  Ascot                                   4     On time
## 13:26  Didcot Parkway                          13    On time
## 13:31  Ealing Broadway                         14    On time
## 13:41  Redhill                                 6     On time
## 13:42  London Paddington                       11    On time
## 13:43  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:48  London Paddington                       11    On time
## 13:52  Ascot                                   4     On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:01  Ealing Broadway                         14    On time
## 14:01  London Paddington                       10    On time
## 14:06  Penzance                                7     On time
## 14:10  Carmarthen                              8     On time
## 14:14  Hereford                                9     On time
## 14:14  London Paddington                       13    On time
## 14:15  London Paddington                       10    On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Stoke-on-Trent                      
## 14:17  London Paddington                       11    On time
## 14:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:21  Ascot                                   4     On time
## 14:25  Didcot Parkway                          13    On time
## 14:28  Westbury                                7     On time
## 14:31  Ealing Broadway                         14    On time
## 14:39  Redhill                                 15    On time
## 14:43  Newbury                                 1     On time
## 14:46  Bournemouth                             13    On time
## 14:48  London Paddington                       10    On time
## 14:52  Ascot                                   4     On time
## 14:55  Bristol Temple Meads                    9     On time
## 15:01  Ealing Broadway                         14    On time
## 15:02  London Paddington                       10    On time
## 15:06  Plymouth                                9     On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:38  Basingstoke                             BUS   On time
## 13:52  Winchester                              BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:38  Basingstoke                             BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
