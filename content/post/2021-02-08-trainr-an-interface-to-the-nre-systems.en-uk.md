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

## Example (Last rendered on 2022-01-25 08:04)

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
## Reading (RDG) Station Board on 2022-01-25 08:04:07
## Time   From                                    Plat  Expected
## 08:01  Plymouth                                11    08:13
## 08:06  Basingstoke                             2     On time
## 08:09  Bournemouth                             8     On time
## 08:10  Didcot Parkway                          15    On time
## 08:10  London Waterloo                         4     08:18
## 08:10  Oxford                                  10A   Delayed
## 08:11  London Paddington                       9     On time
## 08:13  London Paddington                       14    On time
## 08:14  London Paddington                       13B   On time
## 08:14  Worcester Shrub Hill                    11    On time
## 08:16  London Paddington                       9B    On time
## 08:16  Redhill                                 6     On time
## 08:18  Swansea                                 10    On time
## 08:22  Newbury                                 3     On time
## 08:25  London Paddington                       9     On time
## 08:26  Cheltenham Spa                          10A   On time
## 08:27  London Paddington                       7     On time
## 08:28  London Paddington                       14    On time
## 08:34  Gatwick Airport                         5     On time
## 08:39  Weston-super-Mare                       11    On time
## 08:40  London Waterloo                         6     On time
## 08:42  Basingstoke                             2     On time
## 08:43  London Paddington                       9     On time
## 08:43  London Paddington                       14    On time
## 08:44  Didcot Parkway                          15    On time
## 08:46  Manchester Piccadilly                   7B    On time
## 08:50  London Paddington                       12    On time
## 08:51  London Paddington                       9B    On time
## 08:53  Plymouth                                11    08:56
## 08:55  London Paddington                       8     On time
## 08:58  London Paddington                       14    On time
## 09:01  Didcot Parkway                          15    On time
## 09:02  Basingstoke                             1     On time
## 09:04  Redhill                                 5     On time
## 09:04  Taunton                                 10A   On time
## 09:05  Bournemouth                             8     On time
## 09:09  Newbury                                 11    On time
## 09:11  Hereford                                10    On time
## 09:11  London Paddington                       9     On time
## 09:13  London Paddington                       14    On time
## 09:14  London Paddington                       12    On time
## 09:15  London Waterloo                         4     On time
## 09:16  London Paddington                       9     On time
## 09:19  Swansea                                 10    On time
## 09:24  Gatwick Airport                         5     On time
## 09:24  Oxford                                  10    On time
## 09:25  London Paddington                       9     On time
## 09:27  London Paddington                       7     On time
## 09:28  London Paddington                       14    On time
## 09:30  Penzance                                11    On time
## 09:32  London Paddington                       7B    On time
## 09:32  Worcester Shrub Hill                    10    On time
## 09:37  Didcot Parkway                          15    On time
## 09:39  Taunton                                 10    On time
## 09:40  London Waterloo                         6     On time
## 09:40  Nottingham                              7     On time
## 09:43  London Paddington                       14    On time
## 09:44  London Paddington                       12    On time
## 09:45  Swansea                                 10    On time
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       9     On time
## 09:46  Shalford                                5     On time
## 09:52  London Paddington                       8     On time
## 09:53  Banbury                                 13    On time
## 09:54  Gatwick Airport                         4     On time
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    10    On time
## 09:56  London Paddington                       9     On time
## 10:00  London Paddington                       8     On time
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-25 08:04:12
## Time   To                                      Plat  Expected
## 08:03  Ealing Broadway                         14    On time
## 08:03  Newbury                                 1     On time
## 08:10  London Paddington                       11    08:22
## 08:12  London Waterloo                         6     On time
## 08:13  Swansea                                 9     On time
## 08:14  London Paddington                       10A   Delayed
## 08:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       11    On time
## 08:17  London Paddington                       15    On time
## 08:19  Great Malvern                           9B    On time
## 08:20  London Paddington                       10    On time
## 08:20  Redhill                                 5     On time
## 08:22  Ealing Broadway                         14    On time
## 08:23  Basingstoke                             2     On time
## 08:26  Didcot Parkway                          13B   On time
## 08:27  Bristol Temple Meads                    9     On time
## 08:29  London Paddington                       10A   On time
## 08:29  Penzance                                7     On time
## 08:31  London Paddington                       15    On time
## 08:33  Ealing Broadway                         14    On time
## 08:38  Newbury                                 7     On time
## 08:41  London Paddington                       11    On time
## 08:42  London Waterloo                         4     On time
## 08:46  Oxford                                  9     On time
## 08:48  London Paddington                       15    On time
## 08:52  Bournemouth                             7B    On time
## 08:52  Ealing Broadway                         14    On time
## 08:53  Cheltenham Spa                          9B    On time
## 08:53  Didcot Parkway                          12    On time
## 08:56  London Paddington                       11    09:04
## 08:57  Bristol Temple Meads                    8     On time
## 08:59  Basingstoke                             2     On time
## 09:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 09:03  Ealing Broadway                         14    On time
## 09:06  London Paddington                       10A   On time
## 09:08  Ealing Broadway                         15    On time
## 09:11  London Paddington                       11    On time
## 09:12  London Waterloo                         6     On time
## 09:13  London Paddington                       10    On time
## 09:13  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:18  Great Malvern                           9     On time
## 09:20  London Paddington                       10    On time
## 09:20  Redhill                                 5     On time
## 09:22  Ealing Broadway                         14    On time
## 09:23  Didcot Parkway                          12    On time
## 09:26  London Paddington                       10    On time
## 09:27  Bristol Temple Meads                    9     On time
## 09:29  Plymouth                                7     On time
## 09:32  Basingstoke                             1     On time
## 09:32  London Paddington                       11    On time
## 09:35  London Paddington                       10    On time
## 09:36  Bedwyn                                  7B    On time
## 09:42  London Paddington                       10    On time
## 09:42  London Waterloo                         4     On time
## 09:45  Ealing Broadway                         15    On time
## 09:47  London Paddington                       10    On time
## 09:48  Oxford                                  9     On time
## 09:52  Ealing Broadway                         14    On time
## 09:54  Cheltenham Spa                          8     On time
## 09:55  Didcot Parkway                          12    On time
## 09:57  London Paddington                       10    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:02  Paignton                                8     On time
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
