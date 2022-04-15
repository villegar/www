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

## Example (Last rendered on 2022-04-15 12:04)

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
## Reading (RDG) Station Board on 2022-04-15 12:04:36
## Time   From                                    Plat  Expected
## 12:58  Penzance                                11    13:04
## 13:01  Didcot Parkway                          15A   12:58
## 13:05  Bournemouth                             8B    On time
## 13:09  Bristol Temple Meads                    10    On time
## 13:11  London Paddington                       9     13:35
## 13:13  London Paddington                       14    On time
## 13:14  London Paddington                       12B   On time
## 13:16  London Paddington                       9B    On time
## 13:18  Basingstoke                             2     On time
## 13:24  Newbury                                 11A   On time
## 13:24  Oxford                                  10    On time
## 13:25  London Paddington                       9     13:29
## 13:30  Cheltenham Spa                          10A   On time
## 13:31  Didcot Parkway                          13A   On time
## 13:33  London Paddington                       7B    On time
## 13:33  Redhill                                 6     On time
## 13:36  Newbury                                 1     On time
## 13:39  Bristol Temple Meads                    10    On time
## 13:41  Manchester Piccadilly                   8     On time
## 13:42  Paignton                                11    On time
## 13:43  London Paddington                       14    On time
## 13:45  London Paddington                       13B   On time
## 13:45  Swansea                                 10    On time
## 13:46  London Paddington                       9B    On time
## 13:51  Gatwick Airport                         4     On time
## 13:51  London Paddington                       9B    On time
## 13:54  Moreton-in-Marsh                        10    On time
## 13:55  Basingstoke                             2     On time
## 13:56  London Paddington                       9     On time
## 14:02  Penzance                                11    On time
## 14:03  Didcot Parkway                          15A   On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:11  London Paddington                       9     On time
## 14:13  London Paddington                       14    On time
## 14:14  London Paddington                       12B   On time
## 14:16  Cardiff Central                         11    On time
## 14:16  London Paddington                       9B    On time
## 14:19  Basingstoke                             2     On time
## 14:22  Bedwyn                                  11A   On time
## 14:24  Oxford                                  10    On time
## 14:25  London Paddington                       9     On time
## 14:29  Cheltenham Spa                          11A   On time
## 14:31  Didcot Parkway                          15A   On time
## 14:33  Redhill                                 6     On time
## 14:34  London Paddington                       7B    On time
## 14:40  Bristol Temple Meads                    10    On time
## 14:40  Manchester Piccadilly                   13    On time
## 14:40  Newbury                                 1     On time
## 14:43  London Paddington                       14    On time
## 14:44  London Paddington                       12B   On time
## 14:45  Swansea                                 10    On time
## 14:46  London Paddington                       9     On time
## 14:49  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         4     On time
## 14:51  London Paddington                       8     On time
## 14:55  London Paddington                       9     On time
## 14:55  Moreton-in-Marsh                        10    On time
## 15:00  London Paddington                       7     On time
## 13:03  Staines                                 BUS   On time
## 13:07  Staines                                 BUS   On time
## 13:33  Staines                                 BUS   On time
## 13:37  Staines                                 BUS   On time
## 13:45  Heathrow Central Bus Stn                BUS   On time
## 14:03  Staines                                 BUS   On time
## 14:07  Staines                                 BUS   On time
## 14:33  Staines                                 BUS   On time
## 14:37  Staines                                 BUS   On time
## 14:45  Heathrow Central Bus Stn                BUS   On time
## 15:03  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-15 12:04:39
## Time   To                                      Plat  Expected
## 13:04  London Paddington                       11    13:05
## 13:07  Basingstoke                             2     On time
## 13:08  Ealing Broadway                         15A   On time
## 13:12  Newbury                                 1     On time
## 13:13  Swansea                                 9     13:36
## 13:14  London Paddington                       10    On time
## 13:15  Manchester Piccadilly                   8B    On time
##        via Stoke-on-Trent                      
## 13:18  Moreton-in-Marsh                        9B    On time
## 13:20  Ealing Broadway                         14    On time
## 13:20  Redhill                                 6     On time
## 13:23  Didcot Parkway                          12B   On time
## 13:26  London Paddington                       10    On time
## 13:27  Bristol Temple Meads                    9     13:30
## 13:29  Plymouth                                8     On time
## 13:31  London Paddington                       11A   On time
## 13:32  Basingstoke                             2     On time
## 13:34  London Paddington                       10A   On time
## 13:37  Newbury                                 7B    On time
## 13:38  Ealing Broadway                         13A   On time
## 13:41  London Paddington                       10    On time
## 13:42  London Paddington                       11    On time
## 13:48  London Paddington                       10    On time
## 13:48  Oxford                                  9B    On time
## 13:52  Ealing Broadway                         14    On time
## 13:53  Cheltenham Spa                          9B    On time
## 13:55  Didcot Parkway                          13B   On time
## 13:57  London Paddington                       10    On time
## 13:58  Bristol Temple Meads                    9     On time
## 14:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 14:04  London Paddington                       11    On time
## 14:07  Basingstoke                             2     On time
## 14:09  Ealing Broadway                         15A   On time
## 14:11  London Paddington                       10    On time
## 14:12  Newbury                                 1     On time
## 14:13  Swansea                                 9     On time
## 14:15  Manchester Piccadilly                   8B    On time
##        via Stoke-on-Trent                      
## 14:18  Moreton-in-Marsh                        9B    On time
## 14:19  London Paddington                       11    On time
## 14:20  Redhill                                 6     On time
## 14:22  Ealing Broadway                         14    On time
## 14:24  London Paddington                       11A   On time
## 14:25  Didcot Parkway                          12B   On time
## 14:27  Bristol Temple Meads                    9     On time
## 14:27  London Paddington                       10    On time
## 14:29  Penzance                                7     On time
## 14:32  Basingstoke                             2     On time
## 14:35  London Paddington                       11A   On time
## 14:37  Newbury                                 7B    On time
## 14:43  London Paddington                       10    On time
## 14:45  Ealing Broadway                         15A   On time
## 14:48  London Paddington                       10    On time
## 14:49  Bournemouth                             13    On time
## 14:49  Oxford                                  9     On time
## 14:52  Ealing Broadway                         14    On time
## 14:53  Cheltenham Spa                          8     On time
## 14:55  Didcot Parkway                          12B   On time
## 14:57  London Paddington                       10    On time
## 14:57  Weston-super-Mare                       9     On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:02  Paignton                                7     On time
## 13:13  Staines                                 BUS   On time
## 13:13  Staines                                 BUS   On time
## 13:43  Staines                                 BUS   On time
## 13:43  Staines                                 BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
## 14:13  Staines                                 BUS   On time
## 14:13  Staines                                 BUS   On time
## 14:43  Staines                                 BUS   On time
## 14:43  Staines                                 BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
```
