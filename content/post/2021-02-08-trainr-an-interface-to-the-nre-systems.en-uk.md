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

## Example (Last rendered on 2024-04-24 05:06)

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
## Reading (RDG) Station Board on 2024-04-24 05:06:41.250347
## Time   From                                    Plat  Expected
## 05:55  Newbury                                 1     06:10
## 05:58  Bristol Temple Meads                    11A   06:06
## 06:06  Southampton Central                     8B    On time
## 06:11  London Paddington                       13    On time
## 06:12  Bedwyn                                  11A   On time
## 06:14  Staines                                 5     On time
## 06:16  London Paddington                       9B    06:18
## 06:18  Didcot Parkway                          15    On time
## 06:25  London Paddington                       9     On time
## 06:28  Oxford                                  11A   On time
## 06:31  Basingstoke                             -     Cancelled
## 06:31  Bristol Temple Meads                    10    On time
## 06:41  Bedwyn                                  11A   On time
## 06:42  London Paddington                       14    On time
## 06:46  Didcot Parkway                          15    On time
## 06:48  London Waterloo                         6     On time
## 06:48  Swansea                                 10    On time
## 06:51  Basingstoke                             1     On time
## 06:51  Gatwick Airport                         5     On time
## 06:51  London Paddington                       9     On time
## 06:53  Evesham                                 10    On time
## 06:54  London Paddington                       8B    On time
## 06:55  London Paddington                       13    On time
## 06:59  Bristol Temple Meads                    11    On time
## 07:00  London Paddington                       14    On time
## 07:01  Newbury                                 1     On time
## 07:04  Bristol Temple Meads                    11    On time
## 07:08  Southampton Central                     12B   On time
## 07:09  Oxford                                  10A   On time
## 07:10  London Paddington                       14    On time
## 07:11  London Paddington                       9     On time
## 07:11  London Waterloo                         4     On time
## 07:12  Didcot Parkway                          15    On time
## 07:13  London Paddington                       8B    On time
## 07:18  London Paddington                       12    On time
## 07:18  Swansea                                 10    On time
## 07:21  Newbury                                 11    On time
## 07:23  London Paddington                       9     On time
## 07:25  Abbey Wood                              13    On time
## 07:26  Cheltenham Spa                          10    On time
## 07:26  London Paddington                       7     On time
## 07:26  Oxford                                  8     On time
## 07:28  Basingstoke                             2     On time
## 07:31  Frome                                   11A   On time
## 07:33  Gatwick Airport                         5     On time
## 07:33  London Paddington                       7B    On time
## 07:38  Bristol Temple Meads                    11    On time
## 07:38  London Paddington                       9     On time
## 07:43  Didcot Parkway                          15    On time
## 07:44  Abbey Wood                              14    On time
## 07:44  London Paddington                       8B    On time
## 07:45  Birmingham New Street                   7B    On time
## 07:46  Basingstoke                             -     Cancelled
## 07:46  London Waterloo                         6     On time
## 07:47  London Paddington                       12B   On time
## 07:49  Swansea                                 10    On time
## 07:51  London Paddington                       9     On time
## 07:51  Newbury                                 1     On time
## 07:54  Evesham                                 11A   On time
## 07:54  London Paddington                       8B    On time
## 07:55  Abbey Wood                              13    On time
## 06:35  Heathrow Airport T3 (Bus)               BUS   On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
## 07:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-24 05:06:42.97025
## Time   To                                      Plat  Expected
## 06:00  London Paddington                       11A   06:07
## 06:09  London Waterloo                         6     On time
## 06:14  Abbey Wood                              14    On time
## 06:14  London Paddington                       11A   On time
## 06:14  Newbury                                 15B   On time
## 06:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 06:18  Evesham                                 9B    06:19
## 06:19  London Paddington                       15    On time
## 06:20  Basingstoke                             12B   On time
## 06:24  Abbey Wood                              13    On time
## 06:27  Gatwick Airport                         15A   On time
##        via Guildford                           
## 06:27  Penzance                                9     On time
##        via Bristol                             
## 06:34  London Paddington                       10    On time
## 06:36  London Paddington                       11A   On time
## 06:37  Newbury                                 1     On time
## 06:39  London Waterloo                         5     On time
## 06:40  Basingstoke                             -     Cancelled
## 06:42  London Paddington                       11A   On time
## 06:44  Abbey Wood                              13    On time
## 06:45  Newcastle                               7B    On time
##        via Doncaster                           
## 06:48  London Paddington                       15    On time
## 06:50  London Paddington                       10    On time
## 06:51  Redhill                                 13A   On time
## 06:53  Weston-super-Mare                       9     On time
## 06:54  Abbey Wood                              14    On time
## 06:56  Cheltenham Spa                          8B    On time
## 06:56  London Paddington                       10    On time
## 06:57  Basingstoke                             1     On time
## 07:01  Didcot Parkway                          14    On time
## 07:02  London Paddington                       11    On time
## 07:07  London Paddington                       11    On time
## 07:09  London Waterloo                         6     On time
## 07:10  Newbury                                 1     On time
## 07:12  London Paddington                       10A   On time
## 07:13  Carmarthen                              9     On time
## 07:14  Abbey Wood                              13    On time
## 07:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 07:18  Evesham                                 8B    On time
## 07:18  London Paddington                       15    On time
## 07:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:20  London Paddington                       10    On time
## 07:24  Abbey Wood                              14    On time
## 07:24  London Paddington                       11    On time
## 07:25  Bristol Temple Meads                    9     On time
## 07:26  Didcot Parkway                          12    On time
## 07:30  Paignton                                7     On time
## 07:31  London Paddington                       10    On time
## 07:34  London Paddington                       11A   On time
## 07:35  Newbury                                 7B    On time
## 07:38  Basingstoke                             2     On time
## 07:38  London Paddington                       8     On time
## 07:39  Cardiff Central                         9     On time
## 07:39  London Paddington                       14    On time
## 07:39  London Waterloo                         4     On time
## 07:41  London Paddington                       11    On time
## 07:45  Abbey Wood                              13    On time
## 07:49  Didcot Parkway                          12B   On time
## 07:49  London Paddington                       15    On time
## 07:49  Oxford                                  8B    On time
## 07:51  London Paddington                       10    On time
## 07:52  Bournemouth                             7B    On time
## 07:52  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:53  Bristol Temple Meads                    9     On time
## 07:54  Abbey Wood                              14    On time
## 07:56  Cheltenham Spa                          8B    On time
## 07:56  London Paddington                       11A   On time
## 08:00  Basingstoke                             2     On time
## 08:03  Newbury                                 1     On time
## 06:25  Heathrow Airport T3 (Bus)               BUS   On time
## 06:55  Heathrow Airport T3 (Bus)               BUS   On time
## 07:25  Heathrow Airport T3 (Bus)               BUS   On time
## 07:55  Heathrow Airport T3 (Bus)               BUS   On time
```
