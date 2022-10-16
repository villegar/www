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

## Example (Last rendered on 2022-10-16 14:05)

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
## Reading (RDG) Station Board on 2022-10-16 14:05:52
## Time   From                                    Plat  Expected
## 14:55  London Paddington                       9     15:02
## 14:57  London Paddington                       7     15:07
## 14:58  Great Malvern                           10    15:10
## 15:04  London Paddington                       9     On time
## 15:05  Southampton Airport Parkway             8     On time
## 15:08  London Paddington                       14    15:10
## 15:08  Redhill                                 4     15:05
## 15:09  Weston-super-Mare                       11    15:13
## 15:12  London Paddington                       9     15:16
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       12    15:21
## 15:18  Bedwyn                                  3     15:22
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10A   On time
## 15:27  London Paddington                       7     On time
## 15:33  Basingstoke                             2     On time
## 15:38  Gatwick Airport                         5     15:41
## 15:38  London Paddington                       14    On time
## 15:39  Manchester Piccadilly                   13    15:42
## 15:40  Bristol Temple Meads                    10    On time
## 15:41  Exeter St Davids                        12    On time
## 15:44  London Paddington                       8     On time
## 15:46  Swansea                                 11    On time
## 15:47  Salisbury                               1     On time
## 15:55  London Paddington                       9     On time
## 15:56  Ledbury                                 10A   On time
## 15:58  Exeter St Davids                        11    On time
## 16:03  London Paddington                       8     On time
## 16:08  London Paddington                       14    On time
## 16:08  Redhill                                 6     On time
## 16:09  Bristol Temple Meads                    11    On time
## 16:12  London Paddington                       9B    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       12    On time
## 16:25  London Paddington                       9     On time
## 16:25  Oxford                                  10A   On time
## 16:27  London Paddington                       7     On time
## 16:32  Cheltenham Spa                          11A   On time
## 16:33  Basingstoke                             2     On time
## 16:38  Gatwick Airport                         5     On time
## 16:38  London Paddington                       14    On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:44  London Paddington                       9B    On time
## 16:44  Swansea                                 10    On time
## 16:47  Salisbury                               1     On time
## 16:55  London Paddington                       9     On time
## 16:57  London Paddington                       7     On time
## 16:58  Penzance                                11    On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:26  Staines                                 BUS   On time
## 15:27  Staines                                 BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:56  Staines                                 BUS   On time
## 15:57  Staines                                 BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:26  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:56  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-16 14:05:56
## Time   To                                      Plat  Expected
## 14:56  Taunton                                 9     15:04
## 15:01  Exeter St Davids                        7     15:08
## 15:04  Ealing Broadway                         14    On time
## 15:05  London Paddington                       10    15:11
## 15:10  Swansea                                 9     On time
## 15:12  Salisbury                               1     On time
## 15:14  Great Malvern                           9     15:17
## 15:14  London Paddington                       11    On time
## 15:14  London Paddington                       15    On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:25  Didcot Parkway                          12    On time
## 15:26  Bristol Temple Meads                    9     On time
## 15:28  London Paddington                       10A   On time
## 15:28  Plymouth                                7     On time
## 15:34  Ealing Broadway                         14    On time
## 15:38  Basingstoke                             2     On time
## 15:41  Redhill                                 4     On time
## 15:42  London Paddington                       12    On time
## 15:43  Bedwyn                                  3     On time
## 15:44  London Paddington                       10    On time
## 15:46  London Paddington                       11    On time
## 15:49  Oxford                                  8     On time
## 15:56  Taunton                                 9     On time
## 16:02  London Paddington                       11    On time
## 16:04  Ealing Broadway                         14    On time
## 16:05  London Paddington                       10A   On time
## 16:10  Swansea                                 8     On time
## 16:12  Salisbury                               1     On time
## 16:14  Ledbury                                 9B    On time
## 16:14  London Paddington                       15    On time
## 16:14  London Paddington                       11    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:25  Didcot Parkway                          12    On time
## 16:26  Bristol Temple Meads                    9     On time
## 16:28  London Paddington                       10A   On time
## 16:28  Penzance                                7     On time
## 16:34  Ealing Broadway                         14    On time
## 16:38  Basingstoke                             2     On time
## 16:41  Redhill                                 6     On time
## 16:42  London Paddington                       11A   On time
## 16:43  Newbury                                 3     On time
## 16:46  London Paddington                       10    On time
## 16:49  Oxford                                  9B    On time
## 16:52  Southampton Airport Parkway             13    On time
## 16:56  Plymouth                                9     On time
##        via Bristol                             
## 17:02  London Paddington                       11    On time
## 17:02  Plymouth                                7     On time
## 17:04  Ealing Broadway                         14    On time
## 15:25  Staines                                 BUS   On time
## 15:27  Staines                                 BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:55  Staines                                 BUS   On time
## 15:57  Staines                                 BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:25  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:55  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
