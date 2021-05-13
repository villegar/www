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

## Example (Last rendered on 2021-05-13 06:11)

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
## Reading (RDG) Station Board on 2021-05-13 06:11:49
## Time   From                                    Plat  Expected
## 07:13  Didcot Parkway                          15A   07:15
## 07:13  London Paddington                       14    07:08
## 07:15  London Paddington                       12B   On time
## 07:16  London Paddington                       -     Cancelled
## 07:18  Swansea                                 -     Cancelled
## 07:20  Newbury                                 10A   On time
## 07:25  London Paddington                       -     Cancelled
## 07:27  Cheltenham Spa                          -     Cancelled
## 07:28  Basingstoke                             2     On time
## 07:28  London Paddington                       14    On time
## 07:31  Frome                                   -     Cancelled
## 07:33  Oxford                                  -     Cancelled
## 07:38  Bristol Temple Meads                    -     Cancelled
## 07:43  Birmingham New Street                   7     On time
## 07:43  Didcot Parkway                          -     Cancelled
## 07:43  London Paddington                       14    On time
## 07:44  London Paddington                       12    On time
## 07:45  London Waterloo                         6     On time
## 07:45  Swindon                                 15    On time
## 07:47  Basingstoke                             2     On time
## 07:49  Bristol Parkway                         10    On time
## 07:51  London Paddington                       -     Cancelled
## 07:51  Newbury                                 1     On time
## 07:53  Hereford                                -     Cancelled
## 07:53  London Paddington                       9     On time
## 07:55  Shalford                                -     Cancelled
## 07:56  London Paddington                       -     Cancelled
## 07:58  London Paddington                       14    On time
## 07:59  Didcot Parkway                          -     Cancelled
## 08:01  Swindon                                 15    On time
## 08:09  Bournemouth                             8     On time
## 08:10  London Waterloo                         4     On time
## 08:13  London Paddington                       14    On time
## 08:14  London Paddington                       13B   On time
## 08:14  Worcester Shrub Hill                    -     Cancelled
## 08:15  Didcot Parkway                          15    On time
## 08:16  Redhill                                 6     08:24
## 08:18  Swansea                                 -     Cancelled
## 08:19  Basingstoke                             2     On time
## 08:26  Cheltenham Spa                          -     Cancelled
## 08:27  London Paddington                       -     Cancelled
## 08:27  Newbury                                 3     On time
## 08:28  London Paddington                       14    On time
## 08:31  London Paddington                       -     Cancelled
## 08:34  Basingstoke                             1     On time
## 08:34  Gatwick Airport                         5     On time
## 08:39  Weston-super-Mare                       -     Cancelled
## 08:41  London Waterloo                         6     On time
## 08:42  Didcot Parkway                          15    On time
## 08:43  London Paddington                       14    On time
## 08:44  Manchester Piccadilly                   7     On time
## 08:49  Newport (South Wales)                   -     On time
## 08:50  London Paddington                       13    On time
## 08:51  London Paddington                       -     Cancelled
## 08:53  Bedwyn                                  12B   On time
## 08:53  Plymouth                                -     Cancelled
## 08:55  London Paddington                       -     Cancelled
## 08:58  London Paddington                       14    On time
## 09:00  London Paddington                       13    On time
## 09:01  Didcot Parkway                          15    On time
## 09:02  Basingstoke                             2     On time
## 09:03  London Paddington                       7     On time
## 09:04  Redhill                                 5     On time
## 09:04  Taunton                                 -     Cancelled
## 09:05  London Paddington                       -     On time
## 09:09  Bedwyn                                  11    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-13 06:11:52
## Time   To                                      Plat  Expected
## 07:10  Newbury                                 1     On time
## 07:12  London Waterloo                         6     On time
## 07:13  Newport (South Wales)                   9B    On time
## 07:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 07:16  London Paddington                       15A   On time
## 07:18  Great Malvern                           -     Cancelled
## 07:20  London Paddington                       -     Cancelled
## 07:22  Ealing Broadway                         14    On time
## 07:24  London Paddington                       10A   On time
## 07:24  London Waterloo                         4     On time
## 07:25  Didcot Parkway                          12B   On time
## 07:27  Bristol Temple Meads                    -     Cancelled
## 07:27  Shalford                                15A   On time
## 07:29  London Paddington                       -     Cancelled
## 07:30  London Paddington                       13A   On time
## 07:33  Ealing Broadway                         14    On time
## 07:34  Bedwyn                                  11A   On time
## 07:34  London Paddington                       -     Cancelled
## 07:37  Basingstoke                             2     On time
## 07:37  London Paddington                       -     Cancelled
## 07:41  London Paddington                       -     Cancelled
## 07:42  London Waterloo                         4     On time
## 07:45  London Paddington                       -     Cancelled
## 07:45  London Paddington                       15    On time
## 07:49  Gatwick Airport                         13A   On time
##        via Guildford                           
## 07:51  Didcot Parkway                          12    On time
## 07:52  Bournemouth                             7     On time
## 07:52  Ealing Broadway                         14    On time
## 07:53  Cheltenham Spa                          -     Cancelled
## 07:53  Swindon                                 9     On time
## 07:56  London Paddington                       -     Cancelled
## 08:00  Basingstoke                             2     On time
## 08:00  Bristol Temple Meads                    -     Cancelled
## 08:01  London Paddington                       -     Cancelled
## 08:01  London Paddington                       15    On time
## 08:03  Ealing Broadway                         14    On time
## 08:03  Newbury                                 1     On time
## 08:12  London Waterloo                         6     On time
## 08:13  Newport (South Wales)                   9     On time
## 08:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       -     Cancelled
## 08:17  London Paddington                       15    On time
## 08:19  Worcester Foregate Street               9     On time
## 08:20  London Paddington                       -     Cancelled
## 08:20  Redhill                                 6     On time
## 08:22  Ealing Broadway                         14    On time
## 08:24  Basingstoke                             2     On time
## 08:26  Didcot Parkway                          13B   On time
## 08:29  London Paddington                       -     Cancelled
## 08:29  Penzance                                -     Cancelled
## 08:31  London Paddington                       13A   On time
## 08:33  Ealing Broadway                         14    On time
## 08:36  Bedwyn                                  -     Cancelled
## 08:41  London Paddington                       -     Cancelled
## 08:42  London Waterloo                         4     On time
## 08:48  London Paddington                       15    On time
## 08:52  Bournemouth                             7     On time
## 08:52  Ealing Broadway                         14    On time
## 08:53  Cheltenham Spa                          -     Cancelled
## 08:54  Didcot Parkway                          13    On time
## 08:56  London Paddington                       -     Cancelled
## 08:57  Bristol Temple Meads                    -     Cancelled
## 08:59  Basingstoke                             1     On time
## 09:03  Ealing Broadway                         14    On time
## 09:05  London Paddington                       -     Cancelled
## 09:05  Swindon                                 -     On time
## 09:08  Ealing Broadway                         15    On time
```
