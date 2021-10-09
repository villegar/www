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

## Example (Last rendered on 2021-10-09 10:03)

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
## Reading (RDG) Station Board on 2021-10-09 10:03:38
## Time   From                                    Plat  Expected
## 11:01  Penzance                                11    11:06
## 11:02  Didcot Parkway                          15    On time
## 11:05  Bournemouth                             13B   11:16
## 11:10  Bristol Temple Meads                    10    11:14
## 11:13  London Paddington                       14    On time
## 11:14  London Waterloo                         4     On time
## 11:17  London Paddington                       9B    On time
## 11:21  Newbury                                 11    On time
## 11:23  Oxford                                  10    On time
## 11:25  London Paddington                       9     On time
## 11:27  London Paddington                       7     On time
## 11:33  London Paddington                       7     On time
## 11:33  Redhill                                 5     On time
## 11:34  Cheltenham Spa                          11A   On time
## 11:39  Manchester Piccadilly                   13    On time
## 11:40  Bristol Temple Meads                    10    11:45
## 11:41  London Paddington                       9     On time
## 11:41  Newbury                                 1     On time
## 11:43  London Paddington                       14    On time
## 11:43  Paignton                                11    On time
## 11:44  London Paddington                       12    On time
## 11:44  London Waterloo                         6     On time
## 11:47  London Paddington                       9B    On time
## 11:48  Swansea                                 11    On time
## 11:51  Gatwick Airport                         4     On time
## 11:51  London Paddington                       8B    On time
## 11:54  Great Malvern                           10A   On time
## 11:55  London Paddington                       9     On time
## 11:56  Basingstoke                             2     On time
## 12:00  Penzance                                11    On time
## 12:02  Didcot Parkway                          15    On time
## 12:10  Bristol Temple Meads                    10    On time
## 12:13  London Paddington                       14    On time
## 12:14  London Waterloo                         5     On time
## 12:17  London Paddington                       9     On time
## 12:23  Newbury                                 11    On time
## 12:25  London Paddington                       9     On time
## 12:25  Oxford                                  10    On time
## 12:27  London Paddington                       7     On time
## 12:33  London Paddington                       7     On time
## 12:33  Redhill                                 4     On time
## 12:34  Cheltenham Spa                          11    On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:41  London Paddington                       8     On time
## 12:42  Newbury                                 1     On time
## 12:43  London Paddington                       14    On time
## 12:44  London Paddington                       12    On time
## 12:44  London Waterloo                         6     On time
## 12:46  Swansea                                 11    On time
## 12:47  London Paddington                       9     On time
## 12:51  Basingstoke                             2     On time
## 12:51  Gatwick Airport                         5     On time
## 12:53  London Paddington                       9     On time
## 12:54  Great Malvern                           10    On time
## 12:58  London Paddington                       -     Cancelled
## 11:21  Heathrow Central Bus Stn                BUS   On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-09 10:03:41
## Time   To                                      Plat  Expected
## 11:05  London Paddington                       11    11:07
## 11:09  London Waterloo                         6     On time
## 11:10  Newbury                                 1     On time
## 11:12  London Paddington                       10    11:15
## 11:15  Ealing Broadway                         15    On time
## 11:15  Manchester Piccadilly                   13B   11:17
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Foregate Street               9B    On time
## 11:20  Redhill                                 5     On time
## 11:22  Ealing Broadway                         14    On time
## 11:24  London Paddington                       11    On time
## 11:27  Bristol Temple Meads                    9     On time
## 11:27  London Paddington                       10    On time
## 11:30  Plymouth                                7     On time
## 11:35  London Paddington                       11A   On time
## 11:35  Newbury                                 7     On time
## 11:38  Basingstoke                             2     On time
## 11:39  London Waterloo                         4     On time
## 11:42  London Paddington                       10    11:46
## 11:43  Swansea                                 9     On time
## 11:45  London Paddington                       11    On time
## 11:49  Oxford                                  9B    On time
## 11:50  London Paddington                       11    On time
## 11:52  Ealing Broadway                         14    On time
## 11:53  Cheltenham Spa                          8B    On time
## 11:54  Didcot Parkway                          12    On time
## 11:57  London Paddington                       10A   On time
## 11:57  Weston-super-Mare                       9     On time
## 12:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:05  London Paddington                       11    On time
## 12:09  London Waterloo                         6     On time
## 12:11  Ealing Broadway                         15    On time
## 12:12  London Paddington                       10    On time
## 12:12  Newbury                                 1     On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Hereford                                9     On time
## 12:20  Redhill                                 4     On time
## 12:22  Ealing Broadway                         14    On time
## 12:24  London Paddington                       11    On time
## 12:27  Bristol Temple Meads                    9     On time
## 12:27  London Paddington                       10    On time
## 12:30  Penzance                                7     On time
## 12:35  London Paddington                       11    On time
## 12:35  Newbury                                 7     On time
## 12:38  Basingstoke                             2     On time
## 12:39  London Waterloo                         5     On time
## 12:42  London Paddington                       10    On time
## 12:43  Swansea                                 8     On time
## 12:48  London Paddington                       11    On time
## 12:49  Oxford                                  9     On time
## 12:52  Bournemouth                             7     On time
## 12:52  Ealing Broadway                         14    On time
## 12:53  Didcot Parkway                          12    On time
## 12:55  Weston-super-Mare                       9     On time
## 12:57  London Paddington                       10    On time
## 13:01  Exeter St Davids                        -     Cancelled
## 13:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
