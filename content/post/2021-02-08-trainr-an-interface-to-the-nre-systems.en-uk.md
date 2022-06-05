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

## Example (Last rendered on 2022-06-05 18:04)

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
## Reading (RDG) Station Board on 2022-06-05 18:04:47
## Time   From                                    Plat  Expected
## 17:57  Newquay                                 11    19:20
## 18:58  Penzance                                11    20:12
## 19:00  Great Malvern                           10A   19:04
## 19:02  London Waterloo                         4     19:05
## 19:03  London Paddington                       14    19:05
## 19:05  Southampton Central                     8     On time
## 19:07  London Paddington                       9     On time
## 19:08  Redhill                                 15    On time
## 19:09  Bristol Temple Meads                    10    19:21
## 19:12  London Paddington                       9     On time
## 19:13  Didcot Parkway                          13    On time
## 19:13  London Paddington                       12    On time
## 19:19  Bedwyn                                  1     On time
## 19:26  London Paddington                       8     19:31
## 19:32  London Waterloo                         6     On time
## 19:33  London Paddington                       14    On time
## 19:34  Basingstoke                             2     On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  London Paddington                       9     On time
## 19:39  Manchester Piccadilly                   7B    19:49
## 19:40  Paignton                                -     Cancelled
## 19:48  Carmarthen                              10    On time
## 19:53  London Paddington                       9     On time
## 19:57  Plymouth                                11    20:26
## 20:00  Hereford                                10    On time
## 20:02  London Waterloo                         4     On time
## 20:04  London Paddington                       14    On time
## 20:07  London Paddington                       8     On time
## 20:08  Redhill                                 15    On time
## 20:12  Exeter St Davids                        10    On time
## 20:12  London Paddington                       9B    On time
## 20:13  Didcot Parkway                          13    On time
## 20:19  London Paddington                       12    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:32  London Waterloo                         6     On time
## 20:33  Basingstoke                             2     On time
## 20:33  London Paddington                       14    On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:42  Exeter St Davids                        11    On time
## 20:49  Swansea                                 10    On time
## 20:58  Penzance                                11    On time
## 21:00  Great Malvern                           10A   On time
## 21:02  London Waterloo                         4     On time
## 21:03  London Paddington                       14    On time
## 19:38  Heathrow Central Bus Stn                BUS   On time
## 20:30  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-05 18:04:51
## Time   To                                      Plat  Expected
## 17:59  London Paddington                       11    19:21
## 18:59  London Paddington                       11    20:13
## 19:02  London Paddington                       10A   19:05
## 19:09  Swansea                                 9     On time
## 19:11  London Paddington                       10    19:22
## 19:13  Ealing Broadway                         13    On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:24  Ealing Broadway                         14    On time
## 19:24  London Waterloo                         4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:28  Plymouth                                8     19:32
## 19:38  Basingstoke                             2     On time
## 19:40  Swindon                                 9     On time
## 19:42  London Paddington                       -     Cancelled
## 19:43  Bedwyn                                  1     On time
## 19:50  London Paddington                       10    On time
## 19:52  Bournemouth                             7B    On time
## 19:54  Ealing Broadway                         14    On time
## 19:54  London Waterloo                         6     On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:58  London Paddington                       11    20:26
## 20:02  London Paddington                       10    On time
## 20:09  Swansea                                 8     On time
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         13    On time
## 20:14  Great Malvern                           9B    On time
## 20:14  London Paddington                       10    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:24  Ealing Broadway                         14    On time
## 20:24  London Waterloo                         4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:28  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:43  Newbury                                 1     On time
## 20:44  London Paddington                       11    On time
## 20:50  London Paddington                       10    On time
## 20:52  Bournemouth                             8     On time
## 20:54  Ealing Broadway                         14    On time
## 20:54  London Waterloo                         6     On time
## 20:59  London Paddington                       11    On time
## 21:02  London Paddington                       10A   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
