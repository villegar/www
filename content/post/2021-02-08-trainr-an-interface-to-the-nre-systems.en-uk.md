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

## Example (Last rendered on 2022-04-16 14:04)

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
## Reading (RDG) Station Board on 2022-04-16 14:04:11
## Time   From                                    Plat  Expected
## 14:59  London Paddington                       7B    15:08
## 15:00  Penzance                                11    15:14
## 15:01  Didcot Parkway                          15A   On time
## 15:07  Bournemouth                             13    On time
## 15:10  Bristol Temple Meads                    10    On time
## 15:11  London Paddington                       8     On time
## 15:13  London Paddington                       14    On time
## 15:14  London Paddington                       12B   On time
## 15:17  London Paddington                       9B    On time
## 15:20  Basingstoke                             2     On time
## 15:23  Bedwyn                                  11A   On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10A   On time
## 15:27  London Paddington                       7     On time
## 15:31  Didcot Parkway                          15A   On time
## 15:32  London Paddington                       7B    On time
## 15:33  Cheltenham Spa                          11A   On time
## 15:33  Redhill                                 6     On time
## 15:38  London Paddington                       9     On time
## 15:40  Newbury                                 1     On time
## 15:40  Weston-super-Mare                       10    On time
## 15:42  Exeter St Davids                        -     Cancelled
## 15:43  London Paddington                       14    On time
## 15:44  London Paddington                       12B   On time
## 15:47  London Paddington                       9B    On time
## 15:47  Swansea                                 10    On time
## 15:51  Basingstoke                             2     On time
## 15:51  Gatwick Airport                         4     On time
## 15:53  Moreton-in-Marsh                        10A   On time
## 15:55  London Paddington                       9     On time
## 16:00  Didcot Parkway                          15A   On time
## 16:00  Plymouth                                11    On time
## 16:10  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       9     On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12B   On time
## 16:17  London Paddington                       9B    On time
## 16:18  Cardiff Central                         10A   On time
## 16:20  Basingstoke                             2     On time
## 16:23  Bedwyn                                  -     Cancelled
## 16:25  London Paddington                       9     On time
## 16:27  London Paddington                       7     On time
## 16:27  Oxford                                  10A   On time
## 16:31  Didcot Parkway                          15    On time
## 16:32  London Paddington                       7B    On time
## 16:33  Redhill                                 4     On time
## 16:39  Manchester Piccadilly                   7B    On time
## 16:40  Weston-super-Mare                       11    On time
## 16:43  London Paddington                       14    On time
## 16:43  Newbury                                 10    On time
## 16:44  London Paddington                       12    On time
## 16:46  Swansea                                 11    On time
## 16:47  London Paddington                       9B    On time
## 16:50  Basingstoke                             2     On time
## 16:51  Gatwick Airport                         6     On time
## 16:51  London Paddington                       8     On time
## 16:54  Moreton-in-Marsh                        11    On time
## 16:55  London Paddington                       9     On time
## 16:59  London Paddington                       -     Cancelled
## 15:07  Staines                                 BUS   On time
## 15:08  Staines                                 BUS   On time
## 15:37  Staines                                 BUS   On time
## 15:38  Staines                                 BUS   On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
## 16:07  Staines                                 BUS   On time
## 16:08  Staines                                 BUS   On time
## 16:37  Staines                                 BUS   On time
## 16:38  Staines                                 BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-16 14:04:14
## Time   To                                      Plat  Expected
## 15:01  Plymouth                                7B    15:10
## 15:05  London Paddington                       11    15:15
## 15:07  Basingstoke                             2     On time
## 15:12  London Paddington                       10    On time
## 15:12  Newbury                                 1     On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15A   On time
## 15:15  Manchester Piccadilly                   13    On time
##        via Stoke-on-Trent                      
## 15:19  Moreton-in-Marsh                        9B    On time
## 15:20  Redhill                                 6     On time
## 15:22  Ealing Broadway                         14    On time
## 15:24  Didcot Parkway                          12B   On time
## 15:24  London Paddington                       11A   On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       10A   On time
## 15:29  Penzance                                7     On time
## 15:34  Bedwyn                                  7B    On time
## 15:35  London Paddington                       11A   On time
## 15:37  Basingstoke                             2     On time
## 15:40  Bristol Parkway                         9     On time
## 15:43  London Paddington                       10    On time
## 15:45  Ealing Broadway                         15A   On time
## 15:46  London Paddington                       -     Cancelled
## 15:48  London Paddington                       10    On time
## 15:49  Oxford                                  9B    On time
## 15:52  Ealing Broadway                         14    On time
## 15:53  Didcot Parkway                          12B   On time
## 15:57  Weston-super-Mare                       9     On time
## 15:58  London Paddington                       10A   On time
## 16:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 16:05  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:12  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15A   On time
## 16:19  London Paddington                       10A   On time
## 16:19  Moreton-in-Marsh                        9B    On time
## 16:20  Redhill                                 4     On time
## 16:22  Ealing Broadway                         14    On time
## 16:23  Didcot Parkway                          12B   On time
## 16:24  London Paddington                       -     Cancelled
## 16:27  Bristol Temple Meads                    9     On time
## 16:28  London Paddington                       10A   On time
## 16:29  Plymouth                                7     On time
## 16:34  Bedwyn                                  7B    On time
## 16:37  Basingstoke                             2     On time
## 16:42  London Paddington                       11    On time
## 16:45  Ealing Broadway                         15    On time
## 16:48  London Paddington                       11    On time
## 16:49  Oxford                                  9B    On time
## 16:52  Bournemouth                             7B    On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  Cheltenham Spa                          8     On time
## 16:53  Didcot Parkway                          12    On time
## 16:56  London Paddington                       11    On time
## 16:57  Taunton                                 9     On time
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:01  Paignton                                -     Cancelled
## 15:13  Staines                                 BUS   On time
## 15:13  Staines                                 BUS   On time
## 15:43  Staines                                 BUS   On time
## 15:43  Staines                                 BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 16:13  Staines                                 BUS   On time
## 16:13  Staines                                 BUS   On time
## 16:43  Staines                                 BUS   On time
## 16:43  Staines                                 BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
