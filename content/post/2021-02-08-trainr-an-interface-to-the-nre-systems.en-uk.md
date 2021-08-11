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

## Example (Last rendered on 2021-08-11 20:03)

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
## Reading (RDG) Station Board on 2021-08-11 20:03:23
## Time   From                                    Plat  Expected
## 20:44  Swansea                                 -     21:00
## 20:59  London Paddington                       -     21:02
## 21:00  Par                                     -     21:08
## 21:03  Didcot Parkway                          -     21:00
## 21:04  Basingstoke                             -     21:01
## 21:07  Bournemouth                             -     On time
## 21:09  Bath Spa                                -     21:12
## 21:11  London Paddington                       -     On time
## 21:12  London Waterloo                         -     On time
## 21:15  London Paddington                       -     On time
## 21:16  London Paddington                       -     On time
## 21:21  Newbury                                 -     On time
## 21:22  London Paddington                       -     On time
## 21:23  London Paddington                       -     On time
## 21:24  Oxford                                  -     On time
## 21:28  Basingstoke                             -     On time
## 21:29  Didcot Parkway                          -     On time
## 21:29  Redhill                                 -     On time
## 21:31  London Paddington                       -     On time
## 21:33  Cheltenham Spa                          -     On time
## 21:33  London Paddington                       -     On time
## 21:38  Newbury                                 -     On time
## 21:41  London Waterloo                         -     On time
## 21:41  Manchester Piccadilly                   -     On time
## 21:44  London Paddington                       -     On time
## 21:44  Swansea                                 -     21:48
## 21:51  London Paddington                       -     On time
## 21:53  Great Malvern                           -     On time
## 21:56  Gatwick Airport                         -     On time
## 21:56  London Paddington                       -     On time
## 21:57  Basingstoke                             -     On time
## 22:00  Plymouth                                -     22:14
## 22:08  Bath Spa                                -     On time
## 22:13  London Paddington                       -     On time
## 22:14  Newbury                                 -     On time
## 22:15  London Paddington                       -     On time
## 22:15  London Paddington                       -     On time
## 22:20  Newbury                                 -     On time
## 22:25  Oxford                                  -     On time
## 22:27  London Paddington                       -     On time
## 22:29  London Paddington                       -     On time
## 22:30  Cheltenham Spa                          -     On time
## 22:34  Shalford                                -     On time
## 22:40  Basingstoke                             -     On time
## 22:41  London Waterloo                         -     On time
## 22:41  Manchester Piccadilly                   -     On time
## 22:43  London Paddington                       -     On time
## 22:44  Penzance                                -     On time
## 22:47  London Paddington                       -     On time
## 22:50  Salisbury                               -     On time
## 22:59  Worcester Foregate Street               -     On time
## 23:01  London Paddington                       -     On time
## 23:01  London Paddington                       -     On time
## 21:03  Heathrow Central Bus Stn                -     On time
## 22:03  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-11 20:03:27
## Time   To                                      Plat  Expected
## 20:50  London Paddington                       -     21:03
## 21:01  Bristol Parkway                         -     21:03
## 21:05  London Paddington                       -     21:09
## 21:10  Newbury                                 -     On time
## 21:12  London Waterloo                         -     On time
## 21:13  Birmingham New Street                   -     On time
##        via Coventry                            
## 21:15  London Paddington                       -     On time
## 21:16  Ealing Broadway                         -     On time
## 21:18  Swansea                                 -     On time
## 21:22  Basingstoke                             -     On time
## 21:22  Ealing Broadway                         -     On time
## 21:23  Didcot Parkway                          -     On time
## 21:25  Great Malvern                           -     On time
## 21:25  London Paddington                       -     On time
## 21:32  Bath Spa                                -     On time
## 21:34  Gatwick Airport                         -     On time
##        via Guildford                           
## 21:34  London Paddington                       -     On time
## 21:34  Plymouth                                -     On time
## 21:37  London Paddington                       -     On time
## 21:38  Ealing Broadway                         -     On time
## 21:42  London Waterloo                         -     On time
## 21:51  London Paddington                       -     On time
## 21:52  Bournemouth                             -     On time
## 21:52  Ealing Broadway                         -     On time
## 21:52  Oxford                                  -     On time
## 21:57  Cheltenham Spa                          -     On time
## 22:05  Basingstoke                             -     On time
## 22:05  London Paddington                       -     On time
## 22:10  London Paddington                       -     22:15
## 22:10  Newbury                                 -     On time
## 22:12  London Waterloo                         -     On time
## 22:14  London Paddington                       -     On time
## 22:16  Ealing Broadway                         -     On time
## 22:17  Swansea                                 -     On time
## 22:21  Worcester Shrub Hill                    -     On time
## 22:23  Ealing Broadway                         -     On time
## 22:29  Basingstoke                             -     On time
## 22:30  Didcot Parkway                          -     On time
## 22:31  Plymouth                                -     On time
## 22:35  London Paddington                       -     On time
## 22:41  London Paddington                       -     On time
## 22:45  London Paddington                       -     On time
## 22:48  Ealing Broadway                         -     On time
## 22:49  Southampton Central                     -     On time
## 22:52  Basingstoke                             -     On time
## 22:52  Ealing Broadway                         -     On time
## 22:55  Oxford                                  -     On time
## 23:01  London Paddington                       -     On time
## 23:02  Bath Spa                                -     On time
## 23:02  London Waterloo                         -     On time
## 22:00  Heathrow Central Bus Stn                -     On time
## 23:00  Heathrow Central Bus Stn                -     On time
```
