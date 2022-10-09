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

## Example (Last rendered on 2022-10-09 14:05)

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
## Reading (RDG) Station Board on 2022-10-09 14:05:40
## Time   From                                    Plat  Expected
## 14:56  Bournemouth                             8B    On time
## 14:58  Great Malvern                           10    15:02
## 14:59  London Paddington                       9     On time
## 15:01  London Paddington                       7     15:03
## 15:05  Ascot                                   4     On time
## 15:08  Redhill                                 6     15:13
## 15:09  Bristol Temple Meads                    11    On time
## 15:09  London Paddington                       14    On time
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15    15:16
## 15:13  London Paddington                       12    On time
## 15:17  Penzance                                10    On time
## 15:18  Bedwyn                                  3     On time
## 15:23  London Paddington                       9     On time
## 15:35  Ascot                                   4     On time
## 15:38  Gatwick Airport                         5     On time
## 15:39  London Paddington                       14    On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:46  Swansea                                 11    On time
## 15:53  London Paddington                       9     On time
## 15:56  Hereford                                10    On time
## 15:59  London Paddington                       7     On time
## 16:01  London Paddington                       8     On time
## 16:05  Ascot                                   4     On time
## 16:08  Redhill                                 6     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:09  London Paddington                       14    On time
## 16:12  London Paddington                       9B    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       12    On time
## 16:15  Exeter St Davids                        11    On time
## 16:23  London Paddington                       9     On time
## 16:32  Cheltenham Spa                          10A   On time
## 16:35  Ascot                                   4     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  London Paddington                       14    On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:44  Swansea                                 10    On time
## 16:53  London Paddington                       9     On time
## 16:57  Worcester Shrub Hill                    10    On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:20  Basingstoke                             BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:20  Basingstoke                             BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:00  Winchester                              BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-09 14:05:44
## Time   To                                      Plat  Expected
## 15:02  London Paddington                       10    15:05
## 15:06  Plymouth                                9     On time
## 15:10  Swansea                                 7     On time
## 15:14  Great Malvern                           9B    On time
## 15:14  London Paddington                       15    15:17
## 15:15  London Paddington                       11    On time
## 15:15  Manchester Piccadilly                   8B    On time
##        via Stoke-on-Trent                      
## 15:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:18  London Paddington                       10    On time
## 15:21  Ascot                                   4     On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:25  Didcot Parkway                          12    On time
## 15:31  Ealing Broadway                         14    On time
## 15:41  Redhill                                 6     On time
## 15:43  Bedwyn                                  3     On time
## 15:45  London Paddington                       10    On time
## 15:48  London Paddington                       11    On time
## 15:52  Ascot                                   4     On time
## 15:55  Bristol Temple Meads                    9     On time
## 16:01  Ealing Broadway                         14    On time
## 16:02  London Paddington                       10    On time
## 16:06  Penzance                                7     On time
## 16:10  Swansea                                 8     On time
## 16:14  Hereford                                9B    On time
## 16:14  London Paddington                       15    On time
## 16:15  London Paddington                       10    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Stoke-on-Trent                      
## 16:17  London Paddington                       11    On time
## 16:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:21  Ascot                                   4     On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:31  Ealing Broadway                         14    On time
## 16:39  Redhill                                 6     On time
## 16:40  London Paddington                       10A   On time
## 16:43  Newbury                                 3     On time
## 16:46  Bournemouth                             13    On time
## 16:48  London Paddington                       10    On time
## 16:52  Ascot                                   4     On time
## 16:55  Bristol Temple Meads                    9     On time
## 17:01  Ealing Broadway                         14    On time
## 17:01  London Paddington                       10    On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:38  Basingstoke                             BUS   On time
## 15:52  Winchester                              BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:38  Basingstoke                             BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
