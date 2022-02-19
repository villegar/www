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

## Example (Last rendered on 2022-02-19 10:04)

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
## Reading (RDG) Station Board on 2022-02-19 10:04:03
## Time   From                                    Plat  Expected
## 10:00  Exeter St Davids                        -     Cancelled
## 10:01  Didcot Parkway                          -     Cancelled
## 10:07  London Waterloo                         -     Cancelled
## 10:10  Exeter St Davids                        -     Cancelled
## 10:11  London Paddington                       -     Cancelled
## 10:13  London Paddington                       14    On time
## 10:14  Worcester Foregate Street               -     Cancelled
## 10:17  London Paddington                       -     Cancelled
## 10:17  Swansea                                 -     Cancelled
## 10:20  Basingstoke                             -     Cancelled
## 10:23  Bedwyn                                  -     Cancelled
## 10:25  Oxford                                  -     Cancelled
## 10:27  London Paddington                       -     Cancelled
## 10:31  Didcot Parkway                          -     Cancelled
## 10:33  London Paddington                       -     Cancelled
## 10:33  Redhill                                 -     Cancelled
## 10:41  Birmingham New Street                   13    On time
## 10:41  London Waterloo                         -     Cancelled
## 10:42  Newbury                                 -     Cancelled
## 10:43  London Paddington                       14    On time
## 10:46  Swansea                                 10    On time
## 10:47  London Paddington                       9     On time
## 10:50  Basingstoke                             2     On time
## 10:51  Gatwick Airport                         -     Cancelled
## 10:51  London Paddington                       8     On time
## 10:54  Great Malvern                           -     Cancelled
## 10:58  London Paddington                       7     On time
## 11:01  Didcot Parkway                          -     Cancelled
## 11:01  Exeter St Davids                        -     Cancelled
## 11:07  London Waterloo                         -     Cancelled
## 11:10  Bristol Temple Meads                    10    Delayed
## 11:11  London Paddington                       8     On time
## 11:13  London Paddington                       14    On time
## 11:14  London Paddington                       12    On time
## 11:17  London Paddington                       9     On time
## 11:21  Bedwyn                                  -     Cancelled
## 11:24  Oxford                                  10    On time
## 11:25  London Paddington                       9     On time
## 11:27  London Paddington                       7     On time
## 11:28  Basingstoke                             2     On time
## 11:28  Bristol Parkway                         -     Cancelled
## 11:31  Didcot Parkway                          15    On time
## 11:33  Cheltenham Spa                          -     Cancelled
## 11:33  London Paddington                       7B    On time
## 11:33  Redhill                                 -     Cancelled
## 11:41  London Waterloo                         -     Cancelled
## 11:41  Newbury                                 1     On time
## 11:43  Exeter St Davids                        -     Cancelled
## 11:43  London Paddington                       14    On time
## 11:44  London Paddington                       12    On time
## 11:46  Swansea                                 10    On time
## 11:47  London Paddington                       9     On time
## 11:51  Gatwick Airport                         -     Cancelled
## 11:51  London Paddington                       8     On time
## 11:54  Great Malvern                           -     Cancelled
## 11:55  London Paddington                       9     On time
## 11:56  Basingstoke                             2     On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-19 10:04:06
## Time   To                                      Plat  Expected
## 10:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 10:05  London Paddington                       -     Cancelled
## 10:07  Basingstoke                             -     Cancelled
## 10:12  London Paddington                       -     Cancelled
## 10:12  London Waterloo                         -     Cancelled
## 10:12  Newbury                                 -     Cancelled
## 10:13  Swansea                                 -     Cancelled
## 10:15  Ealing Broadway                         -     Cancelled
## 10:15  London Paddington                       -     Cancelled
## 10:18  London Paddington                       -     Cancelled
## 10:19  Hereford                                -     Cancelled
## 10:20  Redhill                                 -     Cancelled
## 10:22  London Paddington                       14    On time
## 10:23  Didcot Parkway                          12    On time
## 10:24  London Paddington                       -     Cancelled
## 10:27  Bristol Temple Meads                    9     On time
## 10:27  London Paddington                       -     Cancelled
## 10:30  Exeter St Davids                        -     Cancelled
## 10:35  Bedwyn                                  -     Cancelled
## 10:38  Basingstoke                             2     On time
## 10:42  London Waterloo                         -     Cancelled
## 10:45  Ealing Broadway                         -     Cancelled
## 10:48  London Paddington                       10    On time
## 10:49  Oxford                                  9     On time
## 10:52  Didcot Parkway                          12    On time
## 10:52  Ealing Broadway                         14    On time
## 10:53  Cheltenham Spa                          8     On time
## 10:56  London Paddington                       -     Cancelled
## 11:01  Exeter St Davids                        7     On time
## 11:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 11:05  Basingstoke                             2     On time
## 11:05  London Paddington                       -     Cancelled
## 11:10  Newbury                                 1     On time
## 11:12  London Paddington                       10    Delayed
## 11:12  London Waterloo                         -     Cancelled
## 11:13  Swansea                                 8     On time
## 11:15  Ealing Broadway                         -     Cancelled
## 11:19  Great Malvern                           9     On time
## 11:20  Redhill                                 5     On time
## 11:22  Ealing Broadway                         14    On time
## 11:23  Didcot Parkway                          12    On time
## 11:24  London Paddington                       -     Cancelled
## 11:27  Bristol Temple Meads                    9     On time
## 11:27  London Paddington                       10    On time
## 11:30  Exeter St Davids                        7     On time
## 11:32  London Paddington                       -     Cancelled
## 11:35  Bedwyn                                  7B    On time
## 11:35  London Paddington                       -     Cancelled
## 11:38  Basingstoke                             2     On time
## 11:42  London Waterloo                         -     Cancelled
## 11:45  London Paddington                       -     Cancelled
## 11:48  London Paddington                       10    On time
## 11:49  Oxford                                  9     On time
## 11:52  Ealing Broadway                         14    On time
## 11:53  Cheltenham Spa                          8     On time
## 11:54  Didcot Parkway                          12    On time
## 11:57  Bristol Temple Meads                    9     On time
## 11:57  London Paddington                       -     Cancelled
## 12:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
