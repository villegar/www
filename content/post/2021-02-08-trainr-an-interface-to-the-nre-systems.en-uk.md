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

## Example (Last rendered on 2022-08-25 20:04)

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
## Reading (RDG) Station Board on 2022-08-25 20:05:00
## Time   From                                    Plat  Expected
## 20:46  London Paddington                       12B   20:58
## 20:51  London Paddington                       9B    21:04
## 20:56  London Paddington                       8B    21:18
## 21:00  Penzance                                11    21:02
## 21:01  London Paddington                       -     Cancelled
## 21:03  Didcot Parkway                          15A   20:58
## 21:04  Basingstoke                             2     On time
## 21:07  Bournemouth                             8     21:09
## 21:09  Bristol Temple Meads                    15A   21:14
## 21:10  London Paddington                       14    21:27
## 21:12  London Waterloo                         6     On time
## 21:13  London Paddington                       13    21:22
## 21:16  London Paddington                       9     21:19
## 21:20  London Paddington                       8     21:29
## 21:21  Bedwyn                                  15    On time
## 21:25  Oxford                                  10    On time
## 21:28  Basingstoke                             2     On time
## 21:29  Didcot Parkway                          14    On time
## 21:29  Redhill                                 -     Cancelled
## 21:32  London Paddington                       7     On time
## 21:33  Cheltenham Spa                          11    On time
## 21:39  Newbury                                 1     On time
## 21:41  London Waterloo                         4     On time
## 21:41  Manchester Piccadilly                   7     On time
## 21:42  London Paddington                       14    21:56
## 21:44  Swansea                                 13    On time
## 21:45  London Paddington                       12    21:48
## 21:50  London Paddington                       9     On time
## 21:53  Great Malvern                           10    On time
## 21:56  Gatwick Airport                         -     Cancelled
## 21:57  Basingstoke                             3     On time
## 22:01  London Paddington                       9     On time
## 22:02  Paignton                                14    On time
## 22:05  Didcot Parkway                          15    On time
## 22:08  London Paddington                       13    On time
## 22:11  Exeter St Davids                        15    On time
## 22:11  London Paddington                       14    On time
## 22:16  London Paddington                       12    On time
## 22:16  Newbury                                 13B   On time
## 22:18  London Paddington                       9     On time
## 22:21  London Paddington                       8     On time
## 22:23  Newbury                                 11    On time
## 22:25  Oxford                                  15    On time
## 22:30  London Paddington                       9     On time
## 22:32  Cheltenham Spa                          10    On time
## 22:34  Shalford                                14A   Delayed
## 22:40  Basingstoke                             2     On time
## 22:41  London Waterloo                         6     On time
## 22:41  Manchester Piccadilly                   7     On time
## 22:42  London Paddington                       14    On time
## 22:43  Swansea                                 10    On time
## 22:45  Didcot Parkway                          15    On time
## 22:45  London Paddington                       12    On time
## 22:48  London Paddington                       9     On time
## 22:52  Salisbury                               3     On time
## 22:57  London Paddington                       12    On time
## 22:59  London Paddington                       13    On time
## 22:59  Worcester Foregate Street               15    On time
## 23:03  Ash                                     -     On time
## 23:03  Basingstoke                             14A   On time
## 21:20  Heathrow Central Bus Stn                BUS   On time
## 22:30  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-25 20:05:05
## Time   To                                      Plat  Expected
## 20:51  Didcot Parkway                          12B   Delayed
## 20:52  Oxford                                  9B    21:05
## 20:58  Cheltenham Spa                          8B    21:19
## 21:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 21:02  Weston-super-Mare                       -     Cancelled
## 21:03  London Paddington                       11    On time
## 21:07  Ealing Broadway                         15A   On time
## 21:10  Newbury                                 1     On time
## 21:12  London Waterloo                         4     On time
## 21:13  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:15  London Paddington                       15A   On time
## 21:17  Swansea                                 9     21:20
## 21:22  Basingstoke                             2     On time
## 21:22  Great Malvern                           8     21:30
## 21:23  Didcot Parkway                          14    On time
## 21:23  London Paddington                       15    On time
## 21:27  Ealing Broadway                         13    On time
## 21:31  Bristol Temple Meads                    9     On time
## 21:34  Ash                                     -     On time
## 21:34  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 21:34  London Paddington                       10    On time
## 21:34  Plymouth                                7     On time
## 21:37  London Paddington                       11    On time
## 21:39  Ealing Broadway                         14    On time
## 21:42  London Waterloo                         6     On time
## 21:46  London Paddington                       13    On time
## 21:49  Didcot Parkway                          12    On time
## 21:52  Bournemouth                             7     On time
## 21:52  Oxford                                  9     On time
## 21:57  Ealing Broadway                         14    On time
## 22:03  London Paddington                       10    On time
## 22:04  Cheltenham Spa                          9     On time
## 22:05  Basingstoke                             3     On time
## 22:06  London Paddington                       14    On time
## 22:08  Ealing Broadway                         15    On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         4     On time
## 22:15  London Paddington                       15    On time
## 22:18  Didcot Parkway                          12    On time
## 22:20  Swansea                                 9     On time
## 22:23  Worcester Shrub Hill                    8     On time
## 22:24  London Paddington                       11    On time
## 22:26  London Paddington                       15    On time
## 22:27  Ealing Broadway                         14    On time
## 22:29  Basingstoke                             2     On time
## 22:31  Plymouth                                9     On time
##        via Bristol                             
## 22:36  London Paddington                       10    On time
## 22:46  Didcot Parkway                          12    On time
## 22:48  London Paddington                       10    On time
## 22:49  Oxford                                  9     On time
## 22:49  Southampton Central                     7     On time
## 22:52  Basingstoke                             2     On time
## 22:57  Ealing Broadway                         14    On time
## 23:01  Bedwyn                                  12    On time
## 23:01  London Paddington                       15    On time
## 23:02  Bristol Temple Meads                    13    On time
## 23:02  London Waterloo                         6     On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
