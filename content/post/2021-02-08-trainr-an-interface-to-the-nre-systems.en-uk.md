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

## Example (Last rendered on 2022-02-19 20:03)

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
## Reading (RDG) Station Board on 2022-02-19 20:03:57
## Time   From                                    Plat  Expected
## 19:51  London Paddington                       8B    20:08
## 19:54  Great Malvern                           10    19:59
## 20:02  Exeter St Davids                        11    20:04
## 20:07  London Waterloo                         -     Cancelled
## 20:10  Bristol Temple Meads                    10    20:17
## 20:11  London Paddington                       8     On time
## 20:13  London Paddington                       14    On time
## 20:17  London Paddington                       9     Delayed
## 20:18  Bedwyn                                  11    20:33
## 20:23  Basingstoke                             2     On time
## 20:25  London Paddington                       9     On time
## 20:25  Oxford                                  -     Cancelled
## 20:27  London Paddington                       7     On time
## 20:31  Didcot Parkway                          15    On time
## 20:33  Cheltenham Spa                          11    On time
## 20:35  Redhill                                 -     Cancelled
## 20:38  London Paddington                       9     On time
## 20:41  London Waterloo                         -     Cancelled
## 20:42  Newbury                                 1     On time
## 20:43  London Paddington                       14    On time
## 20:46  Swansea                                 10    20:58
## 20:47  London Paddington                       -     Cancelled
## 20:50  Basingstoke                             2     On time
## 20:54  Great Malvern                           10    On time
## 20:55  Gatwick Airport                         -     Cancelled
## 20:55  London Paddington                       9     On time
## 21:01  Didcot Parkway                          15    On time
## 21:07  London Waterloo                         -     Cancelled
## 21:10  Bristol Temple Meads                    -     Cancelled
## 21:11  London Paddington                       9     On time
## 21:13  London Paddington                       14    On time
## 21:15  Exeter St Davids                        11    21:42
## 21:17  London Paddington                       -     Cancelled
## 21:22  Basingstoke                             2     On time
## 21:25  Oxford                                  -     Cancelled
## 21:26  Bedwyn                                  11    On time
## 21:31  Didcot Parkway                          13    On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:39  Manchester Piccadilly                   7B    On time
## 21:41  London Waterloo                         -     Cancelled
## 21:42  Newbury                                 1     On time
## 21:43  London Paddington                       14    On time
## 21:46  London Paddington                       13    On time
## 21:50  Basingstoke                             2     On time
## 21:50  Swansea                                 10    22:14
## 21:51  London Paddington                       -     Cancelled
## 21:52  Redhill                                 -     Cancelled
## 21:54  Worcester Foregate Street               11    On time
## 21:56  London Paddington                       9     On time
## 21:58  Gatwick Airport                         -     Cancelled
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-19 20:04:02
## Time   To                                      Plat  Expected
## 19:53  Cheltenham Spa                          8B    20:09
## 19:56  London Paddington                       10    20:04
## 20:01  Redhill                                 -     Cancelled
## 20:03  London Paddington                       11    20:05
## 20:05  Basingstoke                             2     On time
## 20:10  Newbury                                 -     Cancelled
## 20:12  London Paddington                       10    20:18
## 20:12  London Waterloo                         -     Cancelled
## 20:13  Swansea                                 8     On time
## 20:19  Great Malvern                           9     Delayed
## 20:22  Ealing Broadway                         14    On time
## 20:23  Didcot Parkway                          12    On time
## 20:27  Bristol Temple Meads                    9     On time
## 20:27  London Paddington                       -     Cancelled
## 20:29  Exeter St Davids                        7     On time
## 20:32  Bedwyn                                  13B   On time
## 20:32  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 20:35  London Paddington                       11    On time
## 20:37  Basingstoke                             2     On time
## 20:40  Swindon                                 9     On time
## 20:42  London Waterloo                         -     Cancelled
## 20:48  London Paddington                       10    20:59
## 20:49  Oxford                                  -     Cancelled
## 20:52  Ealing Broadway                         14    On time
## 20:53  Didcot Parkway                          12    On time
## 20:56  London Paddington                       10    On time
## 20:57  Exeter St Davids                        9     On time
##        via Bristol                             
## 21:05  Basingstoke                             2     On time
## 21:10  Newbury                                 1     On time
## 21:12  London Waterloo                         -     Cancelled
## 21:13  London Paddington                       -     Cancelled
## 21:13  Swansea                                 9     On time
## 21:16  London Paddington                       11    21:43
## 21:19  Oxford                                  -     Cancelled
## 21:22  Ealing Broadway                         14    On time
## 21:23  Didcot Parkway                          12    On time
## 21:26  London Paddington                       -     Cancelled
## 21:33  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       -     Cancelled
## 21:42  London Waterloo                         -     Cancelled
## 21:51  London Paddington                       10    22:16
## 21:52  Ealing Broadway                         14    On time
## 21:52  Southampton Central                     7B    On time
## 21:53  Oxford                                  -     Cancelled
## 21:56  London Paddington                       11    On time
## 21:57  Bristol Temple Meads                    9     On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
