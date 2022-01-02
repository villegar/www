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

## Example (Last rendered on 2022-01-02 16:06)

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
## Reading (RDG) Station Board on 2022-01-02 16:06:39
## Time   From                                    Plat  Expected
## 15:58  Exeter St Davids                        11    16:06
## 16:07  London Paddington                       9     16:05
## 16:08  Redhill                                 6     On time
## 16:09  Bristol Temple Meads                    10    16:11
## 16:13  Didcot Parkway                          15A   On time
## 16:13  London Paddington                       9B    On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12B   On time
## 16:15  Newbury                                 1     16:19
## 16:26  London Paddington                       7     16:40
## 16:32  Cheltenham Spa                          10A   16:42
## 16:33  Basingstoke                             2     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  Manchester Piccadilly                   13    16:47
## 16:43  London Paddington                       14    On time
## 16:47  Salisbury                               1     On time
## 16:47  Swansea                                 10    On time
## 16:53  London Paddington                       9     On time
## 16:58  Plymouth                                11    17:00
## 16:59  Great Malvern                           10A   On time
## 17:00  London Paddington                       7B    On time
## 17:07  London Paddington                       9     On time
## 17:07  Southampton Airport Parkway             8     On time
## 17:08  Redhill                                 6     On time
## 17:10  Bristol Temple Meads                    10    On time
## 17:13  Didcot Parkway                          15A   On time
## 17:13  London Paddington                       14    On time
## 17:13  London Paddington                       9B    On time
## 17:15  London Paddington                       12B   On time
## 17:20  Bedwyn                                  1     On time
## 17:26  London Paddington                       7     On time
## 17:33  Basingstoke                             2     On time
## 17:37  Paignton                                -     Cancelled
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   13    On time
## 17:43  London Paddington                       14    On time
## 17:45  Carmarthen                              11    On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Plymouth                                11    On time
## 17:59  Hereford                                10    On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 16:22  Virginia Water                          BUS   On time
## 16:31  Virginia Water                          BUS   On time
## 16:52  Virginia Water                          BUS   On time
## 17:01  Virginia Water                          BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
## 17:22  Virginia Water                          BUS   On time
## 17:31  Virginia Water                          BUS   On time
## 17:52  Virginia Water                          BUS   On time
## 18:01  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-02 16:06:43
## Time   To                                      Plat  Expected
## 15:58  London Paddington                       11    16:07
## 16:09  Swansea                                 9     On time
## 16:11  London Paddington                       10    16:12
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15A   On time
## 16:15  Hereford                                9B    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:22  Ealing Broadway                         14    On time
## 16:26  Didcot Parkway                          12B   On time
## 16:28  Penzance                                7     16:41
## 16:34  London Paddington                       10A   16:43
## 16:38  Basingstoke                             2     On time
## 16:41  Redhill                                 6     On time
## 16:44  Newbury                                 1     On time
## 16:50  London Paddington                       10    On time
## 16:52  Ealing Broadway                         14    On time
## 16:52  Southampton Airport Parkway             13    On time
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 16:59  London Paddington                       11    17:01
## 17:02  London Paddington                       10A   On time
## 17:03  Plymouth                                7B    On time
## 17:09  Swansea                                 9     On time
## 17:12  London Paddington                       10    On time
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15A   On time
## 17:14  Great Malvern                           9B    On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:22  Ealing Broadway                         14    On time
## 17:26  Didcot Parkway                          12B   On time
## 17:28  Penzance                                7     On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       -     Cancelled
## 17:41  Redhill                                 6     On time
## 17:44  Bedwyn                                  1     On time
## 17:50  London Paddington                       11    On time
## 17:52  Ealing Broadway                         14    On time
## 17:55  Bristol Temple Meads                    9     On time
## 17:59  London Paddington                       11    On time
## 18:00  Cheltenham Spa                          8     On time
## 18:02  London Paddington                       10    On time
## 16:05  Virginia Water                          BUS   On time
## 16:24  Virginia Water                          BUS   On time
## 16:35  Virginia Water                          BUS   On time
## 16:54  Virginia Water                          BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:05  Virginia Water                          BUS   On time
## 17:24  Virginia Water                          BUS   On time
## 17:35  Virginia Water                          BUS   On time
## 17:54  Virginia Water                          BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 18:05  Virginia Water                          BUS   On time
```
