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

## Example (Last rendered on 2022-09-24 06:08)

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
## Reading (RDG) Station Board on 2022-09-24 06:08:58
## Time   From                                    Plat  Expected
## 07:04  Didcot Parkway                          15    Delayed
## 07:04  Gatwick Airport                         5     07:21
## 07:05  Southampton Central                     13B   07:09
## 07:08  London Paddington                       14    07:10
## 07:11  Bristol Temple Meads                    10    On time
## 07:11  London Paddington                       8     On time
## 07:11  London Waterloo                         4     On time
## 07:19  London Paddington                       8B    On time
## 07:20  Basingstoke                             2     On time
## 07:22  London Paddington                       12B   On time
## 07:23  Newbury                                 11    On time
## 07:25  London Paddington                       9     On time
## 07:32  Didcot Parkway                          15    On time
## 07:33  London Paddington                       7A    On time
## 07:33  London Paddington                       14    On time
## 07:33  Swindon                                 10    On time
## 07:38  Newbury                                 1     On time
## 07:40  Bristol Temple Meads                    10    On time
## 07:41  London Waterloo                         5     On time
## 07:42  Didcot Parkway                          13    On time
## 07:45  Swansea                                 10    On time
## 07:46  London Paddington                       12    On time
## 07:51  Gatwick Airport                         4     On time
## 07:51  London Paddington                       8B    On time
## 07:55  Didcot Parkway                          10A   On time
## 07:55  London Paddington                       9     On time
## 07:57  Basingstoke                             2     On time
## 08:00  Salisbury                               3     On time
## 08:02  Didcot Parkway                          15    On time
## 08:03  London Paddington                       14    On time
## 08:10  Weston-super-Mare                       11    On time
## 08:11  London Paddington                       9     On time
## 08:11  London Waterloo                         4     On time
## 08:16  London Paddington                       12    On time
## 08:16  Swansea                                 10    On time
## 08:19  London Paddington                       8B    On time
## 08:21  Basingstoke                             2     On time
## 08:25  London Paddington                       9     On time
## 08:27  London Paddington                       7     On time
## 08:30  Cheltenham Spa                          10A   On time
## 08:30  Newbury                                 11    On time
## 08:32  Didcot Parkway                          15    On time
## 08:32  London Paddington                       8     On time
## 08:33  London Paddington                       14    On time
## 08:33  Redhill                                 5     On time
## 08:38  London Paddington                       9     On time
## 08:39  Didcot Parkway                          8     On time
## 08:41  Bristol Temple Meads                    11    On time
## 08:41  London Waterloo                         6     On time
## 08:42  Newbury                                 1     On time
## 08:46  London Paddington                       12    On time
## 08:46  Swansea                                 10    On time
## 08:51  Basingstoke                             2     On time
## 08:51  Gatwick Airport                         4     On time
## 08:52  London Paddington                       9B    On time
## 08:55  Didcot Parkway                          10    On time
## 08:55  London Paddington                       8     On time
## 08:57  Honiton                                 3     On time
## 08:58  London Paddington                       7B    On time
## 09:03  London Paddington                       14    On time
## 09:03  Plymouth                                11    On time
## 07:33  Heathrow Central Bus Stn                BUS   On time
## 08:35  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-24 06:09:02
## Time   To                                      Plat  Expected
## 07:07  Basingstoke                             2     On time
## 07:12  London Paddington                       10    On time
## 07:12  London Waterloo                         6     On time
## 07:12  Newbury                                 7B    On time
## 07:13  Swansea                                 8     On time
## 07:15  Didcot Parkway                          13B   On time
## 07:15  Ealing Broadway                         15    Delayed
## 07:20  Didcot Parkway                          8B    On time
## 07:20  Redhill                                 5     07:24
## 07:24  Ealing Broadway                         14    On time
## 07:24  London Paddington                       11    On time
## 07:26  Didcot Parkway                          12B   On time
## 07:27  Bristol Temple Meads                    9     On time
## 07:32  Basingstoke                             2     On time
## 07:34  London Paddington                       10    On time
## 07:35  Newbury                                 7A    On time
## 07:42  London Paddington                       10    On time
## 07:42  London Waterloo                         4     On time
## 07:45  Ealing Broadway                         15    On time
## 07:47  London Paddington                       10    On time
## 07:53  Cheltenham Spa                          8B    On time
## 07:53  Didcot Parkway                          12    On time
## 07:54  Ealing Broadway                         14    On time
## 07:57  Bristol Temple Meads                    9     On time
## 07:58  London Paddington                       10A   On time
## 08:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 08:02  Newbury                                 1     On time
## 08:05  Basingstoke                             2     On time
## 08:12  London Waterloo                         5     On time
## 08:13  Swansea                                 9     On time
## 08:14  London Paddington                       11    On time
## 08:15  Didcot Parkway                          13    On time
## 08:15  Ealing Broadway                         15    On time
## 08:15  Salisbury                               3     On time
## 08:18  London Paddington                       10    On time
## 08:20  Didcot Parkway                          8B    On time
## 08:20  Redhill                                 6     On time
## 08:23  Didcot Parkway                          12    On time
## 08:24  Ealing Broadway                         14    On time
## 08:27  Bristol Temple Meads                    9     On time
## 08:29  Penzance                                7     On time
## 08:31  London Paddington                       11    On time
## 08:33  Newbury                                 8     On time
## 08:35  London Paddington                       10A   On time
## 08:38  Basingstoke                             2     On time
## 08:40  Bristol Parkway                         9     On time
## 08:42  London Waterloo                         4     On time
## 08:43  London Paddington                       11    On time
## 08:45  Ealing Broadway                         15    On time
## 08:48  London Paddington                       10    On time
## 08:52  Bournemouth                             8     On time
## 08:52  Didcot Parkway                          12    On time
## 08:54  Cheltenham Spa                          9B    On time
## 08:54  Ealing Broadway                         14    On time
## 08:58  London Paddington                       10    On time
## 08:59  Taunton                                 8     On time
## 09:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:02  Exeter St Davids                        7B    On time
## 09:05  Basingstoke                             2     On time
## 09:05  London Paddington                       11    On time
## 08:00  Heathrow Central Bus Stn                BUS   On time
## 09:00  Heathrow Central Bus Stn                BUS   On time
```
