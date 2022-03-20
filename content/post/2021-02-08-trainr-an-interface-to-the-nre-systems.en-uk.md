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

## Example (Last rendered on 2022-03-20 18:03)

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
## Reading (RDG) Station Board on 2022-03-20 18:03:54
## Time   From                                    Plat  Expected
## 17:56  London Paddington                       8B    18:02
## 17:57  Hereford                                10A   18:19
## 18:06  Plymouth                                10    18:15
## 18:07  London Paddington                       9     On time
## 18:08  Redhill                                 6     On time
## 18:12  London Paddington                       9     18:14
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       14    On time
## 18:15  London Paddington                       12    On time
## 18:21  Cardiff Central                         10    18:24
## 18:25  Plymouth                                11    On time
## 18:26  London Paddington                       8     On time
## 18:28  London Paddington                       9     On time
## 18:29  Oxford                                  10A   Delayed
## 18:33  Basingstoke                             2     On time
## 18:33  Gloucester                              11A   On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:43  London Paddington                       14    On time
## 18:44  Cardiff Central                         10    On time
## 18:44  London Paddington                       8     On time
## 18:53  London Paddington                       -     Cancelled
## 18:56  Great Malvern                           10    On time
## 19:07  London Paddington                       9     On time
## 19:09  Southampton Central                     7     On time
## 19:09  Taunton                                 10    On time
## 19:10  Redhill                                 15    On time
## 19:12  London Paddington                       9     On time
## 19:13  London Paddington                       13    On time
## 19:14  Didcot Parkway                          14    On time
## 19:15  London Paddington                       12    On time
## 19:17  Penzance                                11    On time
## 19:26  London Paddington                       8     On time
## 19:28  London Paddington                       9     On time
## 19:29  Oxford                                  10    On time
## 19:34  Basingstoke                             2     On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  London Paddington                       9     On time
## 19:39  Manchester Piccadilly                   7B    On time
## 19:43  London Paddington                       14    On time
## 19:47  London Paddington                       9     On time
## 19:48  Cardiff Central                         10    On time
## 19:53  London Paddington                       9     On time
## 19:55  Hereford                                10    On time
## 18:26  Staines                                 BUS   On time
## 18:27  Staines                                 BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
## 18:50  Newbury                                 BUS   On time
## 18:56  Staines                                 BUS   On time
## 18:57  Staines                                 BUS   On time
## 19:17  Newbury                                 BUS   On time
## 19:26  Staines                                 BUS   On time
## 19:27  Staines                                 BUS   On time
## 19:38  Heathrow Central Bus Stn                BUS   On time
## 19:55  Bedwyn                                  BUS   On time
## 19:56  Staines                                 BUS   On time
## 19:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-20 18:03:57
## Time   To                                      Plat  Expected
## 17:58  Gloucester                              8B    18:03
## 18:01  London Paddington                       10A   18:20
## 18:09  Port Talbot Parkway                     9     On time
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9     18:15
## 18:14  London Paddington                       10    18:16
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 18:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:22  Ealing Broadway                         14    On time
## 18:23  London Paddington                       10    18:25
## 18:25  Didcot Parkway                          12    On time
## 18:27  London Paddington                       11    On time
## 18:29  Penzance                                8     On time
## 18:30  London Paddington                       10A   Delayed
## 18:32  Plymouth                                9     On time
##        via Bristol                             
## 18:33  London Paddington                       11A   On time
## 18:39  Basingstoke                             2     On time
## 18:41  London Paddington                       11    On time
## 18:41  Redhill                                 6     On time
## 18:46  London Paddington                       10    On time
## 18:47  Oxford                                  8     On time
## 18:52  Ealing Broadway                         14    On time
## 18:55  Weston-super-Mare                       -     Cancelled
## 19:02  London Paddington                       10    On time
## 19:08  Port Talbot Parkway                     9     On time
## 19:11  London Paddington                       10    On time
## 19:14  Ealing Broadway                         14    On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 19:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:19  London Paddington                       11    On time
## 19:22  Ealing Broadway                         13    On time
## 19:25  Didcot Parkway                          12    On time
## 19:29  Plymouth                                8     On time
## 19:31  London Paddington                       10    On time
## 19:32  Bristol Temple Meads                    9     On time
## 19:38  Basingstoke                             2     On time
## 19:40  Swindon                                 9     On time
## 19:50  London Paddington                       10    On time
## 19:50  Oxford                                  9     On time
## 19:52  Bournemouth                             7B    On time
## 19:52  Ealing Broadway                         14    On time
## 19:55  Bristol Temple Meads                    9     On time
## 20:01  London Paddington                       10    On time
## 18:25  Staines                                 BUS   On time
## 18:27  Staines                                 BUS   On time
## 18:35  Newbury                                 BUS   On time
## 18:40  Newbury                                 BUS   On time
## 18:55  Staines                                 BUS   On time
## 18:57  Staines                                 BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 19:25  Staines                                 BUS   On time
## 19:27  Staines                                 BUS   On time
## 19:35  Bedwyn                                  BUS   On time
## 19:55  Staines                                 BUS   On time
## 19:57  Staines                                 BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
