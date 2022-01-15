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

## Example (Last rendered on 2022-01-15 14:04)

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
## Reading (RDG) Station Board on 2022-01-15 14:04:46
## Time   From                                    Plat  Expected
## 13:59  Penzance                                10    On time
## 14:02  Didcot Parkway                          15    13:59
## 14:10  Didcot Parkway                          10    On time
## 14:11  Bedwyn                                  3     On time
## 14:11  London Waterloo                         5     14:18
## 14:13  London Paddington                       14    On time
## 14:17  London Paddington                       9B    14:24
## 14:18  London Paddington                       12    On time
## 14:20  Basingstoke                             2     On time
## 14:25  London Paddington                       9     On time
## 14:27  London Paddington                       7B    On time
## 14:28  Oxford                                  10A   On time
## 14:31  Didcot Parkway                          15A   On time
## 14:40  Manchester Piccadilly                   7     On time
## 14:41  London Waterloo                         6     On time
## 14:42  Newbury                                 1     On time
## 14:43  London Paddington                       14    On time
## 14:44  London Paddington                       12    On time
## 14:47  London Paddington                       9     On time
## 14:51  Basingstoke                             2     On time
## 14:51  London Paddington                       8     On time
## 14:53  Oxford                                  10    On time
## 14:54  Swansea                                 11    On time
## 14:59  London Paddington                       7B    On time
## 15:00  Penzance                                10    On time
## 15:01  Didcot Parkway                          15    On time
## 15:07  Bournemouth                             13B   On time
## 15:10  Bedwyn                                  3     On time
## 15:10  Didcot Parkway                          10    On time
## 15:11  London Waterloo                         4     Delayed
## 15:13  London Paddington                       14    On time
## 15:14  London Paddington                       12    On time
## 15:17  London Paddington                       9B    On time
## 15:20  Basingstoke                             2     On time
## 15:25  London Paddington                       9     On time
## 15:27  London Paddington                       7     On time
## 15:28  Oxford                                  10    On time
## 15:31  Didcot Parkway                          15    On time
## 15:40  Newbury                                 1     On time
## 15:41  London Waterloo                         6     On time
## 15:42  Exeter St Davids                        11    On time
## 15:43  London Paddington                       14    On time
## 15:44  London Paddington                       12    On time
## 15:47  London Paddington                       9     On time
## 15:51  Basingstoke                             2     On time
## 15:53  Hereford                                10A   On time
## 15:55  London Paddington                       7     On time
## 15:55  Swansea                                 11    On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 14:25  Swindon                                 BUS   On time
## 14:41  North Camp                              BUS   On time
## 14:55  Swindon                                 BUS   On time
## 14:58  North Camp                              BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
## 15:25  Swindon                                 BUS   On time
## 15:41  North Camp                              BUS   On time
## 15:55  Swindon                                 BUS   On time
## 15:58  North Camp                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-15 14:04:51
## Time   To                                      Plat  Expected
## 14:05  London Paddington                       10    On time
## 14:07  Basingstoke                             2     On time
## 14:11  London Paddington                       10    On time
## 14:12  London Waterloo                         6     On time
## 14:12  Newbury                                 1     On time
## 14:15  Ealing Broadway                         15    On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Great Malvern                           9B    14:25
## 14:22  Ealing Broadway                         14    On time
## 14:24  Didcot Parkway                          12    On time
## 14:27  Didcot Parkway                          9     On time
## 14:29  Penzance                                7B    On time
## 14:30  London Paddington                       10A   On time
## 14:37  Basingstoke                             -     On time
## 14:42  London Waterloo                         5     On time
## 14:43  Bedwyn                                  3     On time
## 14:45  Ealing Broadway                         15A   On time
## 14:49  Oxford                                  9     On time
## 14:52  Bournemouth                             7     On time
## 14:52  Ealing Broadway                         14    On time
## 14:53  Didcot Parkway                          12    On time
## 14:55  Swansea                                 8     On time
## 14:56  London Paddington                       10    On time
## 15:00  London Paddington                       11    On time
## 15:01  Plymouth                                7B    On time
## 15:05  London Paddington                       10    On time
## 15:07  Basingstoke                             2     On time
## 15:11  London Paddington                       10    On time
## 15:12  London Waterloo                         6     On time
## 15:12  Newbury                                 1     On time
## 15:15  Ealing Broadway                         15    On time
## 15:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Great Malvern                           9B    On time
## 15:22  Ealing Broadway                         14    On time
## 15:24  Didcot Parkway                          12    On time
## 15:27  Didcot Parkway                          9     On time
## 15:29  Penzance                                7     On time
## 15:30  London Paddington                       10    On time
## 15:37  Basingstoke                             2     On time
## 15:42  London Waterloo                         4     On time
## 15:44  Bedwyn                                  3     On time
## 15:45  Ealing Broadway                         15    On time
## 15:46  London Paddington                       11    On time
## 15:49  Oxford                                  9     On time
## 15:52  Ealing Broadway                         14    On time
## 15:53  Didcot Parkway                          12    On time
## 15:57  Swansea                                 7     On time
## 15:58  London Paddington                       10A   On time
## 16:00  London Paddington                       11    On time
## 14:10  Swindon                                 BUS   On time
## 14:23  North Camp                              BUS   On time
## 14:40  Swindon                                 BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:00  North Camp                              BUS   On time
## 15:10  Swindon                                 BUS   On time
## 15:23  North Camp                              BUS   On time
## 15:40  Swindon                                 BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 16:00  North Camp                              BUS   On time
```
