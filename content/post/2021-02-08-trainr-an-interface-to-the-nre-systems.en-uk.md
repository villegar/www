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

## Example (Last rendered on 2021-08-09 14:09)

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
## Reading (RDG) Station Board on 2021-08-09 14:09:08
## Time   From                                    Plat  Expected
## 14:45  Swansea                                 10    15:22
## 14:55  London Paddington                       8     15:05
## 15:05  Bournemouth                             8     Delayed
## 15:09  Bristol Parkway                         10    15:26
## 15:13  London Paddington                       13    15:07
## 15:14  London Paddington                       12    On time
## 15:16  London Paddington                       9     On time
## 15:17  London Waterloo                         4     On time
## 15:22  Newbury                                 11    On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10    On time
## 15:26  Basingstoke                             2     On time
## 15:27  London Paddington                       7     On time
## 15:30  Cheltenham Spa                          10    15:36
## 15:32  Didcot Parkway                          15    On time
## 15:32  London Paddington                       7B    On time
## 15:33  Redhill                                 5     On time
## 15:36  Newbury                                 1     On time
## 15:39  Bath Spa                                11    On time
## 15:40  Manchester Piccadilly                   8     On time
## 15:41  London Paddington                       9     On time
## 15:43  London Paddington                       14    On time
## 15:44  Swansea                                 10    16:02
## 15:45  London Waterloo                         6     On time
## 15:46  London Paddington                       9     On time
## 15:47  Exeter St Davids                        11    On time
## 15:51  Gatwick Airport                         4     On time
## 15:53  Basingstoke                             2     On time
## 15:53  Hereford                                10    On time
## 15:56  London Paddington                       9     On time
## 15:57  Plymouth                                11    On time
## 16:09  Bristol Parkway                         10    On time
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       14    On time
## 16:17  Bristol Parkway                         11    On time
## 16:17  London Waterloo                         4     On time
## 16:18  Basingstoke                             2     On time
## 16:22  London Paddington                       12    On time
## 16:22  Newbury                                 11    On time
## 16:24  Oxford                                  10    On time
## 16:25  London Paddington                       9     On time
## 16:27  London Paddington                       8     On time
## 16:31  Didcot Parkway                          14    On time
## 16:31  London Paddington                       7B    On time
## 16:32  Newbury                                 1     On time
## 16:33  Redhill                                 5     On time
## 16:39  Bath Spa                                10    On time
## 16:41  Manchester Piccadilly                   7     On time
## 16:43  London Paddington                       14    On time
## 16:43  Paignton                                11    On time
## 16:45  London Waterloo                         6     On time
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       9     On time
## 16:46  London Paddington                       13    On time
## 16:50  Basingstoke                             2     On time
## 16:54  Worcester Foregate Street               10    On time
## 16:56  London Paddington                       9     On time
## 16:56  Newbury                                 3     On time
## 16:58  London Paddington                       14    On time
## 16:59  London Paddington                       7     On time
## 17:00  Gatwick Airport                         5     On time
## 17:01  Penzance                                10    On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-09 14:09:13
## Time   To                                      Plat  Expected
## 14:48  London Paddington                       10    15:23
## 14:57  Bristol Parkway                         8     15:08
## 15:05  Basingstoke                             2     15:07
## 15:10  London Waterloo                         6     On time
## 15:10  Newbury                                 1     On time
## 15:13  London Paddington                       10    15:27
## 15:13  Swansea                                 9     On time
## 15:15  Manchester Piccadilly                   8     Delayed
##        via Coventry & Stoke-on-Trent           
## 15:18  Redhill                                 5     On time
## 15:18  Worcester Foregate Street               9     On time
## 15:22  Ealing Broadway                         13    On time
## 15:23  Didcot Parkway                          12    On time
## 15:24  London Paddington                       11    On time
## 15:27  Bath Spa                                9     On time
## 15:27  London Paddington                       10    On time
## 15:29  Penzance                                7     On time
## 15:32  Basingstoke                             2     On time
## 15:34  London Paddington                       10    15:37
## 15:37  Bedwyn                                  7B    On time
## 15:39  Ealing Broadway                         15    On time
## 15:40  London Waterloo                         4     On time
## 15:43  Cardiff Central                         9     On time
## 15:43  London Paddington                       11    On time
## 15:45  London Paddington                       10    16:03
## 15:48  Worcester Foregate Street               9     On time
## 15:50  London Paddington                       11    On time
## 15:50  Newbury                                 3     On time
## 15:52  Ealing Broadway                         14    On time
## 15:55  Oxford                                  15B   On time
## 15:56  London Paddington                       10    On time
## 15:58  Bristol Parkway                         9     On time
## 16:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:04  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:10  London Waterloo                         6     On time
## 16:12  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15    On time
## 16:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           9     On time
## 16:19  London Paddington                       11    On time
## 16:20  Redhill                                 5     On time
## 16:22  Ealing Broadway                         14    On time
## 16:24  London Paddington                       11    On time
## 16:25  Didcot Parkway                          12    On time
## 16:27  Bath Spa                                9     On time
## 16:27  London Paddington                       10    On time
## 16:27  London Paddington                       15    On time
## 16:29  Penzance                                8     On time
## 16:33  Basingstoke                             2     On time
## 16:33  Ealing Broadway                         13    On time
## 16:37  Newbury                                 7B    On time
## 16:38  Ealing Broadway                         14    On time
## 16:39  London Waterloo                         4     On time
## 16:42  London Paddington                       10    On time
## 16:45  London Paddington                       11    On time
## 16:48  London Paddington                       10    On time
## 16:48  Oxford                                  9     On time
## 16:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:52  Bournemouth                             7     On time
## 16:52  Ealing Broadway                         14    On time
## 16:57  London Paddington                       10    On time
## 16:58  Bristol Parkway                         9     On time
## 17:02  Plymouth                                7     On time
## 17:03  Ealing Broadway                         14    On time
## 17:05  London Paddington                       10    On time
## 17:06  Ealing Broadway                         13    On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
