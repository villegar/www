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

## Example (Last rendered on 2021-05-10 14:15)

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
## Reading (RDG) Station Board on 2021-05-10 14:15:12
## Time   From                                    Plat  Expected
## 14:45  Newport (South Wales)                   10    15:28
## 15:06  Bournemouth                             8B    On time
## 15:14  London Paddington                       14    15:16
## 15:16  London Paddington                       -     Cancelled
## 15:22  Bedwyn                                  -     Cancelled
## 15:26  Basingstoke                             2     On time
## 15:30  Cheltenham Spa                          -     Cancelled
## 15:31  London Paddington                       -     Cancelled
## 15:33  Redhill                                 5     On time
## 15:36  Newbury                                 1     On time
## 15:39  Bristol Temple Meads                    -     Cancelled
## 15:39  Manchester Piccadilly                   7     On time
## 15:40  London Waterloo                         6     On time
## 15:43  London Paddington                       14    On time
## 15:44  Didcot Parkway                          -     On time
## 15:44  Newport (South Wales)                   10    15:46
## 15:47  Exeter St Davids                        -     Cancelled
## 15:51  Gatwick Airport                         4     On time
## 15:51  London Paddington                       -     Cancelled
## 15:53  Basingstoke                             2     On time
## 15:54  Hereford                                -     Cancelled
## 15:55  London Paddington                       -     Cancelled
## 15:57  Plymouth                                -     Cancelled
## 15:58  London Paddington                       -     On time
## 16:02  Didcot Parkway                          15    On time
## 16:09  Bristol Temple Meads                    -     Cancelled
## 16:10  London Waterloo                         4     On time
## 16:13  London Paddington                       14    On time
## 16:18  Basingstoke                             2     On time
## 16:19  Redhill                                 7B    On time
## 16:22  Bedwyn                                  -     Cancelled
## 16:22  London Paddington                       12    On time
## 16:27  London Paddington                       -     Cancelled
## 16:29  Cheltenham Spa                          -     Cancelled
## 16:31  London Paddington                       -     Cancelled
## 16:33  Newbury                                 1     On time
## 16:33  Redhill                                 5     On time
## 16:39  Bristol Temple Meads                    -     Cancelled
## 16:40  London Waterloo                         6     On time
## 16:41  London Paddington                       9     On time
## 16:43  London Paddington                       14    On time
## 16:43  Manchester Piccadilly                   7B    On time
## 16:43  Paignton                                -     Cancelled
## 16:44  Didcot Parkway                          -     On time
## 16:45  Swansea                                 -     Cancelled
## 16:50  Basingstoke                             3     On time
## 16:55  London Paddington                       -     Cancelled
## 16:56  London Waterloo                         6     On time
## 16:58  London Paddington                       14    On time
## 16:58  London Paddington                       -     On time
## 16:58  Worcester Foregate Street               -     Cancelled
## 16:59  Penzance                                -     Cancelled
## 17:00  Gatwick Airport                         5     On time
## 17:00  London Paddington                       -     Cancelled
## 17:01  Didcot Parkway                          15    On time
## 17:09  Bristol Temple Meads                    -     Cancelled
## 17:09  London Paddington                       10    On time
## 17:10  London Waterloo                         4     On time
## 17:13  London Paddington                       14    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-10 14:15:14
## Time   To                                      Plat  Expected
## 15:01  Gatwick Airport                         15A   15:15
##        via Guildford                           
## 15:05  Basingstoke                             15B   Delayed
## 15:12  London Waterloo                         6     On time
## 15:13  Newport (South Wales)                   9B    15:33
## 15:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 15:18  Redhill                                 5     On time
## 15:18  Worcester Foregate Street               -     Cancelled
## 15:22  Ealing Broadway                         13    On time
## 15:23  Didcot Parkway                          14    On time
## 15:24  London Paddington                       -     Cancelled
## 15:32  Basingstoke                             2     On time
## 15:34  London Paddington                       -     Cancelled
## 15:37  Bedwyn                                  -     Cancelled
## 15:39  Ealing Broadway                         15    On time
## 15:42  London Waterloo                         4     On time
## 15:43  London Paddington                       -     Cancelled
## 15:44  London Paddington                       -     On time
## 15:50  London Paddington                       -     Cancelled
## 15:52  Ealing Broadway                         14    On time
## 15:53  Cheltenham Spa                          -     Cancelled
## 15:57  London Paddington                       -     Cancelled
## 15:58  Bristol Temple Meads                    -     Cancelled
## 15:58  Didcot Parkway                          -     On time
## 16:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:04  London Paddington                       -     Cancelled
## 16:07  Basingstoke                             2     On time
## 16:12  London Paddington                       -     Cancelled
## 16:12  London Waterloo                         6     On time
## 16:12  Newbury                                 1     On time
## 16:13  Newport (South Wales)                   9     On time
## 16:15  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 5     On time
## 16:22  Ealing Broadway                         14    On time
## 16:24  London Paddington                       -     Cancelled
## 16:25  Didcot Parkway                          12    On time
## 16:27  London Paddington                       -     Cancelled
## 16:29  Penzance                                -     Cancelled
## 16:33  Basingstoke                             7B    On time
## 16:33  Ealing Broadway                         13    On time
## 16:34  London Paddington                       -     Cancelled
## 16:37  Bedwyn                                  -     Cancelled
## 16:38  Ealing Broadway                         14    On time
## 16:41  London Paddington                       -     Cancelled
## 16:42  London Waterloo                         4     On time
## 16:43  Bristol Parkway                         9     On time
## 16:44  London Paddington                       -     On time
## 16:45  Bedwyn                                  3     On time
## 16:45  London Paddington                       -     Cancelled
## 16:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:52  Bournemouth                             7B    On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  London Waterloo                         6     On time
## 16:57  Basingstoke                             2     On time
## 16:58  Didcot Parkway                          -     On time
## 16:58  Taunton                                 -     Cancelled
## 17:00  London Paddington                       -     Cancelled
## 17:03  Ealing Broadway                         14    On time
## 17:03  Plymouth                                -     Cancelled
## 17:05  London Paddington                       -     Cancelled
## 17:06  Ealing Broadway                         15    On time
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       -     Cancelled
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 -     Cancelled
```
