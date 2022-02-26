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

## Example (Last rendered on 2022-02-26 16:03)

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
## Reading (RDG) Station Board on 2022-02-26 16:03:48
## Time   From                                    Plat  Expected
## 16:00  Didcot Parkway                          15    On time
## 16:00  Exeter St Davids                        11    On time
## 16:10  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12    On time
## 16:16  London Waterloo                         6     16:18
## 16:17  London Paddington                       9     On time
## 16:18  Cardiff Central                         10    On time
## 16:20  Basingstoke                             2     On time
## 16:23  Bedwyn                                  11    On time
## 16:25  London Paddington                       9     On time
## 16:27  London Paddington                       7     On time
## 16:27  Oxford                                  10    On time
## 16:31  Didcot Parkway                          15    On time
## 16:32  London Paddington                       7B    On time
## 16:39  Manchester Piccadilly                   7B    On time
## 16:40  Weston-super-Mare                       10A   On time
## 16:41  Newbury                                 1     On time
## 16:43  London Paddington                       14    On time
## 16:44  London Paddington                       12    On time
## 16:46  London Waterloo                         6     On time
## 16:46  Swansea                                 10    17:04
## 16:47  London Paddington                       9     On time
## 16:50  Basingstoke                             2     On time
## 16:51  London Paddington                       8     On time
## 16:54  Great Malvern                           10A   On time
## 16:55  London Paddington                       9     On time
## 16:59  Exeter St Davids                        11    On time
## 16:59  London Paddington                       7     On time
## 17:01  Didcot Parkway                          15    On time
## 17:10  Bristol Temple Meads                    10    On time
## 17:11  London Paddington                       9     On time
## 17:13  London Paddington                       14    On time
## 17:14  London Paddington                       12    On time
## 17:16  London Waterloo                         6     On time
## 17:17  London Paddington                       9     On time
## 17:20  Basingstoke                             2     On time
## 17:23  Bedwyn                                  11    On time
## 17:25  London Paddington                       9     On time
## 17:25  Oxford                                  10    On time
## 17:27  London Paddington                       -     Cancelled
## 17:31  Didcot Parkway                          15    On time
## 17:33  Cheltenham Spa                          11    On time
## 17:33  London Paddington                       7B    On time
## 17:40  Weston-super-Mare                       10    On time
## 17:41  London Paddington                       9     On time
## 17:41  Newbury                                 1     On time
## 17:43  London Paddington                       14    On time
## 17:43  Taunton                                 11    On time
## 17:44  London Paddington                       12    On time
## 17:46  London Waterloo                         6     On time
## 17:47  London Paddington                       9     On time
## 17:47  Swansea                                 10    On time
## 17:51  London Paddington                       8     On time
## 17:54  Basingstoke                             2     On time
## 17:54  Hereford                                10    On time
## 17:55  London Paddington                       -     Cancelled
## 16:03  Guildford                               BUS   On time
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 16:36  Guildford                               BUS   On time
## 16:58  Guildford                               BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
## 17:22  Guildford                               BUS   On time
## 17:36  Guildford                               BUS   On time
## 17:58  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-26 16:03:53
## Time   To                                      Plat  Expected
## 16:05  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:10  London Waterloo                         6     On time
## 16:12  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15    On time
## 16:19  Great Malvern                           9     On time
## 16:19  London Paddington                       10    On time
## 16:22  Ealing Broadway                         14    On time
## 16:23  Didcot Parkway                          12    On time
## 16:24  London Paddington                       11    On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:28  London Paddington                       10    On time
## 16:29  Exeter St Davids                        7     On time
## 16:34  Bedwyn                                  7B    On time
## 16:37  Basingstoke                             2     On time
## 16:40  London Waterloo                         6     On time
## 16:42  London Paddington                       10A   On time
## 16:45  Ealing Broadway                         15    On time
## 16:48  London Paddington                       10    17:05
## 16:49  Oxford                                  9     On time
## 16:52  Ealing Broadway                         14    On time
## 16:52  Southampton Central                     7B    On time
## 16:53  Cheltenham Spa                          8     On time
## 16:53  Didcot Parkway                          12    On time
## 16:56  London Paddington                       10A   On time
## 16:57  Taunton                                 9     On time
## 17:01  Taunton                                 7     On time
## 17:05  London Paddington                       11    On time
## 17:07  Basingstoke                             2     On time
## 17:10  London Waterloo                         6     On time
## 17:12  London Paddington                       10    On time
## 17:12  Newbury                                 1     On time
## 17:13  Swansea                                 9     On time
## 17:15  Ealing Broadway                         15    On time
## 17:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                9     On time
## 17:22  Ealing Broadway                         14    On time
## 17:23  Didcot Parkway                          12    On time
## 17:24  London Paddington                       11    On time
## 17:27  Bristol Temple Meads                    9     On time
## 17:27  London Paddington                       10    On time
## 17:30  Exeter St Davids                        -     Cancelled
## 17:35  Bedwyn                                  7B    On time
## 17:35  London Paddington                       11    On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Waterloo                         6     On time
## 17:42  London Paddington                       10    On time
## 17:43  Carmarthen                              9     On time
## 17:45  Ealing Broadway                         15    On time
## 17:45  London Paddington                       11    On time
## 17:48  London Paddington                       10    On time
## 17:49  Oxford                                  9     On time
## 17:52  Ealing Broadway                         14    On time
## 17:53  Cheltenham Spa                          8     On time
## 17:55  Didcot Parkway                          12    On time
## 17:56  London Paddington                       10    On time
## 17:57  Weston-super-Mare                       -     Cancelled
## 16:14  Guildford                               BUS   On time
## 16:57  Guildford                               BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:14  Guildford                               BUS   On time
## 17:35  Guildford                               BUS   On time
## 17:57  Guildford                               BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
