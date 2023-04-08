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

## Example (Last rendered on 2023-04-08 06:03)

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
## Reading (RDG) Station Board on 2023-04-08 06:03:38
## Time   From                                    Plat  Expected
## 07:03  Didcot Parkway                          15    On time
## 07:04  Gatwick Airport                         5     07:00
## 07:06  Southampton Central                     7B    08:51
## 07:08  London Paddington                       13    On time
## 07:11  Bristol Temple Meads                    10    On time
## 07:11  London Paddington                       8     On time
## 07:17  London Paddington                       -     Cancelled
## 07:20  London Waterloo                         4     On time
## 07:21  London Paddington                       14    On time
## 07:25  Didcot Parkway                          10A   On time
## 07:25  London Paddington                       8     On time
## 07:32  Didcot Parkway                          15    On time
## 07:33  London Paddington                       14    On time
## 07:33  Swindon                                 10    On time
## 07:40  Bristol Temple Meads                    10A   On time
## 07:43  London Paddington                       12    On time
## 07:43  London Waterloo                         5     On time
## 07:45  Swansea                                 10    On time
## 07:47  London Paddington                       7     On time
## 07:51  Gatwick Airport                         4     On time
## 07:51  London Paddington                       8B    On time
## 07:54  Great Malvern                           -     Cancelled
## 07:55  London Paddington                       8     On time
## 08:02  Didcot Parkway                          15    On time
## 08:03  London Paddington                       14    On time
## 08:08  London Paddington                       8     On time
## 08:10  Weston-super-Mare                       10    On time
## 08:12  London Paddington                       8     On time
## 08:13  London Paddington                       12    On time
## 08:13  London Waterloo                         4     On time
## 08:16  Swansea                                 11    On time
## 08:17  London Paddington                       -     Cancelled
## 08:25  London Paddington                       8     On time
## 08:28  Didcot Parkway                          11    On time
## 08:30  Cheltenham Spa                          11A   On time
## 08:32  Didcot Parkway                          15    On time
## 08:33  London Paddington                       14    On time
## 08:33  Redhill                                 5     On time
## 08:38  London Paddington                       9     On time
## 08:41  Bristol Temple Meads                    11    On time
## 08:43  London Paddington                       12    On time
## 08:43  London Waterloo                         6     On time
## 08:46  Swansea                                 10    On time
## 08:47  London Paddington                       9     On time
## 08:51  Gatwick Airport                         4     On time
## 08:52  London Paddington                       9     On time
## 08:54  Hereford                                -     Cancelled
## 08:55  London Paddington                       8     On time
## 08:56  Didcot Parkway                          7     On time
## 07:02  Newbury                                 BUS   On time
## 07:22  Bramley (Hampshire)                     BUS   On time
## 07:25  Heathrow Central Bus Stn                BUS   On time
## 07:30  Bedwyn                                  BUS   On time
## 07:57  Heathrow Central Bus Stn                BUS   On time
## 08:21  Bedwyn                                  BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:42  Newbury                                 BUS   On time
## 08:47  Basingstoke                             BUS   On time
## 08:55  Newbury                                 BUS   On time
## 09:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 06:03:45
## Time   To                                      Plat  Expected
## 07:09  London Waterloo                         6     On time
## 07:12  London Paddington                       10    On time
## 07:13  Swansea                                 8     On time
## 07:15  Didcot Parkway                          7B    08:52
## 07:15  Ealing Broadway                         15    On time
## 07:20  Great Malvern                           -     Cancelled
## 07:20  Redhill                                 5     On time
## 07:24  Ealing Broadway                         13    On time
## 07:26  Didcot Parkway                          14    On time
## 07:27  Bristol Temple Meads                    8     On time
## 07:27  London Paddington                       10A   On time
## 07:34  London Paddington                       10    On time
## 07:39  London Waterloo                         4     On time
## 07:42  London Paddington                       10A   On time
## 07:45  Ealing Broadway                         15    On time
## 07:47  London Paddington                       10    On time
## 07:50  Didcot Parkway                          7     On time
## 07:52  Ealing Broadway                         14    On time
## 07:53  Cheltenham Spa                          8B    On time
## 07:53  Didcot Parkway                          12    On time
## 07:57  Bristol Temple Meads                    8     On time
## 07:58  London Paddington                       -     Cancelled
## 08:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 08:06  Redhill                                 6     On time
## 08:09  London Waterloo                         5     On time
## 08:10  Penzance                                8     On time
## 08:14  Swansea                                 8     On time
## 08:15  Ealing Broadway                         15    On time
## 08:15  London Paddington                       10    On time
## 08:20  Great Malvern                           -     Cancelled
## 08:20  London Paddington                       11    On time
## 08:23  Didcot Parkway                          12    On time
## 08:24  Ealing Broadway                         14    On time
## 08:27  Bristol Temple Meads                    8     On time
## 08:29  London Paddington                       11    On time
## 08:33  London Paddington                       10    On time
## 08:35  London Paddington                       11A   On time
## 08:39  London Waterloo                         4     On time
## 08:40  Bristol Parkway                         9     On time
## 08:42  London Paddington                       11    On time
## 08:45  Ealing Broadway                         15    On time
## 08:48  London Paddington                       10    On time
## 08:49  Didcot Parkway                          9     On time
## 08:52  Didcot Parkway                          12    On time
## 08:54  Cheltenham Spa                          9     On time
## 08:54  Ealing Broadway                         14    On time
## 08:56  Bournemouth                             7     On time
## 08:57  London Paddington                       -     Cancelled
## 08:59  Taunton                                 8     On time
## 09:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 07:10  Newbury                                 BUS   On time
## 07:30  Heathrow Airport T3 (Bus)               BUS   On time
## 07:38  Bramley (Hampshire)                     BUS   On time
## 07:40  Bedwyn                                  BUS   On time
## 08:00  Basingstoke                             BUS   On time
## 08:00  Heathrow Airport T3 (Bus)               BUS   On time
## 08:10  Newbury                                 BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:38  Bramley (Hampshire)                     BUS   On time
## 08:40  Bedwyn                                  BUS   On time
## 08:44  Newbury                                 BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Winchester                              BUS   On time
```
