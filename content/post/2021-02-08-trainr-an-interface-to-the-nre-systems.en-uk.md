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

## Example (Last rendered on 2021-12-05 12:03)

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
## Reading (RDG) Station Board on 2021-12-05 12:03:53
## Time   From                                    Plat  Expected
## 11:56  Great Malvern                           10A   11:53
## 11:57  Plymouth                                11    12:04
## 12:07  London Paddington                       8     Delayed
## 12:08  Redhill                                 6     On time
## 12:09  Bristol Temple Meads                    11    12:13
## 12:10  Didcot Parkway                          15A   On time
## 12:12  London Paddington                       9     On time
## 12:15  London Paddington                       14    On time
## 12:19  Newbury                                 1     On time
## 12:24  London Paddington                       13B   On time
## 12:26  London Paddington                       7     On time
## 12:27  London Waterloo                         4     On time
## 12:31  Cheltenham Spa                          11A   On time
## 12:33  Basingstoke                             2     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  Manchester Piccadilly                   13    On time
## 12:43  Swansea                                 10    12:51
## 12:46  London Paddington                       14    On time
## 12:47  Salisbury                               1     12:49
## 12:53  London Paddington                       9     On time
## 12:55  Penzance                                11    13:06
## 12:56  Oxford                                  10    On time
## 12:57  London Waterloo                         4     On time
## 13:01  London Paddington                       8     On time
## 13:07  London Paddington                       9     On time
## 13:07  Southampton Central                     13    On time
## 13:08  Redhill                                 6     On time
## 13:09  Weston-super-Mare                       11    On time
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       9B    On time
## 13:15  London Paddington                       14    On time
## 13:17  Bedwyn                                  1     On time
## 13:22  London Paddington                       13B   On time
## 13:26  London Paddington                       7     On time
## 13:26  Paignton                                11    On time
## 13:27  London Waterloo                         4     On time
## 13:33  Basingstoke                             2     On time
## 13:38  Gatwick Airport                         5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    10    On time
## 13:43  Swansea                                 11    13:51
## 13:44  London Paddington                       14    On time
## 13:47  Salisbury                               1     On time
## 13:53  London Paddington                       9     On time
## 13:57  London Waterloo                         4     On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-05 12:03:57
## Time   To                                      Plat  Expected
## 12:03  London Paddington                       11    12:05
## 12:05  London Paddington                       10A   On time
## 12:09  Swansea                                 8     Delayed
## 12:12  Ealing Broadway                         15A   On time
## 12:12  Salisbury                               1     On time
## 12:14  Hereford                                9     On time
## 12:15  London Paddington                       11    12:16
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:21  London Waterloo                         4     On time
## 12:22  Ealing Broadway                         14    On time
## 12:25  Didcot Parkway                          13B   On time
## 12:30  Penzance                                7     On time
## 12:38  Basingstoke                             2     On time
## 12:40  London Paddington                       11A   On time
## 12:41  Redhill                                 6     On time
## 12:44  Newbury                                 1     On time
## 12:45  London Paddington                       10    12:56
## 12:51  London Waterloo                         4     On time
## 12:54  Ealing Broadway                         14    On time
## 12:55  Weston-super-Mare                       9     On time
## 13:03  Exeter St Davids                        8     On time
## 13:03  London Paddington                       11    13:07
## 13:05  London Paddington                       10    On time
## 13:09  Swansea                                 9     On time
## 13:12  Ealing Broadway                         15    On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:14  Great Malvern                           9B    On time
## 13:15  London Paddington                       11    On time
## 13:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 13:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:21  London Waterloo                         4     On time
## 13:22  Ealing Broadway                         14    On time
## 13:30  Plymouth                                7     On time
## 13:32  Didcot Parkway                          13B   On time
## 13:35  London Paddington                       11    On time
## 13:38  Basingstoke                             2     On time
## 13:41  Redhill                                 6     On time
## 13:44  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:47  London Paddington                       11    13:54
## 13:51  London Waterloo                         4     On time
## 13:52  Southampton Central                     7     On time
## 13:54  Ealing Broadway                         14    On time
## 13:55  Bristol Temple Meads                    9     On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
```
