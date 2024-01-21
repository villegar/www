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

## Example (Last rendered on 2024-01-21 13:05)

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
## Reading (RDG) Station Board on 2024-01-21 13:05:08.155746
## Time   From                                    Plat  Expected
## 12:53  Penzance                                11    13:20
## 12:58  Bournemouth                             7B    13:14
## 12:59  Great Malvern                           10A   13:12
## 13:00  London Paddington                       8B    13:14
## 13:07  London Paddington                       9     13:10
## 13:09  Bristol Temple Meads                    10    On time
## 13:11  Guildford                               5     On time
## 13:12  London Paddington                       14    On time
## 13:12  London Paddington                       8     13:17
## 13:14  Bristol Parkway                         11A   13:29
## 13:17  Bedwyn                                  1     13:22
## 13:22  Oxford                                  10A   On time
## 13:27  London Paddington                       7     On time
## 13:27  London Waterloo                         4     On time
## 13:34  Westbury                                11    13:50
## 13:35  Bristol Temple Meads                    10A   13:47
## 13:35  Didcot Parkway                          13    On time
## 13:39  Manchester Piccadilly                   12    On time
## 13:40  Guildford                               5     On time
## 13:42  London Paddington                       14    13:44
## 13:44  Swansea                                 10    On time
## 13:47  London Paddington                       13B   On time
## 13:47  London Paddington                       8B    On time
## 13:54  London Waterloo                         4     On time
## 13:58  Penzance                                11    14:10
## 13:59  Great Malvern                           10A   On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:11  Guildford                               5     On time
## 14:12  London Paddington                       14    On time
## 14:12  London Paddington                       8     On time
## 14:16  Swindon                                 11A   On time
## 14:19  Newbury                                 1     On time
## 14:22  Oxford                                  10    On time
## 14:27  London Paddington                       7     On time
## 14:27  London Waterloo                         4     On time
## 14:35  Didcot Parkway                          12    On time
## 14:38  Guildford                               5     On time
## 14:42  London Paddington                       14    On time
## 14:42  Manchester Piccadilly                   8B    On time
## 14:44  Carmarthen                              10    On time
## 14:47  London Paddington                       13    On time
## 14:51  London Paddington                       8     On time
## 14:54  London Paddington                       9     On time
## 14:54  London Waterloo                         4     On time
## 14:59  Worcester Foregate Street               10    On time
## 15:00  London Paddington                       7     On time
## 13:15  Heathrow Airport T3 (Bus)               BUS   On time
## 13:16  Bramley (Hampshire)                     BUS   On time
## 13:45  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Winchester                              BUS   On time
## 14:15  Heathrow Airport T3 (Bus)               BUS   On time
## 14:16  Bramley (Hampshire)                     BUS   On time
## 14:45  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-21 13:05:11.772467
## Time   To                                      Plat  Expected
## 13:02  London Paddington                       10A   13:13
## 13:02  Paignton                                8B    13:15
## 13:04  London Paddington                       11    13:21
## 13:10  Swansea                                 9     13:11
## 13:12  London Paddington                       10    On time
## 13:14  Hereford                                8     13:18
## 13:14  Manchester Piccadilly                   7B    13:15
##        via Coventry & Wilmslow                 
## 13:15  London Paddington                       11A   13:30
## 13:21  Guildford                               5     On time
## 13:24  London Waterloo                         4     On time
## 13:26  Didcot Parkway                          12A   On time
## 13:28  Plymouth                                7     On time
## 13:29  Ealing Broadway                         14    On time
## 13:29  London Paddington                       10A   On time
## 13:36  London Paddington                       10A   13:48
## 13:42  London Paddington                       11    13:51
## 13:43  Bedwyn                                  1     On time
## 13:48  Swindon                                 13B   On time
## 13:50  London Waterloo                         4     On time
## 13:52  Oxford                                  8B    On time
## 13:55  London Paddington                       10    On time
## 13:56  Bristol Temple Meads                    9B    On time
## 13:56  Guildford                               5     On time
## 13:59  Ealing Broadway                         14    On time
## 14:03  London Paddington                       10A   On time
## 14:06  London Paddington                       11    14:11
## 14:10  Carmarthen                              7B    On time
## 14:12  London Paddington                       10    On time
## 14:14  Great Malvern                           8     On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 14:17  London Paddington                       11A   On time
## 14:21  Guildford                               5     On time
## 14:24  London Waterloo                         4     On time
## 14:26  Didcot Parkway                          13A   On time
## 14:28  Penzance                                7     On time
## 14:29  Ealing Broadway                         14    On time
## 14:29  London Paddington                       10    On time
## 14:43  Newbury                                 1     On time
## 14:46  Bournemouth                             8B    On time
## 14:48  Cardiff Central                         13    On time
## 14:50  London Waterloo                         4     On time
## 14:52  Oxford                                  8     On time
## 14:55  London Paddington                       10    On time
## 14:56  Bristol Temple Meads                    9     On time
## 14:56  Guildford                               5     On time
## 14:59  Ealing Broadway                         14    On time
## 15:02  Exeter St Davids                        7     On time
## 15:03  London Paddington                       10    On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:37  Bramley (Hampshire)                     BUS   On time
## 13:52  Winchester                              BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:37  Bramley (Hampshire)                     BUS   On time
## 14:52  Winchester                              BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
