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

## Example (Last rendered on 2022-06-19 10:03)

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
## Reading (RDG) Station Board on 2022-06-19 10:03:53
## Time   From                                    Plat  Expected
## 10:41  Exeter St Davids                        10    11:01
## 10:43  Swansea                                 10    11:15
## 10:59  London Paddington                       7     11:03
## 11:03  London Waterloo                         4     11:10
## 11:05  Bournemouth                             8B    11:07
## 11:05  Bristol Temple Meads                    10    11:12
## 11:08  London Paddington                       12    On time
## 11:08  Redhill                                 6     11:11
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       9B    On time
## 11:15  London Paddington                       15B   On time
## 11:19  Bedwyn                                  1     11:29
## 11:26  London Paddington                       7     11:34
## 11:32  London Waterloo                         4     On time
## 11:32  Swansea                                 10    12:03
## 11:33  Basingstoke                             2     On time
## 11:35  Plymouth                                11    11:55
## 11:38  Gatwick Airport                         5     On time
## 11:39  London Paddington                       14    On time
## 11:39  Manchester Piccadilly                   7     11:41
## 11:47  Salisbury                               1     On time
## 11:50  London Paddington                       9     On time
## 11:53  London Paddington                       8     On time
## 11:56  Great Malvern                           10A   On time
## 11:58  Plymouth                                7     On time
## 12:00  Swansea                                 11    12:10
## 12:06  London Waterloo                         4     12:15
## 12:08  London Paddington                       14    On time
## 12:08  Redhill                                 6     On time
## 12:10  Didcot Parkway                          15A   On time
## 12:12  London Paddington                       9     On time
## 12:13  London Paddington                       12    On time
## 12:16  Bristol Temple Meads                    10    On time
## 12:19  Newbury                                 1     On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10A   On time
## 12:33  Basingstoke                             2     On time
## 12:36  London Waterloo                         4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  London Paddington                       14    On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:47  Salisbury                               1     On time
## 12:47  Swindon                                 10    On time
## 12:50  London Paddington                       9     On time
## 12:53  London Paddington                       8     On time
## 12:55  Penzance                                11    On time
## 12:56  Great Malvern                           10A   On time
## 12:59  London Paddington                       7     13:08
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-19 10:03:57
## Time   To                                      Plat  Expected
## 10:44  London Paddington                       10    11:03
## 10:46  London Paddington                       10    11:16
## 11:01  Ealing Broadway                         -     Cancelled
## 11:01  Paignton                                7     11:04
## 11:11  London Paddington                       10    11:13
## 11:12  Salisbury                               1     On time
## 11:14  Great Malvern                           9B    On time
## 11:14  London Paddington                       15    On time
## 11:15  Manchester Piccadilly                   8B    On time
##        via Stoke-on-Trent                      
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:24  London Waterloo                         4     On time
## 11:26  Didcot Parkway                          15B   On time
## 11:28  Plymouth                                7     11:35
## 11:31  Ealing Broadway                         12A   On time
## 11:35  London Waterloo                         5     On time
## 11:38  Basingstoke                             2     On time
## 11:41  Redhill                                 6     On time
## 11:43  Bedwyn                                  1     On time
## 11:43  London Paddington                       10    12:04
## 11:44  London Paddington                       11    11:56
## 11:52  Bournemouth                             7     On time
## 11:52  Carmarthen                              9     On time
## 11:54  London Waterloo                         4     On time
## 11:56  Bristol Temple Meads                    8     On time
## 11:59  London Paddington                       7     On time
## 12:01  Ealing Broadway                         14A   On time
## 12:02  London Paddington                       11    12:11
## 12:04  London Paddington                       10A   On time
## 12:12  Salisbury                               1     On time
## 12:14  London Paddington                       15A   On time
## 12:15  Manchester Piccadilly                   13B   On time
##        via Stoke-on-Trent                      
## 12:17  London Paddington                       10    On time
## 12:18  Hereford                                9     On time
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:24  London Waterloo                         4     On time
## 12:26  Didcot Parkway                          12    On time
## 12:28  Penzance                                7     On time
## 12:31  Ealing Broadway                         14    On time
## 12:35  Twickenham                              5     On time
## 12:38  Basingstoke                             2     On time
## 12:41  London Paddington                       10A   On time
## 12:41  Redhill                                 6     On time
## 12:43  Newbury                                 1     On time
## 12:47  London Paddington                       10    On time
## 12:52  Swansea                                 9     On time
## 12:54  London Waterloo                         4     On time
## 12:56  Weston-super-Mare                       8     On time
## 12:57  London Paddington                       11    On time
## 13:00  London Paddington                       10A   On time
## 13:01  Ealing Broadway                         14    On time
## 13:01  Paignton                                7     13:09
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
