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

## Example (Last rendered on 2022-03-06 18:05)

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
## Reading (RDG) Station Board on 2022-03-06 18:05:25
## Time   From                                    Plat  Expected
## 18:01  London Paddington                       9     On time
## 18:08  Redhill                                 6     On time
## 18:08  St Austell                              10    18:21
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15B   On time
## 18:14  London Paddington                       14    On time
## 18:15  London Paddington                       12    On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7     On time
## 18:32  Ascot                                   4     On time
## 18:33  Cheltenham Spa                          -     Cancelled
## 18:33  London Paddington                       8B    On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   15    On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:44  London Paddington                       14    On time
## 18:46  Port Talbot Parkway                     11    On time
## 18:53  London Paddington                       9     On time
## 18:56  Bournemouth                             8     On time
## 18:56  Great Malvern                           10A   On time
## 18:58  Par                                     11    On time
## 18:59  London Paddington                       7     On time
## 19:01  London Paddington                       9     On time
## 19:04  Ascot                                   4     On time
## 19:09  Bristol Temple Meads                    10    On time
## 19:10  Redhill                                 15    On time
## 19:12  London Paddington                       9B    On time
## 19:14  Didcot Parkway                          14    On time
## 19:14  London Paddington                       13    On time
## 19:15  London Paddington                       12    On time
## 19:19  Bedwyn                                  1     On time
## 19:23  London Paddington                       9     On time
## 19:26  London Paddington                       8     On time
## 19:32  Ascot                                   6     On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  Manchester Piccadilly                   12    Delayed
## 19:40  Paignton                                11    On time
## 19:44  London Paddington                       14    On time
## 19:47  Port Talbot Parkway                     10    On time
## 19:53  London Paddington                       9     On time
## 19:55  Hereford                                10    On time
## 19:57  Exeter St Davids                        11    On time
## 20:02  Ascot                                   4     On time
## 18:20  Basingstoke                             BUS   On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 19:00  Winchester                              BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 19:20  Bramley (Hampshire)                     BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-06 18:05:29
## Time   To                                      Plat  Expected
## 18:09  Port Talbot Parkway                     9     On time
## 18:14  Ealing Broadway                         15B   On time
## 18:14  Great Malvern                           9B    On time
## 18:14  London Paddington                       10    18:22
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:24  Ascot                                   4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:29  St Austell                              7     On time
## 18:31  Ealing Broadway                         14    On time
## 18:38  Oxford                                  8B    On time
## 18:38  Redhill                                 6     On time
## 18:40  London Paddington                       -     Cancelled
## 18:44  Newbury                                 1     On time
## 18:45  London Paddington                       10    On time
## 18:46  Bournemouth                             15    On time
## 18:48  London Paddington                       11    On time
## 18:54  Ascot                                   4     On time
## 18:55  Weston-super-Mare                       9     On time
## 19:00  London Paddington                       11    On time
## 19:01  Ealing Broadway                         14    On time
## 19:01  Plymouth                                7     On time
## 19:02  Port Talbot Parkway                     9     On time
## 19:03  London Paddington                       10A   On time
## 19:13  London Paddington                       10    On time
## 19:14  Ealing Broadway                         14    On time
## 19:14  Hereford                                9B    On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:24  Ascot                                   4     On time
## 19:25  Bristol Temple Meads                    9     On time
## 19:25  Didcot Parkway                          12    On time
## 19:29  Plymouth                                8     On time
## 19:31  Ealing Broadway                         13    On time
## 19:42  London Paddington                       11    On time
## 19:44  Bedwyn                                  1     On time
## 19:48  London Paddington                       10    On time
## 19:54  Ascot                                   6     On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:58  London Paddington                       11    On time
## 20:01  Ealing Broadway                         14    On time
## 20:02  London Paddington                       10    On time
## 18:38  Basingstoke                             BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:52  Basingstoke                             BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
