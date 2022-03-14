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

## Example (Last rendered on 2022-03-14 18:06)

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
## Reading (RDG) Station Board on 2022-03-14 18:06:56
## Time   From                                    Plat  Expected
## 17:55  London Paddington                       8     18:12
## 17:57  Plymouth                                11    18:07
## 17:58  London Paddington                       9     18:15
## 18:01  London Paddington                       7     18:17
## 18:02  Gatwick Airport                         6     18:04
## 18:03  Didcot Parkway                          15    On time
## 18:08  Bournemouth                             12    On time
## 18:09  Bristol Temple Meads                    11    On time
## 18:11  London Paddington                       9     18:18
## 18:12  London Waterloo                         5     On time
## 18:13  London Paddington                       14    On time
## 18:20  Basingstoke                             2     On time
## 18:25  Newbury                                 11    On time
## 18:26  London Paddington                       8B    On time
## 18:26  Oxford                                  10A   On time
## 18:27  London Paddington                       7     On time
## 18:28  London Paddington                       13    18:32
## 18:29  Didcot Parkway                          15    On time
## 18:30  Cheltenham Spa                          11A   On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10A   On time
## 18:42  London Paddington                       9     On time
## 18:42  London Waterloo                         6     On time
## 18:43  London Paddington                       14    On time
## 18:43  Manchester Piccadilly                   8     On time
## 18:44  London Paddington                       -     Cancelled
## 18:45  Redhill                                 5     On time
## 18:47  Swansea                                 10    On time
## 18:50  Basingstoke                             3     On time
## 18:53  London Paddington                       13B   On time
## 18:57  Great Malvern                           10    On time
## 18:57  London Paddington                       9     On time
## 18:57  Penzance                                11A   18:59
## 18:58  London Paddington                       14    On time
## 18:59  London Paddington                       7     On time
## 19:04  Basingstoke                             2     On time
## 19:05  Didcot Parkway                          15    On time
## 19:05  Gatwick Airport                         4     On time
## 19:10  Weston-super-Mare                       10    On time
## 19:11  London Paddington                       9     On time
## 19:13  London Paddington                       14    On time
## 19:14  London Waterloo                         5     On time
## 19:15  London Paddington                       13    On time
## 19:15  Newbury                                 1     On time
## 19:22  Newbury                                 11    On time
## 19:25  Worcester Foregate Street               -     Cancelled
## 19:26  London Paddington                       8     On time
## 19:28  Didcot Parkway                          15    On time
## 19:28  London Paddington                       14    On time
## 19:29  London Paddington                       7     On time
## 19:30  London Paddington                       12    On time
## 19:33  Redhill                                 4     On time
## 19:34  Basingstoke                             2     On time
## 19:34  London Paddington                       7B    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:41  London Paddington                       9     On time
## 19:41  Manchester Piccadilly                   7     On time
## 19:43  London Paddington                       13    On time
## 19:43  London Waterloo                         6     On time
## 19:45  London Paddington                       12    On time
## 19:46  Swansea                                 10    On time
## 19:53  London Paddington                       8     On time
## 19:54  Worcester Foregate Street               10    On time
## 19:55  London Paddington                       12    On time
## 19:55  Plymouth                                11    On time
## 19:56  London Paddington                       9     On time
## 20:00  Basingstoke                             1     On time
## 20:03  Newbury                                 2     On time
## 20:04  Gatwick Airport                         4     On time
## 18:26  Heathrow Central Bus Stn                BUS   On time
## 19:01  Heathrow Central Bus Stn                BUS   On time
## 19:34  Heathrow Central Bus Stn                BUS   On time
## 20:05  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-14 18:07:00
## Time   To                                      Plat  Expected
## 17:57  Taunton                                 8     18:13
## 17:58  London Paddington                       11    18:08
## 18:00  Hereford                                9     18:16
## 18:03  Plymouth                                7     18:18
## 18:05  Ealing Broadway                         14    On time
## 18:07  Newbury                                 1     On time
## 18:08  Ealing Broadway                         15    On time
## 18:12  London Paddington                       11    On time
## 18:12  London Waterloo                         4     On time
## 18:13  Carmarthen                              9     18:19
## 18:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 18:20  Redhill                                 6     On time
## 18:22  Ealing Broadway                         14    On time
## 18:26  London Paddington                       11    On time
## 18:28  Bristol Temple Meads                    8B    On time
## 18:28  London Paddington                       10A   On time
## 18:29  Penzance                                7     On time
## 18:32  Basingstoke                             2     On time
## 18:32  Didcot Parkway                          12    On time
## 18:32  London Paddington                       11A   On time
## 18:33  Ealing Broadway                         13    18:35
## 18:40  Ealing Broadway                         15    On time
## 18:42  London Waterloo                         5     On time
## 18:43  London Paddington                       10A   On time
## 18:43  Swansea                                 9     On time
## 18:49  London Paddington                       10    On time
## 18:52  Ealing Broadway                         14    On time
## 18:57  Didcot Parkway                          13B   On time
## 18:58  London Paddington                       11A   19:00
## 18:59  Weston-super-Mare                       9     On time
## 19:00  London Paddington                       10    On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:01  Plymouth                                7     On time
## 19:04  Ealing Broadway                         14    On time
## 19:05  Basingstoke                             3     On time
## 19:10  Newbury                                 1     On time
## 19:12  London Waterloo                         6     On time
## 19:13  London Paddington                       10    On time
## 19:13  Swansea                                 9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:16  Ealing Broadway                         15    On time
## 19:20  Redhill                                 4     On time
## 19:22  Ealing Broadway                         14    On time
## 19:25  Basingstoke                             2     On time
## 19:25  London Paddington                       11    On time
## 19:27  Bristol Temple Meads                    8     On time
## 19:27  London Paddington                       -     Cancelled
## 19:30  Didcot Parkway                          12    On time
## 19:31  Plymouth                                7     On time
## 19:36  Bedwyn                                  7B    On time
## 19:38  Ealing Broadway                         15    On time
## 19:41  London Paddington                       10    On time
## 19:42  London Waterloo                         5     On time
## 19:42  Newbury                                 1     On time
## 19:43  Swansea                                 9     On time
## 19:49  Bournemouth                             7     On time
## 19:49  London Paddington                       10    On time
## 19:52  Ealing Broadway                         13    On time
## 19:55  London Paddington                       11    On time
## 19:55  Oxford                                  8     On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          12    On time
## 19:58  London Paddington                       10    On time
## 19:58  Weston-super-Mare                       9     On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:15  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
