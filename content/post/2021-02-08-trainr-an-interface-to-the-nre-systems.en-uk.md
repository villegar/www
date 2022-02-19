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

## Example (Last rendered on 2022-02-19 08:03)

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
## Reading (RDG) Station Board on 2022-02-19 08:03:53
## Time   From                                    Plat  Expected
## 08:02  Didcot Parkway                          -     Cancelled
## 08:07  London Waterloo                         -     Cancelled
## 08:10  Weston-super-Mare                       -     Cancelled
## 08:11  London Paddington                       -     Cancelled
## 08:13  London Paddington                       14    On time
## 08:14  London Paddington                       -     Cancelled
## 08:16  Bedwyn                                  -     Cancelled
## 08:16  Swansea                                 -     Cancelled
## 08:17  London Paddington                       -     Cancelled
## 08:21  Basingstoke                             -     Cancelled
## 08:25  London Paddington                       -     Cancelled
## 08:25  Oxford                                  -     Cancelled
## 08:27  London Paddington                       -     Cancelled
## 08:30  Cheltenham Spa                          -     Cancelled
## 08:32  Didcot Parkway                          -     Cancelled
## 08:33  London Paddington                       -     Cancelled
## 08:33  Redhill                                 -     Cancelled
## 08:38  London Paddington                       -     Cancelled
## 08:39  Manchester Piccadilly                   13B   On time
## 08:41  London Waterloo                         -     Cancelled
## 08:42  Newbury                                 -     Cancelled
## 08:43  London Paddington                       14    On time
## 08:44  London Paddington                       -     Cancelled
## 08:46  Swansea                                 10    On time
## 08:47  London Paddington                       -     Cancelled
## 08:51  Basingstoke                             -     Cancelled
## 08:51  Gatwick Airport                         -     Cancelled
## 08:52  London Paddington                       -     Cancelled
## 08:54  Worcester Shrub Hill                    -     Cancelled
## 08:58  London Paddington                       -     Cancelled
## 09:01  Didcot Parkway                          -     Cancelled
## 09:03  Exeter St Davids                        -     Cancelled
## 09:07  London Waterloo                         4     Delayed
## 09:10  Taunton                                 -     Cancelled
## 09:11  London Paddington                       -     Cancelled
## 09:13  London Paddington                       14    On time
## 09:15  London Paddington                       -     Cancelled
## 09:16  Swansea                                 -     Cancelled
## 09:17  London Paddington                       -     Cancelled
## 09:20  Basingstoke                             -     Cancelled
## 09:23  Bedwyn                                  -     Cancelled
## 09:25  London Paddington                       -     Cancelled
## 09:25  Oxford                                  -     Cancelled
## 09:27  London Paddington                       -     Cancelled
## 09:31  Didcot Parkway                          -     Cancelled
## 09:33  London Paddington                       -     Cancelled
## 09:33  Redhill                                 -     Cancelled
## 09:34  Cheltenham Spa                          -     Cancelled
## 09:41  London Waterloo                         6     Delayed
## 09:41  Newbury                                 -     Cancelled
## 09:43  London Paddington                       14    On time
## 09:44  London Paddington                       -     Cancelled
## 09:46  Swansea                                 10    On time
## 09:47  London Paddington                       -     Cancelled
## 09:48  Basingstoke                             -     Cancelled
## 09:51  Gatwick Airport                         -     Cancelled
## 09:51  London Paddington                       -     Cancelled
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-19 08:03:55
## Time   To                                      Plat  Expected
## 08:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 08:02  Newbury                                 -     Cancelled
## 08:06  Redhill                                 -     Cancelled
## 08:07  Basingstoke                             -     Cancelled
## 08:12  London Paddington                       -     Cancelled
## 08:12  London Waterloo                         -     Cancelled
## 08:13  Swansea                                 -     Cancelled
## 08:15  Ealing Broadway                         -     Cancelled
## 08:18  London Paddington                       -     Cancelled
## 08:20  Great Malvern                           -     Cancelled
## 08:20  London Paddington                       -     Cancelled
## 08:22  Ealing Broadway                         14    On time
## 08:23  Didcot Parkway                          -     Cancelled
## 08:26  London Paddington                       -     Cancelled
## 08:27  Bristol Temple Meads                    -     Cancelled
## 08:30  Exeter St Davids                        -     Cancelled
## 08:35  Bedwyn                                  -     Cancelled
## 08:35  London Paddington                       -     Cancelled
## 08:38  Basingstoke                             -     Cancelled
## 08:40  Bristol Parkway                         -     Cancelled
## 08:42  London Waterloo                         4     On time
## 08:45  Ealing Broadway                         -     Cancelled
## 08:48  London Paddington                       10    On time
## 08:49  Oxford                                  -     Cancelled
## 08:52  Ealing Broadway                         14    On time
## 08:53  Didcot Parkway                          -     Cancelled
## 08:54  Cheltenham Spa                          -     Cancelled
## 08:57  London Paddington                       -     Cancelled
## 09:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 09:02  Exeter St Davids                        -     Cancelled
## 09:05  London Paddington                       -     Cancelled
## 09:06  Newbury                                 -     Cancelled
## 09:09  Basingstoke                             -     Cancelled
## 09:12  London Paddington                       -     Cancelled
## 09:12  London Waterloo                         -     Cancelled
## 09:13  Swansea                                 -     Cancelled
## 09:15  Ealing Broadway                         -     Cancelled
## 09:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 09:18  London Paddington                       -     Cancelled
## 09:20  Great Malvern                           -     Cancelled
## 09:20  Redhill                                 -     Cancelled
## 09:22  Ealing Broadway                         14    On time
## 09:24  Didcot Parkway                          -     Cancelled
## 09:25  London Paddington                       -     Cancelled
## 09:27  Bristol Temple Meads                    -     Cancelled
## 09:27  London Paddington                       -     Cancelled
## 09:30  Exeter St Davids                        -     Cancelled
## 09:35  Bedwyn                                  -     Cancelled
## 09:35  London Paddington                       -     Cancelled
## 09:38  Basingstoke                             -     Cancelled
## 09:42  London Waterloo                         4     On time
## 09:45  Ealing Broadway                         -     Cancelled
## 09:48  London Paddington                       10    On time
## 09:49  Oxford                                  -     Cancelled
## 09:52  Ealing Broadway                         14    On time
## 09:53  Cheltenham Spa                          -     Cancelled
## 09:53  Didcot Parkway                          -     Cancelled
## 10:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
