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

## Example (Last rendered on 2021-05-13 20:11)

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
## Reading (RDG) Station Board on 2021-05-13 20:11:09
## Time   From                                    Plat  Expected
## 20:46  Swansea                                 -     Delayed
## 21:07  Bournemouth                             7     On time
## 21:10  London Waterloo                         4     On time
## 21:13  London Paddington                       14    21:09
## 21:13  London Paddington                       -     On time
## 21:14  London Paddington                       12    On time
## 21:14  Swindon                                 11    21:09
## 21:16  London Paddington                       -     Cancelled
## 21:21  Bedwyn                                  -     Cancelled
## 21:25  London Paddington                       -     Cancelled
## 21:27  London Paddington                       -     Cancelled
## 21:30  Redhill                                 15    On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:38  Newbury                                 2     On time
## 21:40  London Waterloo                         6     On time
## 21:41  Manchester Piccadilly                   7     On time
## 21:43  London Paddington                       13    On time
## 21:44  Newport (South Wales)                   -     On time
## 21:53  Great Malvern                           -     Cancelled
## 21:53  London Paddington                       -     On time
## 21:56  Basingstoke                             8B    On time
## 22:07  Didcot Parkway                          15    On time
## 22:08  Bristol Temple Meads                    -     Cancelled
## 22:10  London Waterloo                         4     On time
## 22:13  London Paddington                       14    On time
## 22:13  London Paddington                       9     On time
## 22:13  Newbury                                 1     On time
## 22:14  London Paddington                       13    On time
## 22:14  Swindon                                 -     On time
## 22:16  London Paddington                       -     Cancelled
## 22:20  Bedwyn                                  11    On time
## 22:24  London Paddington                       -     Cancelled
## 22:27  London Paddington                       -     On time
## 22:30  Cheltenham Spa                          -     Cancelled
## 22:33  Shalford                                14A   On time
## 22:40  London Waterloo                         6     On time
## 22:41  Manchester Piccadilly                   7B    On time
## 22:43  London Paddington                       14    On time
## 22:44  London Paddington                       12    On time
## 22:48  Oxford                                  15    On time
## 22:50  Salisbury                               8     On time
## 22:57  Worcester Shrub Hill                    -     On time
## 23:04  Basingstoke                             7     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-13 20:11:12
## Time   To                                      Plat  Expected
## 20:13  Newport (South Wales)                   8     Delayed
## 20:46  London Paddington                       -     Delayed
## 21:01  Gatwick Airport                         5     Delayed
##        via Guildford                           
## 21:10  Newbury                                 2     On time
## 21:12  London Waterloo                         6     On time
## 21:13  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:13  Newport (South Wales)                   -     On time
## 21:13  Newport (South Wales)                   -     On time
## 21:13  Newport (South Wales)                   9     On time
## 21:13  Swansea                                 -     On time
## 21:14  London Paddington                       11    On time
## 21:18  Great Malvern                           -     Cancelled
## 21:22  Ealing Broadway                         14    On time
## 21:23  Didcot Parkway                          12    On time
## 21:23  London Paddington                       -     Cancelled
## 21:27  Bristol Temple Meads                    -     Cancelled
## 21:29  Plymouth                                -     Cancelled
## 21:40  London Paddington                       -     Cancelled
## 21:42  London Waterloo                         4     On time
## 21:52  Bournemouth                             7     On time
## 21:52  Ealing Broadway                         13    On time
## 21:53  Swindon                                 -     On time
## 21:56  London Paddington                       -     Cancelled
## 21:59  Oxford                                  8B    On time
## 22:05  Basingstoke                             1     On time
## 22:10  London Paddington                       -     Cancelled
## 22:10  Newbury                                 2     On time
## 22:12  London Waterloo                         6     On time
## 22:13  Newport (South Wales)                   9     On time
## 22:13  Swansea                                 9     On time
## 22:14  London Paddington                       -     On time
## 22:15  Ealing Broadway                         15    On time
## 22:18  Worcester Shrub Hill                    -     Cancelled
## 22:22  Ealing Broadway                         14    On time
## 22:25  Exeter St Davids                        -     Cancelled
##        via Bristol                             
## 22:27  Swindon                                 -     On time
## 22:35  London Paddington                       -     Cancelled
## 22:46  Didcot Parkway                          12    On time
## 22:48  Ealing Broadway                         13    On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Ealing Broadway                         14    On time
```
