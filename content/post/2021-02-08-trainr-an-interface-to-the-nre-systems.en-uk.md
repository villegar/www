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

## Example (Last rendered on 2022-07-31 10:04)

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
## Reading (RDG) Station Board on 2022-07-31 10:04:14
## Time   From                                    Plat  Expected
## 11:05  Bournemouth                             8     On time
## 11:05  Bristol Temple Meads                    10    On time
## 11:08  Redhill                                 4     11:11
## 11:10  Didcot Parkway                          15    On time
## 11:15  London Paddington                       12    On time
## 11:19  Bedwyn                                  1     11:21
## 11:25  Oxford                                  10A   On time
## 11:26  London Paddington                       -     On time
## 11:26  London Paddington                       -     Cancelled
## 11:32  Swindon                                 10    On time
## 11:33  Basingstoke                             2     On time
## 11:33  London Paddington                       14    On time
## 11:38  Gatwick Airport                         -     On time
## 11:39  Manchester Piccadilly                   7     11:42
## 11:44  Swansea                                 11    12:30
## 11:45  London Paddington                       8B    On time
## 11:47  Salisbury                               1     On time
## 11:53  London Paddington                       9     On time
## 12:03  London Paddington                       14    On time
## 12:07  London Paddington                       -     On time
## 12:08  Redhill                                 4     On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Didcot Parkway                          15    On time
## 12:13  London Paddington                       12    On time
## 12:18  London Paddington                       9     On time
## 12:19  Newbury                                 1     On time
## 12:25  Oxford                                  10A   On time
## 12:26  London Paddington                       7     On time
## 12:33  Basingstoke                             2     On time
## 12:33  London Paddington                       14    On time
## 12:38  Gatwick Airport                         7A    On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:45  London Paddington                       9     On time
## 12:46  Swansea                                 -     13:11
## 12:47  Salisbury                               1     On time
## 12:47  Swindon                                 10    On time
## 12:51  Swansea                                 -     Cancelled
## 12:53  London Paddington                       9     On time
## 12:55  Plymouth                                11    On time
## 13:03  London Paddington                       14    On time
## 11:15  Staines                                 BUS   On time
## 11:26  Staines                                 BUS   On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 11:45  Staines                                 BUS   On time
## 11:56  Staines                                 BUS   On time
## 12:15  Staines                                 BUS   On time
## 12:26  Staines                                 BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
## 12:45  Staines                                 BUS   On time
## 12:56  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-31 10:04:17
## Time   To                                      Plat  Expected
## 11:11  London Paddington                       10    On time
## 11:12  Salisbury                               1     On time
## 11:14  Ealing Broadway                         15    On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:21  Gatwick Airport                         7A    On time
##        via Guildford                           
## 11:24  Ealing Broadway                         14    On time
## 11:25  London Paddington                       10A   On time
## 11:26  Didcot Parkway                          12    On time
## 11:27  Swindon                                 -     On time
## 11:28  Newquay                                 -     Cancelled
## 11:33  London Paddington                       10    On time
## 11:38  Basingstoke                             2     On time
## 11:41  Redhill                                 4     On time
## 11:43  Bedwyn                                  3     On time
## 11:45  London Paddington                       11    12:32
## 11:48  Oxford                                  8B    On time
## 11:52  Bournemouth                             7     On time
## 11:54  Bristol Temple Meads                    9     On time
## 11:54  Ealing Broadway                         14    On time
## 12:09  Swansea                                 -     On time
## 12:11  London Paddington                       10    On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         15    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Swindon                                 9     On time
## 12:21  Gatwick Airport                         8     On time
##        via Guildford                           
## 12:24  Ealing Broadway                         14    On time
## 12:25  London Paddington                       10A   On time
## 12:26  Didcot Parkway                          12    On time
## 12:28  Penzance                                7     On time
## 12:38  Basingstoke                             2     On time
## 12:41  Redhill                                 4     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       -     13:11
## 12:48  London Paddington                       10    On time
## 12:48  Oxford                                  9     On time
## 12:53  Reading                                 -     Cancelled
## 12:54  Ealing Broadway                         14    On time
## 12:55  Bristol Temple Meads                    9     On time
## 12:57  London Paddington                       11    On time
## 11:25  Staines                                 BUS   On time
## 11:26  Staines                                 BUS   On time
## 11:55  Staines                                 BUS   On time
## 11:56  Staines                                 BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 12:25  Staines                                 BUS   On time
## 12:26  Staines                                 BUS   On time
## 12:55  Staines                                 BUS   On time
## 12:56  Staines                                 BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
