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

## Example (Last rendered on 2022-10-09 10:04)

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
## Reading (RDG) Station Board on 2022-10-09 10:04:25
## Time   From                                    Plat  Expected
## 10:57  Worcester Shrub Hill                    11A   11:06
## 10:59  London Paddington                       9B    11:04
## 11:01  London Paddington                       7     On time
## 11:05  Bristol Temple Meads                    10    11:52
## 11:06  Ascot                                   4     On time
## 11:09  London Paddington                       14    11:11
## 11:10  Didcot Parkway                          15    On time
## 11:10  Redhill                                 6     On time
## 11:12  London Paddington                       9     11:14
## 11:14  Swansea                                 11    On time
## 11:15  London Paddington                       12    11:27
## 11:19  Bedwyn                                  1     11:21
## 11:35  Ascot                                   4     On time
## 11:38  Gatwick Airport                         5     On time
## 11:39  Birmingham New Street                   13    On time
## 11:39  London Paddington                       14    On time
## 11:44  Swansea                                 11    On time
## 11:48  Plymouth                                10    11:50
## 11:53  London Paddington                       9     On time
## 11:56  Great Malvern                           10    On time
## 11:59  London Paddington                       7     On time
## 12:01  London Paddington                       8     On time
## 12:05  Ascot                                   4     On time
## 12:06  Westbury                                11    On time
## 12:08  Redhill                                 6     On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:09  London Paddington                       14    On time
## 12:10  Didcot Parkway                          15    On time
## 12:12  London Paddington                       9     On time
## 12:13  London Paddington                       12    On time
## 12:22  Newbury                                 1     On time
## 12:31  Cheltenham Spa                          11    On time
## 12:35  Ascot                                   4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  London Paddington                       14    On time
## 12:39  Manchester Piccadilly                   13    On time
## 12:45  Swansea                                 10    On time
## 12:53  London Paddington                       9     On time
## 12:56  Great Malvern                           10    On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:20  Basingstoke                             BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 13:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-09 10:04:29
## Time   To                                      Plat  Expected
## 11:01  London Paddington                       11A   11:07
## 11:06  Plymouth                                9B    On time
## 11:10  Swansea                                 7     On time
## 11:14  London Paddington                       15    On time
## 11:14  Worcester Shrub Hill                    9     On time
## 11:15  London Paddington                       10    11:53
## 11:15  Manchester Piccadilly                   8     On time
##        via Stoke-on-Trent                      
## 11:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:18  London Paddington                       11    On time
## 11:21  Ascot                                   4     On time
## 11:26  Didcot Parkway                          12    11:28
## 11:31  Ealing Broadway                         14    On time
## 11:41  Redhill                                 6     On time
## 11:43  Bedwyn                                  1     On time
## 11:45  London Paddington                       11    On time
## 11:48  London Paddington                       10    11:50
## 11:52  Ascot                                   4     On time
## 11:55  Bristol Temple Meads                    9     On time
## 12:01  Ealing Broadway                         14    On time
## 12:02  London Paddington                       10    On time
## 12:06  Penzance                                7     On time
## 12:10  Carmarthen                              8     On time
## 12:14  London Paddington                       15    On time
## 12:15  London Paddington                       11    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Stoke-on-Trent                      
## 12:17  London Paddington                       10    On time
## 12:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:18  Hereford                                9     On time
## 12:21  Ascot                                   4     On time
## 12:26  Didcot Parkway                          12    On time
## 12:31  Ealing Broadway                         14    On time
## 12:39  Redhill                                 6     On time
## 12:40  London Paddington                       11    On time
## 12:43  Newbury                                 1     On time
## 12:46  Bournemouth                             13    On time
## 12:46  London Paddington                       10    On time
## 12:52  Ascot                                   4     On time
## 12:55  Bristol Temple Meads                    9     On time
## 13:01  Ealing Broadway                         14    On time
## 13:01  London Paddington                       10    On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:38  Basingstoke                             BUS   On time
## 11:52  Winchester                              BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:38  Basingstoke                             BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
