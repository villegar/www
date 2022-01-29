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

## Example (Last rendered on 2022-01-29 10:03)

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
## Reading (RDG) Station Board on 2022-01-29 10:03:56
## Time   From                                    Plat  Expected
## 10:00  Plymouth                                10    10:14
## 10:01  Didcot Parkway                          15    09:59
## 10:10  Didcot Parkway                          10    On time
## 10:11  Bedwyn                                  3     On time
## 10:13  London Paddington                       14    On time
## 10:14  London Paddington                       12    On time
## 10:14  Worcester Foregate Street               11A   On time
## 10:16  Staines                                 5     10:33
## 10:17  London Paddington                       9B    On time
## 10:20  Basingstoke                             2     On time
## 10:25  London Paddington                       9     On time
## 10:27  London Paddington                       7     On time
## 10:31  Didcot Parkway                          15    On time
## 10:33  Redhill                                 4     On time
## 10:35  Oxford                                  8A    On time
## 10:41  Birmingham New Street                   7     On time
## 10:41  London Waterloo                         6     On time
## 10:42  Newbury                                 1     On time
## 10:43  London Paddington                       14    On time
## 10:44  London Paddington                       12    On time
## 10:47  London Paddington                       9     On time
## 10:50  Basingstoke                             2     On time
## 10:51  Gatwick Airport                         5     On time
## 10:51  London Paddington                       8     On time
## 10:53  Swansea                                 11    On time
## 10:54  Great Malvern                           10A   On time
## 10:58  London Paddington                       7     On time
## 11:01  Didcot Parkway                          15    On time
## 11:01  Penzance                                11A   On time
## 11:05  Bournemouth                             13B   On time
## 11:10  Didcot Parkway                          10    On time
## 11:10  Newbury                                 3     On time
## 11:12  London Waterloo                         4     On time
## 11:13  London Paddington                       14    On time
## 11:14  London Paddington                       12    On time
## 11:17  London Paddington                       9B    On time
## 11:25  London Paddington                       9     On time
## 11:27  London Paddington                       7     On time
## 11:28  Basingstoke                             2     On time
## 11:31  Didcot Parkway                          15    On time
## 11:33  Oxford                                  10A   On time
## 11:33  Redhill                                 5     On time
## 11:39  Manchester Piccadilly                   13    On time
## 11:41  Newbury                                 1     On time
## 11:42  London Waterloo                         6     On time
## 11:43  London Paddington                       14    On time
## 11:43  Paignton                                11    On time
## 11:44  London Paddington                       12    On time
## 11:47  London Paddington                       9B    On time
## 11:51  Gatwick Airport                         4     On time
## 11:54  Great Malvern                           10A   On time
## 11:56  Basingstoke                             2     On time
## 11:58  Carmarthen                              11    On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 10:25  Swindon                                 BUS   On time
## 10:55  Swindon                                 BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
## 11:25  Swindon                                 BUS   On time
## 11:55  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-29 10:04:01
## Time   To                                      Plat  Expected
## 10:05  London Paddington                       10    10:15
## 10:07  Basingstoke                             2     On time
## 10:11  London Paddington                       10    On time
## 10:12  London Waterloo                         6     On time
## 10:12  Newbury                                 1     On time
## 10:15  Ealing Broadway                         15    On time
## 10:15  London Paddington                       11A   On time
## 10:19  Hereford                                9B    On time
## 10:20  Redhill                                 4     On time
## 10:22  Ealing Broadway                         14    On time
## 10:23  Didcot Parkway                          12    On time
## 10:27  Didcot Parkway                          9     On time
## 10:30  Penzance                                7     On time
## 10:36  London Paddington                       8A    On time
## 10:38  Basingstoke                             2     On time
## 10:42  London Waterloo                         5     On time
## 10:43  Bedwyn                                  3     On time
## 10:45  Ealing Broadway                         15    On time
## 10:49  Oxford                                  9     On time
## 10:51  Bournemouth                             7     On time
## 10:52  Didcot Parkway                          12    On time
## 10:52  Ealing Broadway                         14    On time
## 10:54  Swansea                                 8     On time
## 10:56  London Paddington                       10A   On time
## 10:58  London Paddington                       11    On time
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:01  Paignton                                7     On time
## 11:05  Basingstoke                             2     On time
## 11:05  London Paddington                       11A   On time
## 11:10  Newbury                                 1     On time
## 11:11  London Paddington                       10    On time
## 11:12  London Waterloo                         6     On time
## 11:15  Ealing Broadway                         15    On time
## 11:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Great Malvern                           9B    On time
## 11:20  Redhill                                 5     On time
## 11:22  Ealing Broadway                         14    On time
## 11:23  Didcot Parkway                          12    On time
## 11:27  Didcot Parkway                          9     On time
## 11:30  Plymouth                                7     On time
## 11:35  London Paddington                       10A   On time
## 11:38  Basingstoke                             2     On time
## 11:42  London Waterloo                         4     On time
## 11:45  Bedwyn                                  3     On time
## 11:45  Ealing Broadway                         15    On time
## 11:45  London Paddington                       11    On time
## 11:49  Oxford                                  9B    On time
## 11:52  Ealing Broadway                         14    On time
## 11:54  Didcot Parkway                          12    On time
## 11:57  London Paddington                       10A   On time
## 11:59  London Paddington                       11    On time
## 12:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:10  Swindon                                 BUS   On time
## 10:40  Swindon                                 BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 11:10  Swindon                                 BUS   On time
## 11:40  Swindon                                 BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
