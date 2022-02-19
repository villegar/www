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

## Example (Last rendered on 2022-02-19 06:03)

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
## Reading (RDG) Station Board on 2022-02-19 06:03:51
## Time   From                                    Plat  Expected
## 06:11  Didcot Parkway                          -     Cancelled
## 06:11  Staines                                 -     Cancelled
## 06:13  London Paddington                       14    On time
## 06:17  London Paddington                       -     Cancelled
## 06:17  Oxford                                  -     Cancelled
## 06:18  London Paddington                       -     Cancelled
## 06:34  Didcot Parkway                          -     Cancelled
## 06:41  Bristol Temple Meads                    -     Cancelled
## 06:41  London Waterloo                         -     Cancelled
## 06:43  London Paddington                       13    On time
## 06:46  Basingstoke                             -     Cancelled
## 06:46  London Paddington                       -     Cancelled
## 06:47  London Paddington                       -     Cancelled
## 06:48  Swansea                                 -     Cancelled
## 06:53  Bedwyn                                  -     Cancelled
## 06:55  Oxford                                  -     Cancelled
## 07:03  Didcot Parkway                          -     Cancelled
## 07:04  Redhill                                 -     Delayed
## 07:11  Bristol Temple Meads                    -     Cancelled
## 07:11  London Paddington                       -     Cancelled
## 07:11  London Waterloo                         -     Cancelled
## 07:13  London Paddington                       -     Cancelled
## 07:14  Bedwyn                                  -     Cancelled
## 07:17  London Paddington                       -     Cancelled
## 07:20  Basingstoke                             -     Cancelled
## 07:22  London Paddington                       -     Cancelled
## 07:25  London Paddington                       -     Cancelled
## 07:25  Oxford                                  -     Cancelled
## 07:32  Didcot Parkway                          -     Cancelled
## 07:32  London Paddington                       -     Cancelled
## 07:33  Swindon                                 -     Cancelled
## 07:38  Newbury                                 -     Cancelled
## 07:41  London Waterloo                         -     Cancelled
## 07:43  London Paddington                       14    On time
## 07:45  Swansea                                 -     Cancelled
## 07:46  London Paddington                       -     Cancelled
## 07:47  London Paddington                       -     Cancelled
## 07:51  Gatwick Airport                         -     Cancelled
## 07:51  London Paddington                       -     Cancelled
## 07:54  Great Malvern                           -     Cancelled
## 07:57  Basingstoke                             -     Cancelled
## 06:03  Heathrow Central Bus Stn                -     On time
## 07:11  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-19 06:03:55
## Time   To                                      Plat  Expected
## 06:00  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 06:07  Basingstoke                             -     Cancelled
## 06:12  London Waterloo                         -     Cancelled
## 06:12  Newbury                                 -     Cancelled
## 06:14  London Paddington                       -     Cancelled
## 06:19  Didcot Parkway                          -     Cancelled
## 06:19  Great Malvern                           -     Cancelled
## 06:19  Redhill                                 -     Cancelled
## 06:20  London Paddington                       -     Cancelled
## 06:22  Ealing Broadway                         14    On time
## 06:34  Bedwyn                                  -     Cancelled
## 06:36  London Paddington                       -     Cancelled
## 06:37  Basingstoke                             -     Cancelled
## 06:42  London Paddington                       -     Cancelled
## 06:42  London Waterloo                         -     Cancelled
## 06:49  Oxford                                  -     Cancelled
## 06:50  London Paddington                       -     Cancelled
## 06:52  Ealing Broadway                         13    On time
## 06:56  Didcot Parkway                          -     Cancelled
## 06:58  London Paddington                       -     Cancelled
## 07:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 07:07  Basingstoke                             -     Cancelled
## 07:12  London Paddington                       -     Cancelled
## 07:12  London Waterloo                         -     Cancelled
## 07:12  Newbury                                 -     Cancelled
## 07:13  Swansea                                 -     Cancelled
## 07:14  Ealing Broadway                         -     Cancelled
## 07:15  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 07:17  London Paddington                       -     Cancelled
## 07:20  Great Malvern                           -     Cancelled
## 07:20  Redhill                                 -     Cancelled
## 07:22  Ealing Broadway                         14    On time
## 07:26  Didcot Parkway                          -     Cancelled
## 07:26  London Paddington                       -     Cancelled
## 07:27  Bristol Temple Meads                    -     Cancelled
## 07:32  Basingstoke                             -     Cancelled
## 07:34  London Paddington                       -     Cancelled
## 07:35  Bedwyn                                  -     Cancelled
## 07:42  London Waterloo                         4     On time
## 07:45  Ealing Broadway                         -     Cancelled
## 07:47  London Paddington                       -     Cancelled
## 07:50  Oxford                                  -     Cancelled
## 07:52  Ealing Broadway                         14    On time
## 07:53  Cheltenham Spa                          -     Cancelled
## 07:53  Didcot Parkway                          -     Cancelled
## 07:56  London Paddington                       -     Cancelled
## 08:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 08:02  Newbury                                 -     Cancelled
## 07:00  Heathrow Central Bus Stn                BUS   On time
## 08:00  Heathrow Central Bus Stn                BUS   On time
```
