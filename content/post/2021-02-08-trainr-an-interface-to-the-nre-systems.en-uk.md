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

## Example (Last rendered on 2021-02-12 08:59)

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
## Reading (RDG) Station Board on 2021-02-12 08:59:38
## Time   From                                    Plat  Expected
## 08:44  Manchester Piccadilly                   11B   08:55
## 08:53  Plymouth                                -     Cancelled
## 09:00  London Paddington                       13    On time
## 09:01  Didcot Parkway                          15    On time
## 09:03  London Paddington                       7     On time
## 09:04  Reigate                                 5     09:12
## 09:04  Taunton                                 10    On time
## 09:05  Bournemouth                             8B    On time
## 09:09  Bedwyn                                  11    09:11
## 09:11  Hereford                                10    On time
## 09:11  London Paddington                       9     On time
## 09:13  London Paddington                       14    On time
## 09:14  London Paddington                       12    09:29
## 09:15  London Waterloo                         4     On time
## 09:16  London Paddington                       9     On time
## 09:20  Swansea                                 10    On time
## 09:27  Basingstoke                             2     On time
## 09:27  London Paddington                       7     On time
## 09:28  London Paddington                       14    On time
## 09:29  Reigate                                 15A   Delayed
## 09:30  Worcester Shrub Hill                    10    On time
## 09:31  London Paddington                       8     On time
## 09:34  Didcot Parkway                          15B   On time
## 09:39  Taunton                                 10    On time
## 09:40  London Waterloo                         6     On time
## 09:40  Nottingham                              7     On time
## 09:43  London Paddington                       13    On time
## 09:45  Swansea                                 10    On time
## 09:46  Shalford                                15    On time
## 09:51  London Paddington                       8     On time
## 09:54  Gatwick Airport                         -     Cancelled
## 09:55  London Paddington                       9     On time
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    10    On time
## 10:00  Penzance                                -     Cancelled
## 10:05  Didcot Parkway                          15    On time
## 10:06  Swansea                                 10    On time
## 10:10  London Waterloo                         5     On time
## 10:11  Bedwyn                                  11    On time
## 10:11  London Paddington                       9     On time
## 10:13  London Paddington                       14    On time
## 10:14  Bristol Temple Meads                    10    On time
## 10:14  London Paddington                       12    On time
## 10:17  London Paddington                       9     On time
## 10:19  Basingstoke                             2     On time
## 10:28  Cheltenham Spa                          10    On time
## 10:33  London Paddington                       8     On time
## 10:35  Newbury                                 1     On time
## 10:39  Bristol Temple Meads                    10    On time
## 10:39  Manchester Piccadilly                   7     On time
## 10:43  London Paddington                       14    On time
## 10:45  Carmarthen                              11    On time
## 10:45  London Waterloo                         6     On time
## 10:48  Reigate                                 15B   On time
## 10:52  London Paddington                       8     On time
## 10:54  Great Malvern                           10    On time
## 10:55  London Paddington                       9     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-12 08:59:40
## Time   To                                      Plat  Expected
## 08:52  Bournemouth                             11B   08:59
## 08:56  London Paddington                       -     Cancelled
## 08:59  Basingstoke                             1     On time
## 09:03  Ealing Broadway                         14    On time
## 09:06  London Paddington                       10    On time
## 09:08  Ealing Broadway                         15    On time
## 09:11  London Paddington                       11    09:12
## 09:12  London Waterloo                         6     On time
## 09:13  London Paddington                       10    On time
## 09:13  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:18  Great Malvern                           9     On time
## 09:20  Redhill                                 5     On time
## 09:21  London Paddington                       10    On time
## 09:22  Ealing Broadway                         14    On time
## 09:23  Didcot Parkway                          12    09:30
## 09:29  Plymouth                                7     On time
## 09:33  London Paddington                       10    On time
## 09:36  Bedwyn                                  8     On time
## 09:42  London Paddington                       10    On time
## 09:42  London Waterloo                         4     On time
## 09:48  London Paddington                       10    On time
## 09:52  Ealing Broadway                         13    On time
## 09:53  Cheltenham Spa                          8     On time
## 09:57  London Paddington                       10    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:04  London Paddington                       -     Cancelled
## 10:05  Basingstoke                             2     On time
## 10:08  London Paddington                       10    On time
## 10:12  London Paddington                       11    On time
## 10:12  London Waterloo                         6     On time
## 10:12  Newbury                                 1     On time
## 10:13  Swansea                                 9     On time
## 10:15  Ealing Broadway                         15    On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:16  London Paddington                       10    On time
## 10:19  Hereford                                9     On time
## 10:20  Redhill                                 4     On time
## 10:22  Ealing Broadway                         14    On time
## 10:23  Didcot Parkway                          12    On time
## 10:29  Penzance                                7     On time
## 10:34  London Paddington                       10    On time
## 10:40  Bedwyn                                  8     On time
## 10:42  London Paddington                       10    On time
## 10:42  London Waterloo                         5     On time
## 10:48  London Paddington                       11    On time
## 10:52  Bournemouth                             7     On time
## 10:52  Ealing Broadway                         14    On time
## 10:53  Cheltenham Spa                          8     On time
## 10:57  London Paddington                       10    On time
## 10:58  Bristol Temple Meads                    9     On time
```
