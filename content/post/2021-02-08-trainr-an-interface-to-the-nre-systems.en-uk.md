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

## Example (Last rendered on 2022-01-15 18:08)

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
## Reading (RDG) Station Board on 2022-01-15 18:08:06
## Time   From                                    Plat  Expected
## 17:33  London Paddington                       7B    18:10
## 18:01  Didcot Parkway                          14    On time
## 18:10  Didcot Parkway                          11    On time
## 18:11  Bedwyn                                  3     On time
## 18:11  London Waterloo                         5     18:18
## 18:13  London Paddington                       13    18:06
## 18:14  London Paddington                       12    On time
## 18:17  London Paddington                       9     On time
## 18:21  Basingstoke                             2     On time
## 18:25  London Paddington                       9     On time
## 18:27  London Paddington                       7     On time
## 18:28  Oxford                                  10A   On time
## 18:31  Didcot Parkway                          15    On time
## 18:41  London Waterloo                         6     On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       14    On time
## 18:44  London Paddington                       12    On time
## 18:47  London Paddington                       9B    On time
## 18:50  Basingstoke                             2     On time
## 18:54  Great Malvern                           10A   On time
## 18:54  Swansea                                 11    On time
## 18:55  London Paddington                       7     On time
## 18:59  Penzance                                10    On time
## 19:01  Didcot Parkway                          15    On time
## 19:07  Bournemouth                             13B   On time
## 19:10  Bedwyn                                  3     On time
## 19:10  Didcot Parkway                          10    On time
## 19:11  London Waterloo                         5     On time
## 19:13  London Paddington                       14    On time
## 19:14  London Paddington                       12    On time
## 19:17  London Paddington                       9     On time
## 19:22  Basingstoke                             2     On time
## 19:25  Bristol Temple Meads                    11    On time
## 19:25  London Paddington                       9     On time
## 19:27  London Paddington                       7     On time
## 19:28  Oxford                                  10    On time
## 19:31  Didcot Parkway                          15    On time
## 19:40  Manchester Piccadilly                   13    On time
## 19:40  Newbury                                 1     On time
## 19:41  London Waterloo                         4     On time
## 19:43  London Paddington                       14    On time
## 19:44  London Paddington                       12    On time
## 19:47  London Paddington                       9B    On time
## 19:51  Basingstoke                             2     On time
## 19:54  Great Malvern                           10A   On time
## 19:55  Bedwyn                                  3     On time
## 19:55  London Paddington                       7B    On time
## 20:02  Plymouth                                11    On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 18:25  Swindon                                 BUS   On time
## 18:41  North Camp                              BUS   On time
## 18:55  Swindon                                 BUS   On time
## 18:58  North Camp                              BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 19:25  Swindon                                 BUS   On time
## 19:41  North Camp                              BUS   On time
## 19:55  Swindon                                 BUS   On time
## 19:58  North Camp                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-15 18:08:09
## Time   To                                      Plat  Expected
## 17:35  Weston-super-Mare                       7B    18:11
## 18:08  Newbury                                 1     On time
## 18:11  London Paddington                       11    On time
## 18:12  Basingstoke                             2     On time
## 18:12  London Waterloo                         6     On time
## 18:13  Ealing Broadway                         14    On time
## 18:19  Worcester Foregate Street               9     On time
## 18:22  Ealing Broadway                         13    On time
## 18:23  Didcot Parkway                          12    On time
## 18:27  Didcot Parkway                          9     On time
## 18:29  Penzance                                7     On time
## 18:30  London Paddington                       10A   On time
## 18:37  Basingstoke                             2     On time
## 18:42  London Waterloo                         5     On time
## 18:45  Ealing Broadway                         15    On time
## 18:47  Bedwyn                                  3     On time
## 18:49  Oxford                                  9B    On time
## 18:52  Bournemouth                             7     On time
## 18:52  Ealing Broadway                         14    On time
## 18:53  Didcot Parkway                          12    On time
## 18:56  London Paddington                       10A   On time
## 18:59  London Paddington                       11    On time
## 19:01  Swansea                                 7     On time
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       10    On time
## 19:10  Newbury                                 1     On time
## 19:11  London Paddington                       10    On time
## 19:12  London Waterloo                         6     On time
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 19:19  Hereford                                9     On time
## 19:22  Ealing Broadway                         14    On time
## 19:23  Didcot Parkway                          12    On time
## 19:27  Didcot Parkway                          9     On time
## 19:27  London Paddington                       11    On time
## 19:29  Plymouth                                7     On time
## 19:30  London Paddington                       10    On time
## 19:37  Basingstoke                             2     On time
## 19:42  London Waterloo                         5     On time
## 19:45  Bedwyn                                  3     On time
## 19:45  Ealing Broadway                         15    On time
## 19:49  Oxford                                  9B    On time
## 19:52  Ealing Broadway                         14    On time
## 19:53  Didcot Parkway                          12    On time
## 19:56  London Paddington                       10A   On time
## 19:57  Swansea                                 7B    On time
## 20:03  London Paddington                       11    On time
## 20:05  Basingstoke                             2     On time
## 18:10  Swindon                                 BUS   On time
## 18:23  North Camp                              BUS   On time
## 18:40  Swindon                                 BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 19:09  North Camp                              BUS   On time
## 19:10  Swindon                                 BUS   On time
## 19:32  North Camp                              BUS   On time
## 19:40  Swindon                                 BUS   On time
## 19:50  North Camp                              BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
