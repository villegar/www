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

## Example (Last rendered on 2022-04-16 10:05)

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
## Reading (RDG) Station Board on 2022-04-16 10:05:56
## Time   From                                    Plat  Expected
## 11:01  Didcot Parkway                          13A   On time
## 11:01  Penzance                                11    11:03
## 11:05  Bournemouth                             12    11:07
## 11:10  Bristol Temple Meads                    10    On time
## 11:11  London Paddington                       8     On time
## 11:13  London Paddington                       14    On time
## 11:18  London Paddington                       12B   On time
## 11:21  Bedwyn                                  11A   On time
## 11:24  Oxford                                  10A   On time
## 11:25  London Paddington                       9     On time
## 11:27  London Paddington                       7     On time
## 11:28  Basingstoke                             2     On time
## 11:28  Bristol Parkway                         11A   On time
## 11:31  Didcot Parkway                          15A   On time
## 11:33  Cheltenham Spa                          10A   11:52
## 11:33  London Paddington                       7B    On time
## 11:33  Redhill                                 6     On time
## 11:39  Manchester Piccadilly                   13    On time
## 11:40  Bristol Temple Meads                    10    On time
## 11:41  Newbury                                 7     On time
## 11:43  London Paddington                       14    On time
## 11:43  Paignton                                11    On time
## 11:44  London Paddington                       12B   On time
## 11:46  Swansea                                 10    On time
## 11:47  London Paddington                       9     On time
## 11:51  Gatwick Airport                         4     11:55
## 11:51  London Paddington                       8B    On time
## 11:54  Moreton-in-Marsh                        10A   On time
## 11:55  London Paddington                       9     On time
## 11:56  Basingstoke                             2     On time
## 12:00  Penzance                                -     Cancelled
## 12:02  Didcot Parkway                          15A   On time
## 12:10  Bristol Temple Meads                    10    On time
## 12:11  London Paddington                       9     On time
## 12:13  London Paddington                       14    On time
## 12:14  London Paddington                       12B   On time
## 12:17  London Paddington                       9B    On time
## 12:20  Basingstoke                             2     On time
## 12:23  Bedwyn                                  11A   On time
## 12:25  London Paddington                       9     On time
## 12:25  Oxford                                  10A   On time
## 12:27  London Paddington                       7     On time
## 12:31  Didcot Parkway                          15A   On time
## 12:33  London Paddington                       7B    On time
## 12:33  Redhill                                 4     On time
## 12:34  Cheltenham Spa                          11A   On time
## 12:38  London Paddington                       9     On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:42  Newbury                                 8     On time
## 12:43  London Paddington                       14    On time
## 12:44  London Paddington                       12B   On time
## 12:46  Swansea                                 10    On time
## 12:47  London Paddington                       9     On time
## 12:51  Gatwick Airport                         6     On time
## 12:54  Moreton-in-Marsh                        10    On time
## 12:55  Basingstoke                             2     On time
## 12:55  London Paddington                       9     On time
## 12:55  Newbury Racecourse                      14    On time
## 12:58  London Paddington                       7     On time
## 12:59  Penzance                                11    On time
## 11:09  Staines                                 BUS   On time
## 11:12  Staines                                 BUS   On time
## 11:38  Staines                                 BUS   On time
## 11:38  Staines                                 BUS   On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:07  Staines                                 BUS   On time
## 12:08  Staines                                 BUS   On time
## 12:37  Staines                                 BUS   On time
## 12:38  Staines                                 BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-16 10:06:00
## Time   To                                      Plat  Expected
## 11:05  Basingstoke                             2     On time
## 11:05  London Paddington                       11    On time
## 11:10  Newbury                                 15A   On time
## 11:12  London Paddington                       10    On time
## 11:13  Swansea                                 8     On time
## 11:15  Ealing Broadway                         13A   On time
## 11:15  Manchester Piccadilly                   12    On time
##        via Stoke-on-Trent                      
## 11:19  Moreton-in-Marsh                        9B    On time
## 11:20  Redhill                                 6     On time
## 11:22  Ealing Broadway                         14    On time
## 11:23  Didcot Parkway                          12B   On time
## 11:24  London Paddington                       11A   On time
## 11:27  Bristol Temple Meads                    9     On time
## 11:27  London Paddington                       10A   On time
## 11:30  Plymouth                                7     On time
## 11:32  London Paddington                       11A   On time
## 11:35  Bedwyn                                  7B    On time
## 11:35  London Paddington                       10A   11:53
## 11:38  Basingstoke                             2     On time
## 11:42  London Paddington                       10    On time
## 11:45  Ealing Broadway                         15A   On time
## 11:45  London Paddington                       11    On time
## 11:48  London Paddington                       10    On time
## 11:49  Oxford                                  9     On time
## 11:52  Ealing Broadway                         14    On time
## 11:53  Cheltenham Spa                          8B    On time
## 11:53  Newbury Racecourse                      7B    On time
## 11:54  Didcot Parkway                          12B   On time
## 11:57  London Paddington                       10A   On time
## 11:57  Weston-super-Mare                       9     On time
## 12:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 12:05  London Paddington                       -     Cancelled
## 12:08  Basingstoke                             2     On time
## 12:11  Ealing Broadway                         15A   On time
## 12:12  London Paddington                       10    On time
## 12:12  Newbury                                 7B    On time
## 12:13  Swansea                                 9     On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Stoke-on-Trent                      
## 12:19  Moreton-in-Marsh                        9B    On time
## 12:20  Redhill                                 4     On time
## 12:22  Ealing Broadway                         14    On time
## 12:23  Didcot Parkway                          12B   On time
## 12:24  London Paddington                       11A   On time
## 12:27  Bristol Temple Meads                    9     On time
## 12:27  London Paddington                       10A   On time
## 12:30  Penzance                                7     On time
## 12:35  Bedwyn                                  7B    On time
## 12:35  London Paddington                       11A   On time
## 12:38  Basingstoke                             2     On time
## 12:40  Cardiff Central                         9     On time
## 12:42  London Paddington                       10    On time
## 12:45  Ealing Broadway                         15A   On time
## 12:48  London Paddington                       10    On time
## 12:48  Newbury Racecourse                      8     On time
## 12:49  Oxford                                  9     On time
## 12:52  Bournemouth                             7     On time
## 12:52  Ealing Broadway                         14    On time
## 12:53  Didcot Parkway                          12B   On time
## 12:57  London Paddington                       10    On time
## 12:57  Weston-super-Mare                       9     On time
## 13:01  Exeter St Davids                        7     On time
## 13:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:13  Staines                                 BUS   On time
## 11:13  Staines                                 BUS   On time
## 11:43  Staines                                 BUS   On time
## 11:43  Staines                                 BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 12:13  Staines                                 BUS   On time
## 12:13  Staines                                 BUS   On time
## 12:43  Staines                                 BUS   On time
## 12:43  Staines                                 BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
