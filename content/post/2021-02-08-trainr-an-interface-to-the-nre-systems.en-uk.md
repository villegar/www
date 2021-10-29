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

## Example (Last rendered on 2021-10-29 18:03)

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
## Reading (RDG) Station Board on 2021-10-29 18:03:35
## Time   From                                    Plat  Expected
## 18:57  Penzance                                10    19:04
## 19:00  London Paddington                       8     19:05
## 19:05  Gatwick Airport                         4     On time
## 19:10  Bristol Temple Meads                    10    On time
## 19:11  London Paddington                       9     On time
## 19:13  London Paddington                       14    On time
## 19:14  London Paddington                       13    On time
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         11    20:12
## 19:17  London Waterloo                         5     On time
## 19:22  Newbury                                 11A   On time
## 19:25  Worcester Foregate Street               10A   On time
## 19:26  London Paddington                       8     On time
## 19:28  Didcot Parkway                          15A   On time
## 19:28  London Paddington                       14    On time
## 19:30  London Paddington                       12    On time
## 19:31  Cheltenham Spa                          11A   19:33
## 19:33  Redhill                                 4     19:43
## 19:34  Basingstoke                             2     On time
## 19:34  London Paddington                       -     Cancelled
## 19:39  Bristol Temple Meads                    10A   On time
## 19:41  London Paddington                       9     On time
## 19:41  Manchester Piccadilly                   7     On time
## 19:43  London Paddington                       13    On time
## 19:44  London Paddington                       12    On time
## 19:45  London Waterloo                         6     On time
## 19:46  Swansea                                 10    Delayed
## 19:53  London Paddington                       8B    On time
## 19:54  Plymouth                                11    19:58
## 19:54  Worcester Foregate Street               10A   On time
## 19:55  London Paddington                       12    On time
## 19:57  Didcot Parkway                          15    On time
## 20:00  Basingstoke                             1     On time
## 20:01  London Paddington                       7     On time
## 20:03  Newbury                                 2     On time
## 20:04  Gatwick Airport                         4     20:09
## 20:06  Bournemouth                             8     On time
## 20:10  Bristol Temple Meads                    10    On time
## 20:11  London Paddington                       9     On time
## 20:14  London Paddington                       14    On time
## 20:15  London Waterloo                         6     On time
## 20:17  London Paddington                       9     On time
## 20:18  London Paddington                       12    On time
## 20:25  London Paddington                       9     On time
## 20:27  London Paddington                       8     On time
## 20:28  Banbury                                 11    On time
## 20:32  Cheltenham Spa                          10    On time
## 20:34  Basingstoke                             2     On time
## 20:34  Didcot Parkway                          13    On time
## 20:35  London Paddington                       8     On time
## 20:35  Redhill                                 14A   On time
## 20:43  London Paddington                       14    On time
## 20:43  Manchester Piccadilly                   7     On time
## 20:44  London Waterloo                         4     On time
## 20:44  Newbury                                 1     On time
## 20:44  Swansea                                 10    On time
## 20:47  London Paddington                       9     On time
## 20:48  Newbury                                 11    On time
## 20:51  London Paddington                       -     Cancelled
## 20:53  Gatwick Airport                         6     On time
## 20:53  Great Malvern                           11    On time
## 20:55  London Paddington                       9     On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-29 18:03:39
## Time   To                                      Plat  Expected
## 18:58  London Paddington                       10    19:05
## 19:02  Plymouth                                8     19:06
## 19:04  Ealing Broadway                         14    On time
## 19:06  Basingstoke                             3     On time
## 19:09  London Waterloo                         6     On time
## 19:10  Newbury                                 1     On time
## 19:13  London Paddington                       10    On time
## 19:13  Swansea                                 9     On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       11    20:13
## 19:20  Redhill                                 4     On time
## 19:22  Ealing Broadway                         14    On time
## 19:25  Basingstoke                             2     On time
## 19:25  London Paddington                       11A   On time
## 19:27  London Paddington                       10A   On time
## 19:27  Weston-super-Mare                       8     On time
## 19:30  Didcot Parkway                          12    On time
## 19:31  Penzance                                7B    Delayed
## 19:34  London Paddington                       11A   On time
## 19:35  Bedwyn                                  -     Cancelled
## 19:38  Ealing Broadway                         15A   On time
## 19:39  London Waterloo                         5     On time
## 19:41  London Paddington                       10A   On time
## 19:42  Newbury                                 1     On time
## 19:43  Swansea                                 -     Cancelled
## 19:49  Bournemouth                             7     On time
## 19:49  London Paddington                       10    Delayed
## 19:52  Ealing Broadway                         13    On time
## 19:55  London Paddington                       11    19:59
## 19:55  Oxford                                  8B    On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          12    On time
## 19:57  London Paddington                       10A   On time
## 19:58  Bristol Temple Meads                    9B    On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 20:04  Newbury                                 7     On time
## 20:09  London Waterloo                         6     On time
## 20:10  Newbury                                 2     On time
## 20:12  London Paddington                       10    On time
## 20:13  Swansea                                 9     On time
## 20:15  Ealing Broadway                         15    On time
## 20:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Hereford                                9     On time
## 20:20  Shalford                                4     On time
## 20:21  Basingstoke                             1     On time
## 20:22  Ealing Broadway                         14    On time
## 20:23  Didcot Parkway                          12    On time
## 20:27  Bristol Temple Meads                    9     On time
## 20:29  Plymouth                                8     On time
## 20:31  London Paddington                       11    On time
## 20:36  London Paddington                       10    On time
## 20:36  Newbury                                 8     On time
## 20:39  London Waterloo                         6     On time
## 20:42  London Paddington                       13    On time
## 20:47  London Paddington                       10    On time
## 20:49  London Paddington                       11    On time
## 20:49  Oxford                                  9     On time
## 20:52  Basingstoke                             2     On time
## 20:52  Ealing Broadway                         14    On time
## 20:53  Cheltenham Spa                          -     Cancelled
## 20:56  London Paddington                       11    On time
## 20:57  Weston-super-Mare                       9     On time
## 21:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
