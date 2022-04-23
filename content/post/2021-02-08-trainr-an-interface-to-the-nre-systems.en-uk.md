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

## Example (Last rendered on 2022-04-23 16:04)

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
## Reading (RDG) Station Board on 2022-04-23 16:04:38
## Time   From                                    Plat  Expected
## 16:59  London Paddington                       -     Cancelled
## 16:59  Penzance                                10    17:01
## 17:01  Didcot Parkway                          15    17:03
## 17:05  Bournemouth                             13B   17:10
## 17:10  Bristol Temple Meads                    10    On time
## 17:11  London Paddington                       9     On time
## 17:12  London Waterloo                         4     On time
## 17:13  London Paddington                       14    On time
## 17:14  London Paddington                       12    On time
## 17:17  London Paddington                       9B    On time
## 17:20  Basingstoke                             2     17:23
## 17:23  Bedwyn                                  11A   On time
## 17:25  London Paddington                       9     On time
## 17:25  Oxford                                  10    On time
## 17:27  London Paddington                       7     17:31
## 17:31  Didcot Parkway                          15    On time
## 17:33  Cheltenham Spa                          11A   17:39
## 17:33  London Paddington                       7B    On time
## 17:33  Redhill                                 5     On time
## 17:40  Weston-super-Mare                       10    On time
## 17:41  London Paddington                       9     On time
## 17:41  Newbury                                 1     On time
## 17:42  London Waterloo                         6     On time
## 17:43  London Paddington                       14    On time
## 17:43  Paignton                                11    On time
## 17:44  London Paddington                       12    On time
## 17:47  London Paddington                       9     On time
## 17:47  Swansea                                 10    On time
## 17:51  Gatwick Airport                         4     On time
## 17:51  London Paddington                       8B    On time
## 17:54  Basingstoke                             2     On time
## 17:54  Hereford                                10    On time
## 17:55  London Paddington                       9     On time
## 18:00  Plymouth                                11    On time
## 18:01  Didcot Parkway                          14    On time
## 18:10  Bristol Temple Meads                    10A   On time
## 18:11  London Paddington                       9     On time
## 18:12  London Waterloo                         5     18:14
## 18:13  London Paddington                       13    On time
## 18:14  London Paddington                       12    On time
## 18:17  London Paddington                       9     On time
## 18:21  Basingstoke                             2     On time
## 18:24  Bedwyn                                  11A   On time
## 18:25  London Paddington                       9     On time
## 18:25  Oxford                                  10    On time
## 18:27  London Paddington                       7     On time
## 18:29  Bristol Parkway                         11    On time
## 18:31  Didcot Parkway                          15    On time
## 18:32  London Paddington                       7B    On time
## 18:33  Cheltenham Spa                          10    Delayed
## 18:33  Redhill                                 4     On time
## 18:40  Weston-super-Mare                       11    On time
## 18:41  London Paddington                       9     On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  London Waterloo                         6     On time
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       14    On time
## 18:44  London Paddington                       12    On time
## 18:46  Swansea                                 10    On time
## 18:47  London Paddington                       9     On time
## 18:50  Basingstoke                             2     On time
## 18:51  Gatwick Airport                         5     On time
## 18:51  London Paddington                       8     On time
## 18:54  Great Malvern                           10    On time
## 18:55  London Paddington                       9     On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-23 16:04:43
## Time   To                                      Plat  Expected
## 17:01  Paignton                                -     Cancelled
## 17:05  London Paddington                       10    On time
## 17:07  Basingstoke                             2     On time
## 17:12  London Paddington                       10    On time
## 17:12  London Waterloo                         6     On time
## 17:12  Newbury                                 1     On time
## 17:13  Swansea                                 9     On time
## 17:15  Ealing Broadway                         15    On time
## 17:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                9B    On time
## 17:20  Redhill                                 5     On time
## 17:22  Ealing Broadway                         14    On time
## 17:23  Didcot Parkway                          12    On time
## 17:24  London Paddington                       11A   On time
## 17:27  Bristol Temple Meads                    9     On time
## 17:27  London Paddington                       10    On time
## 17:30  Penzance                                7     17:32
## 17:35  Bedwyn                                  7B    On time
## 17:35  London Paddington                       11A   17:40
## 17:38  Basingstoke                             2     On time
## 17:42  London Paddington                       10    On time
## 17:42  London Waterloo                         4     On time
## 17:43  Carmarthen                              9     On time
## 17:45  Ealing Broadway                         15    On time
## 17:45  London Paddington                       11    On time
## 17:48  London Paddington                       10    On time
## 17:49  Oxford                                  9     On time
## 17:52  Ealing Broadway                         14    On time
## 17:53  Cheltenham Spa                          8B    On time
## 17:55  Didcot Parkway                          12    On time
## 17:56  London Paddington                       10    On time
## 17:57  Weston-super-Mare                       9     On time
## 18:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:05  London Paddington                       11    On time
## 18:08  Newbury                                 1     On time
## 18:12  Basingstoke                             2     On time
## 18:12  London Paddington                       10A   On time
## 18:12  London Waterloo                         6     On time
## 18:13  Ealing Broadway                         14    On time
## 18:13  Swansea                                 9     On time
## 18:19  Worcester Foregate Street               9     On time
## 18:22  Ealing Broadway                         13    On time
## 18:23  Didcot Parkway                          12    On time
## 18:24  London Paddington                       11A   On time
## 18:27  Bristol Temple Meads                    9     On time
## 18:27  London Paddington                       10    On time
## 18:29  Penzance                                7     On time
## 18:32  London Paddington                       11    On time
## 18:34  Bedwyn                                  7B    On time
## 18:35  London Paddington                       10    Delayed
## 18:36  Redhill                                 6     On time
## 18:37  Basingstoke                             2     On time
## 18:42  London Paddington                       11    On time
## 18:42  London Waterloo                         5     On time
## 18:43  Swansea                                 9     On time
## 18:45  Ealing Broadway                         15    On time
## 18:49  Oxford                                  9     On time
## 18:50  London Paddington                       10    On time
## 18:52  Bournemouth                             7     On time
## 18:52  Ealing Broadway                         14    On time
## 18:53  Cheltenham Spa                          8     On time
## 18:53  Didcot Parkway                          12    On time
## 18:56  London Paddington                       10    On time
## 18:57  Taunton                                 9     On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
