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

## Example (Last rendered on 2021-10-03 18:03)

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
## Reading (RDG) Station Board on 2021-10-03 18:03:27
## Time   From                                    Plat  Expected
## 18:55  Great Malvern                           10A   19:04
## 18:58  London Paddington                       7     19:00
## 19:02  Bournemouth                             8     19:17
## 19:06  Paignton                                -     Cancelled
## 19:07  London Paddington                       9     On time
## 19:12  London Paddington                       9     On time
## 19:12  Redhill                                 15    On time
## 19:13  London Paddington                       13    On time
## 19:14  Didcot Parkway                          14A   On time
## 19:15  London Paddington                       12B   On time
## 19:17  Penzance                                11    19:31
## 19:19  Bedwyn                                  1     On time
## 19:27  London Paddington                       9     On time
## 19:34  Basingstoke                             2     On time
## 19:38  Gatwick Airport                         5     19:43
## 19:39  Manchester Piccadilly                   12    On time
## 19:40  Castle Cary                             11A   On time
## 19:40  Swindon                                 10A   On time
## 19:43  London Paddington                       14    On time
## 19:44  London Paddington                       9     On time
## 19:48  Carmarthen                              10    On time
## 19:53  London Paddington                       9     On time
## 19:57  Worcester Foregate Street               10    On time
## 20:07  London Paddington                       8     On time
## 20:12  London Paddington                       9B    On time
## 20:12  Redhill                                 15    On time
## 20:13  Didcot Parkway                          13A   On time
## 20:13  London Paddington                       14    On time
## 20:18  London Paddington                       13B   On time
## 20:18  Penzance                                -     Delayed
## 20:18  Penzance                                11    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:33  Basingstoke                             2     On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:43  London Paddington                       14    On time
## 20:49  Swansea                                 10    On time
## 20:53  London Paddington                       9     On time
## 20:57  Great Malvern                           10    On time
## 19:15  Virginia Water                          BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 19:26  Virginia Water                          BUS   On time
## 19:45  Virginia Water                          BUS   On time
## 19:56  Virginia Water                          BUS   On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 20:15  Virginia Water                          BUS   On time
## 20:26  Virginia Water                          BUS   On time
## 20:45  Virginia Water                          BUS   On time
## 20:56  Virginia Water                          BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-03 18:03:32
## Time   To                                      Plat  Expected
## 18:59  London Paddington                       10A   19:07
## 19:00  Castle Cary                             7     19:01
## 19:09  Bristol Parkway                         9     On time
## 19:11  London Paddington                       -     Cancelled
## 19:14  Ealing Broadway                         14A   On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   8     19:18
##        via Coventry & Wilmslow                 
## 19:18  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:18  London Paddington                       11    19:32
## 19:22  Ealing Broadway                         13    On time
## 19:25  Didcot Parkway                          12B   On time
## 19:30  Plymouth                                9     On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       11A   On time
## 19:44  Bedwyn                                  1     On time
## 19:45  London Paddington                       10A   On time
## 19:47  Oxford                                  9     On time
## 19:50  London Paddington                       10    On time
## 19:52  Ealing Broadway                         14    On time
## 19:54  Swindon                                 9     On time
## 20:01  London Paddington                       10    On time
## 20:09  Swansea                                 8     On time
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         13A   On time
## 20:14  Great Malvern                           9B    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 20:20  London Paddington                       -     Delayed
## 20:20  London Paddington                       11    On time
## 20:22  Ealing Broadway                         14    On time
## 20:25  Didcot Parkway                          13B   On time
## 20:33  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:42  Newbury                                 1     On time
## 20:46  Southampton Central                     8     On time
## 20:50  London Paddington                       10    On time
## 20:52  Ealing Broadway                         14    On time
## 20:54  Swindon                                 9     On time
## 20:59  London Paddington                       10    On time
## 19:05  Virginia Water                          BUS   On time
## 19:25  Virginia Water                          BUS   On time
## 19:35  Virginia Water                          BUS   On time
## 19:52  Winchester                              BUS   On time
## 19:55  Virginia Water                          BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 20:05  Virginia Water                          BUS   On time
## 20:25  Virginia Water                          BUS   On time
## 20:35  Virginia Water                          BUS   On time
## 20:52  Winchester                              BUS   On time
## 20:55  Virginia Water                          BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
