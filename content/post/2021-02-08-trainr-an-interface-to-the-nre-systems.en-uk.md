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

## Example (Last rendered on 2021-11-16 16:05)

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
## Reading (RDG) Station Board on 2021-11-16 16:05:38
## Time   From                                    Plat  Expected
## 15:57  Plymouth                                11    16:02
## 16:09  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       14    On time
## 16:14  London Waterloo                         4     On time
## 16:17  Bristol Parkway                         11A   On time
## 16:18  Basingstoke                             2     On time
## 16:22  London Paddington                       12B   On time
## 16:22  Newbury                                 11A   On time
## 16:24  Oxford                                  10A   On time
## 16:25  London Paddington                       9     On time
## 16:27  London Paddington                       8     On time
## 16:31  Didcot Parkway                          14    On time
## 16:31  London Paddington                       7B    On time
## 16:32  Newbury                                 1     On time
## 16:33  Redhill                                 5     On time
## 16:39  Bristol Temple Meads                    10    On time
## 16:41  Manchester Piccadilly                   7     On time
## 16:43  London Paddington                       14    On time
## 16:43  Paignton                                11    On time
## 16:44  London Waterloo                         6     16:46
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       9B    On time
## 16:46  London Paddington                       13    On time
## 16:50  Basingstoke                             2     On time
## 16:54  Worcester Foregate Street               10    On time
## 16:56  London Paddington                       9     On time
## 16:56  Newbury                                 3     On time
## 16:58  London Paddington                       14    On time
## 16:59  London Paddington                       7     On time
## 17:01  Penzance                                10    On time
## 17:03  Gatwick Airport                         5     On time
## 17:06  Bournemouth                             15    On time
## 17:09  Bristol Temple Meads                    11    On time
## 17:11  London Paddington                       9     On time
## 17:13  London Paddington                       14    On time
## 17:14  London Waterloo                         6     On time
## 17:22  Bedwyn                                  11A   On time
## 17:22  London Paddington                       12B   On time
## 17:25  London Paddington                       8     On time
## 17:26  Basingstoke                             2     On time
## 17:27  London Paddington                       7     On time
## 17:28  London Paddington                       14    On time
## 17:29  Cheltenham Spa                          10A   On time
## 17:33  Newbury                                 1     On time
## 17:34  London Paddington                       7B    On time
## 17:35  Didcot Parkway                          15    On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:38  London Paddington                       9     On time
## 17:39  Exeter St Davids                        11    On time
## 17:40  Manchester Piccadilly                   7     On time
## 17:43  London Paddington                       14    On time
## 17:43  London Waterloo                         4     On time
## 17:44  Redhill                                 5     On time
## 17:44  Swansea                                 10    On time
## 17:46  Basingstoke                             2     On time
## 17:54  London Paddington                       12B   On time
## 17:55  London Paddington                       8     On time
## 17:56  Hereford                                10A   On time
## 17:57  Plymouth                                11    On time
## 17:58  London Paddington                       9B    On time
## 17:58  London Paddington                       14    On time
## 18:01  London Paddington                       7     On time
## 18:02  Gatwick Airport                         6     On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-16 16:05:42
## Time   To                                      Plat  Expected
## 16:04  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:12  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15A   On time
## 16:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           9B    16:30
## 16:19  London Paddington                       11A   On time
## 16:20  Redhill                                 5     On time
## 16:22  Ealing Broadway                         14    On time
## 16:24  London Paddington                       11A   On time
## 16:25  Didcot Parkway                          12B   On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:27  London Paddington                       15    On time
## 16:27  London Paddington                       10A   On time
## 16:29  Penzance                                8     On time
## 16:33  Basingstoke                             2     On time
## 16:33  Ealing Broadway                         13    On time
## 16:37  Newbury                                 7B    On time
## 16:38  Ealing Broadway                         14    On time
## 16:39  London Waterloo                         4     On time
## 16:42  London Paddington                       10    On time
## 16:45  London Paddington                       11    On time
## 16:48  London Paddington                       10    On time
## 16:48  Oxford                                  9B    On time
## 16:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:52  Bournemouth                             7     On time
## 16:52  Ealing Broadway                         14    On time
## 16:57  London Paddington                       10    On time
## 16:58  Taunton                                 9     On time
## 17:02  Plymouth                                7     On time
## 17:03  Ealing Broadway                         14    On time
## 17:05  London Paddington                       10    On time
## 17:06  Ealing Broadway                         13    On time
## 17:09  London Waterloo                         6     On time
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       11    On time
## 17:13  Swansea                                 9     On time
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   15    On time
##        via Coventry & Stoke-on-Trent           
## 17:20  Redhill                                 5     On time
## 17:22  Ealing Broadway                         14    On time
## 17:24  London Paddington                       11A   On time
## 17:25  Didcot Parkway                          12B   On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:29  Penzance                                7     On time
## 17:32  London Paddington                       10A   On time
## 17:33  Ealing Broadway                         14    On time
## 17:35  Newbury                                 7B    On time
## 17:38  Basingstoke                             2     On time
## 17:39  Bristol Parkway                         9     On time
## 17:39  London Waterloo                         6     On time
## 17:41  London Paddington                       10    On time
## 17:42  Ealing Broadway                         15    On time
## 17:43  London Paddington                       11    On time
## 17:46  London Paddington                       10    On time
## 17:49  Newbury                                 3     On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:52  Bournemouth                             7     On time
## 17:52  Ealing Broadway                         14    On time
## 17:57  Basingstoke                             2     On time
## 17:57  Taunton                                 8     On time
## 17:58  Didcot Parkway                          12B   On time
## 17:58  London Paddington                       11    On time
## 18:00  Hereford                                9B    On time
## 18:00  London Paddington                       10A   On time
## 18:03  Plymouth                                7     On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
