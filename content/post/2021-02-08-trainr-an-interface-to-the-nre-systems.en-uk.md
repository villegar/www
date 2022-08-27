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

## Example (Last rendered on 2022-08-27 18:04)

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
## Reading (RDG) Station Board on 2022-08-27 18:04:48
## Time   From                                    Plat  Expected
## 18:59  Penzance                                11    On time
## 19:01  Didcot Parkway                          15    On time
## 19:06  Bournemouth                             13B   19:10
## 19:10  Bristol Temple Meads                    10    19:14
## 19:11  London Paddington                       9     19:13
## 19:11  London Waterloo                         5     On time
## 19:14  London Paddington                       12    On time
## 19:17  London Paddington                       9     On time
## 19:22  Basingstoke                             2     On time
## 19:25  London Paddington                       9     On time
## 19:26  Oxford                                  10A   On time
## 19:27  London Paddington                       7     On time
## 19:27  Newbury                                 11    On time
## 19:31  Didcot Parkway                          15    On time
## 19:32  London Paddington                       7     On time
## 19:32  Redhill                                 6     On time
## 19:33  London Paddington                       14    On time
## 19:38  London Paddington                       9     On time
## 19:40  Manchester Piccadilly                   13    On time
## 19:40  Newbury                                 1     On time
## 19:40  Weston-super-Mare                       10    On time
## 19:41  London Waterloo                         4     19:57
## 19:43  London Paddington                       12    On time
## 19:47  Carmarthen                              10    19:49
## 19:47  London Paddington                       7     On time
## 19:49  London Paddington                       8     On time
## 19:51  Basingstoke                             2     On time
## 19:51  Gatwick Airport                         5     On time
## 19:51  London Paddington                       9     On time
## 19:54  Great Malvern                           10    On time
## 19:55  London Paddington                       8     Delayed
## 20:01  Didcot Parkway                          15    On time
## 20:02  Penzance                                11    On time
## 20:03  London Paddington                       14    On time
## 20:10  Bristol Temple Meads                    11    On time
## 20:11  London Paddington                       8     On time
## 20:11  London Waterloo                         6     On time
## 20:13  London Paddington                       12    On time
## 20:17  London Paddington                       9     On time
## 20:18  Newbury                                 11    On time
## 20:23  Basingstoke                             2     On time
## 20:25  London Paddington                       9     On time
## 20:25  Oxford                                  10    On time
## 20:27  London Paddington                       7     On time
## 20:31  Didcot Parkway                          15    On time
## 20:33  Cheltenham Spa                          11    On time
## 20:33  London Paddington                       14    On time
## 20:35  Redhill                                 5     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:40  Paignton                                -     Cancelled
## 20:41  London Waterloo                         4     On time
## 20:42  London Paddington                       8     On time
## 20:43  London Paddington                       12    On time
## 20:43  Newbury                                 13    On time
## 20:46  Swansea                                 10    On time
## 20:47  London Paddington                       9     On time
## 20:50  Basingstoke                             2     On time
## 20:54  Great Malvern                           10    On time
## 20:55  London Paddington                       9     On time
## 20:58  Gatwick Airport                         15    On time
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
## Reading (RDG) Station Board on 2022-08-27 18:04:52
## Time   To                                      Plat  Expected
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    On time
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       10    19:15
## 19:12  London Waterloo                         4     On time
## 19:13  Swansea                                 9     19:14
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Wilmslow                 
## 19:19  Hereford                                9     On time
## 19:20  Gatwick Airport                         6     On time
##        via Guildford                           
## 19:23  Didcot Parkway                          12    On time
## 19:24  Ealing Broadway                         14    On time
## 19:27  Bristol Temple Meads                    9     On time
## 19:28  London Paddington                       10A   On time
## 19:29  Plymouth                                7     On time
## 19:32  London Paddington                       11    On time
## 19:34  Newbury                                 7     On time
## 19:37  Basingstoke                             2     On time
## 19:41  Swansea                                 9     On time
## 19:42  London Paddington                       10    On time
## 19:42  London Waterloo                         5     On time
## 19:45  Ealing Broadway                         15    On time
## 19:48  London Paddington                       10    19:50
## 19:51  Oxford                                  8     On time
## 19:53  Cheltenham Spa                          9     On time
## 19:54  Ealing Broadway                         14    On time
## 19:55  Didcot Parkway                          12    On time
## 19:56  London Paddington                       10    On time
## 19:57  Taunton                                 8     Delayed
## 20:01  Redhill                                 6     On time
## 20:03  London Paddington                       11    On time
## 20:05  Basingstoke                             2     On time
## 20:10  Newbury                                 1     On time
## 20:12  London Paddington                       11    On time
## 20:12  London Waterloo                         4     On time
## 20:13  Swansea                                 8     On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 20:19  Great Malvern                           9     On time
## 20:20  Ealing Broadway                         15    On time
## 20:20  London Paddington                       11    On time
## 20:23  Didcot Parkway                          12    On time
## 20:24  Ealing Broadway                         14    On time
## 20:27  Bristol Temple Meads                    9     On time
## 20:27  London Paddington                       10    On time
## 20:29  Plymouth                                7     On time
## 20:32  Bedwyn                                  13B   On time
## 20:32  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:35  London Paddington                       11    On time
## 20:37  Basingstoke                             2     On time
## 20:42  London Paddington                       -     Cancelled
## 20:42  London Waterloo                         6     On time
## 20:44  Swindon                                 8     On time
## 20:45  Ealing Broadway                         15    On time
## 20:48  London Paddington                       10    On time
## 20:49  Oxford                                  9     On time
## 20:52  Bournemouth                             7     On time
## 20:53  Didcot Parkway                          12    On time
## 20:54  Ealing Broadway                         14    On time
## 20:56  London Paddington                       10    On time
## 20:57  Exeter St Davids                        9     On time
##        via Bristol                             
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
