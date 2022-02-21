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

## Example (Last rendered on 2022-02-21 08:03)

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
## Reading (RDG) Station Board on 2022-02-21 08:03:52
## Time   From                                    Plat  Expected
## 06:59  Bristol Temple Meads                    11    08:09
## 07:49  Swansea                                 11A   08:22
## 07:56  London Paddington                       9     08:11
## 08:01  Newton Abbot                            11    08:43
## 08:06  Basingstoke                             2     On time
## 08:09  Bournemouth                             8     08:16
## 08:10  Didcot Parkway                          15    08:13
## 08:10  Oxford                                  -     Cancelled
## 08:11  London Paddington                       9B    08:18
## 08:11  London Waterloo                         -     Cancelled
## 08:13  London Paddington                       14    On time
## 08:14  Worcester Shrub Hill                    -     Cancelled
## 08:16  London Paddington                       -     Cancelled
## 08:16  Redhill                                 6     On time
## 08:18  Swansea                                 -     Cancelled
## 08:22  Newbury                                 -     Cancelled
## 08:24  Bedwyn                                  -     08:26
## 08:25  London Paddington                       -     Cancelled
## 08:26  Cheltenham Spa                          -     Cancelled
## 08:27  London Paddington                       7     Delayed
## 08:34  Gatwick Airport                         -     Cancelled
## 08:37  London Paddington                       -     Cancelled
## 08:39  Weston-super-Mare                       -     Cancelled
## 08:42  Basingstoke                             2     On time
## 08:42  London Waterloo                         -     Cancelled
## 08:43  London Paddington                       -     Cancelled
## 08:43  London Paddington                       14    On time
## 08:44  Didcot Parkway                          15    On time
## 08:46  Manchester Piccadilly                   7B    On time
## 08:51  London Paddington                       -     Cancelled
## 08:53  Plymouth                                -     Cancelled
## 08:55  London Paddington                       8     On time
## 09:01  Didcot Parkway                          15    On time
## 09:02  Basingstoke                             1     On time
## 09:04  Bristol Temple Meads                    10    On time
## 09:04  Redhill                                 5     On time
## 09:05  Bournemouth                             8     On time
## 09:09  Bedwyn                                  -     Cancelled
## 09:11  London Paddington                       9     On time
## 09:13  London Paddington                       14    On time
## 09:13  London Waterloo                         -     Cancelled
## 09:14  Hereford                                -     Cancelled
## 09:14  London Paddington                       12    On time
## 09:16  London Paddington                       -     Cancelled
## 09:19  Swansea                                 -     Cancelled
## 09:24  Bedwyn                                  -     On time
## 09:24  Gatwick Airport                         -     Cancelled
## 09:24  Oxford                                  -     Cancelled
## 09:25  London Paddington                       -     Cancelled
## 09:27  London Paddington                       7     On time
## 09:30  Penzance                                -     Cancelled
## 09:32  London Paddington                       -     Cancelled
## 09:32  Worcester Shrub Hill                    -     Cancelled
## 09:37  Didcot Parkway                          15    On time
## 09:39  Taunton                                 -     Cancelled
## 09:40  Birmingham New Street                   7     On time
## 09:41  London Waterloo                         -     Cancelled
## 09:43  London Paddington                       14    On time
## 09:45  Swansea                                 10    On time
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       -     Cancelled
## 09:46  Shalford                                5     On time
## 09:52  London Paddington                       -     Cancelled
## 09:53  Banbury                                 13    On time
## 09:54  Gatwick Airport                         -     Cancelled
## 09:55  Newbury                                 -     Cancelled
## 09:55  Worcester Shrub Hill                    -     Cancelled
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
## Reading (RDG) Station Board on 2022-02-21 08:03:57
## Time   To                                      Plat  Expected
## 07:02  London Paddington                       11    08:10
## 07:51  London Paddington                       11A   08:23
## 08:00  Basingstoke                             2     08:03
## 08:00  Bristol Temple Meads                    9     08:12
## 08:00  London Paddington                       -     Cancelled
## 08:03  Ealing Broadway                         -     Cancelled
## 08:03  Newbury                                 -     Cancelled
## 08:10  London Paddington                       11    08:44
## 08:11  London Waterloo                         6     On time
## 08:12  Bedwyn                                  3     On time
## 08:13  Swansea                                 9B    08:19
## 08:14  London Paddington                       -     Cancelled
## 08:15  Manchester Piccadilly                   8     08:17
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       -     Cancelled
## 08:19  Great Malvern                           -     Cancelled
## 08:20  London Paddington                       -     Cancelled
## 08:20  Redhill                                 5     On time
## 08:22  Ealing Broadway                         14    On time
## 08:23  Basingstoke                             2     On time
## 08:26  Didcot Parkway                          13B   On time
## 08:27  Bristol Temple Meads                    -     Cancelled
## 08:29  Exeter St Davids                        7     Delayed
## 08:29  London Paddington                       -     Cancelled
## 08:31  London Paddington                       -     Cancelled
## 08:33  Ealing Broadway                         -     Cancelled
## 08:38  Newbury                                 -     Cancelled
## 08:41  London Paddington                       -     Cancelled
## 08:42  London Waterloo                         -     Cancelled
## 08:46  Oxford                                  -     Cancelled
## 08:52  Bournemouth                             7B    On time
## 08:52  Ealing Broadway                         14    On time
## 08:53  Cheltenham Spa                          -     Cancelled
## 08:53  Didcot Parkway                          12    On time
## 08:56  London Paddington                       -     Cancelled
## 08:57  Bristol Temple Meads                    8     On time
## 08:59  Basingstoke                             2     On time
## 09:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 09:03  Ealing Broadway                         -     Cancelled
## 09:06  London Paddington                       10    On time
## 09:08  Ealing Broadway                         15    On time
## 09:11  London Paddington                       -     Cancelled
## 09:12  Bedwyn                                  -     On time
## 09:12  London Waterloo                         -     Cancelled
## 09:13  Manchester Piccadilly                   8     On time
##        via Stoke-on-Trent                      
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:16  London Paddington                       -     Cancelled
## 09:18  Great Malvern                           -     Cancelled
## 09:20  London Paddington                       -     Cancelled
## 09:20  Redhill                                 5     On time
## 09:22  Ealing Broadway                         14    On time
## 09:23  Didcot Parkway                          12    On time
## 09:26  London Paddington                       -     Cancelled
## 09:27  Bristol Temple Meads                    -     Cancelled
## 09:29  Exeter St Davids                        7     On time
## 09:32  Basingstoke                             1     On time
## 09:32  London Paddington                       -     Cancelled
## 09:35  London Paddington                       -     Cancelled
## 09:36  Bedwyn                                  -     Cancelled
## 09:42  London Paddington                       -     Cancelled
## 09:42  London Waterloo                         -     Cancelled
## 09:45  Ealing Broadway                         15    On time
## 09:47  London Paddington                       10    On time
## 09:48  Oxford                                  -     Cancelled
## 09:52  Ealing Broadway                         14    On time
## 09:54  Cheltenham Spa                          -     Cancelled
## 09:55  Didcot Parkway                          12    On time
## 09:57  London Paddington                       -     Cancelled
## 09:58  Bristol Temple Meads                    9     On time
## 10:02  Paignton                                8     On time
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
