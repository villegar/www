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

## Example (Last rendered on 2022-02-18 20:04)

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
## Reading (RDG) Station Board on 2022-02-18 20:04:08
## Time   From                                    Plat  Expected
## 20:00  Basingstoke                             -     Cancelled
## 20:03  Newbury                                 -     Delayed
## 20:04  Gatwick Airport                         -     Cancelled
## 20:09  London Paddington                       -     Cancelled
## 20:10  Weston-super-Mare                       -     Cancelled
## 20:11  London Paddington                       -     Cancelled
## 20:14  London Paddington                       -     Cancelled
## 20:15  London Waterloo                         -     Cancelled
## 20:17  London Paddington                       -     Cancelled
## 20:25  London Paddington                       -     Cancelled
## 20:28  Banbury                                 -     Cancelled
## 20:32  Cheltenham Spa                          -     Cancelled
## 20:33  Bedwyn                                  -     Cancelled
## 20:34  Basingstoke                             -     Cancelled
## 20:34  Didcot Parkway                          -     Cancelled
## 20:35  Redhill                                 -     Cancelled
## 20:36  London Paddington                       -     Cancelled
## 20:43  London Paddington                       -     Cancelled
## 20:44  Newbury                                 -     On time
## 20:44  Swansea                                 -     Cancelled
## 20:47  London Paddington                       -     Cancelled
## 20:48  London Waterloo                         -     Cancelled
## 20:53  Gatwick Airport                         -     Cancelled
## 20:53  Great Malvern                           -     Cancelled
## 21:00  Penzance                                -     Cancelled
## 21:03  Didcot Parkway                          -     Cancelled
## 21:04  Basingstoke                             -     Cancelled
## 21:09  Bristol Temple Meads                    -     Cancelled
## 21:10  London Paddington                       -     Cancelled
## 21:10  London Waterloo                         -     Cancelled
## 21:11  London Paddington                       -     Cancelled
## 21:13  London Paddington                       -     Cancelled
## 21:16  London Paddington                       -     Cancelled
## 21:21  Bedwyn                                  -     Cancelled
## 21:24  Oxford                                  -     Cancelled
## 21:25  London Paddington                       -     Cancelled
## 21:27  London Paddington                       -     Cancelled
## 21:28  Basingstoke                             -     Cancelled
## 21:29  Didcot Parkway                          -     Cancelled
## 21:29  Redhill                                 -     Cancelled
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:38  Bedwyn                                  -     Cancelled
## 21:38  Newbury                                 -     Cancelled
## 21:40  London Waterloo                         -     Cancelled
## 21:41  Birmingham New Street                   -     Cancelled
## 21:43  London Paddington                       -     Cancelled
## 21:44  Swansea                                 -     Cancelled
## 21:46  London Paddington                       -     Cancelled
## 21:51  London Paddington                       -     Cancelled
## 21:53  Great Malvern                           -     Cancelled
## 21:56  Gatwick Airport                         -     Cancelled
## 21:57  Basingstoke                             -     Cancelled
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-18 20:04:12
## Time   To                                      Plat  Expected
## 20:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 20:10  Newbury                                 -     Cancelled
## 20:12  Bedwyn                                  -     Cancelled
## 20:12  London Paddington                       -     Cancelled
## 20:12  London Waterloo                         -     Cancelled
## 20:13  Swansea                                 -     Cancelled
## 20:19  Worcester Shrub Hill                    -     Cancelled
## 20:20  Shalford                                -     Cancelled
## 20:21  Basingstoke                             -     Cancelled
## 20:22  Ealing Broadway                         -     Cancelled
## 20:23  Didcot Parkway                          -     Cancelled
## 20:27  Bristol Temple Meads                    -     Cancelled
## 20:31  London Paddington                       -     Cancelled
## 20:36  London Paddington                       -     Cancelled
## 20:37  Newbury                                 -     Cancelled
## 20:42  London Waterloo                         -     Cancelled
## 20:47  London Paddington                       -     Cancelled
## 20:49  Oxford                                  -     Cancelled
## 20:51  Didcot Parkway                          -     Cancelled
## 20:52  Basingstoke                             -     Cancelled
## 20:52  Ealing Broadway                         -     Cancelled
## 20:56  London Paddington                       -     Cancelled
## 21:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 21:03  London Paddington                       -     Cancelled
## 21:08  Ealing Broadway                         -     Cancelled
## 21:10  Newbury                                 -     Cancelled
## 21:12  Bedwyn                                  -     Cancelled
## 21:12  London Waterloo                         -     Cancelled
## 21:13  Birmingham New Street                   -     Cancelled
##        via Coventry                            
## 21:13  London Paddington                       -     Cancelled
## 21:13  Swansea                                 -     Cancelled
## 21:18  Great Malvern                           -     Cancelled
## 21:22  Basingstoke                             -     Cancelled
## 21:22  Ealing Broadway                         -     Cancelled
## 21:23  Didcot Parkway                          -     Cancelled
## 21:23  London Paddington                       -     Cancelled
## 21:26  London Paddington                       -     Cancelled
## 21:27  Bristol Temple Meads                    -     Cancelled
## 21:29  Plymouth                                -     Cancelled
## 21:34  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 21:38  London Paddington                       -     Cancelled
## 21:42  London Waterloo                         -     Cancelled
## 21:46  London Paddington                       -     Cancelled
## 21:48  Oxford                                  -     Cancelled
## 21:49  Didcot Parkway                          -     Cancelled
## 21:52  Ealing Broadway                         -     Cancelled
## 21:53  Cheltenham Spa                          -     Cancelled
## 21:56  London Paddington                       -     Cancelled
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
