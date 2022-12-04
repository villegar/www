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

## Example (Last rendered on 2022-12-04 18:03)

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
## Reading (RDG) Station Board on 2022-12-04 18:03:46
## Time   From                                    Plat  Expected
## 17:53  London Paddington                       9     18:02
## 17:57  Hereford                                12    18:05
## 17:57  Plymouth                                11    18:01
## 17:59  London Paddington                       9     18:08
## 18:01  London Paddington                       8     18:12
## 18:09  London Paddington                       14    On time
## 18:10  Didcot Parkway                          15    18:18
## 18:10  London Paddington                       9     18:18
## 18:14  Bristol Temple Meads                    12    18:18
## 18:16  London Paddington                       8     18:19
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7     On time
## 18:33  Basingstoke                             2     On time
## 18:34  Cheltenham Spa                          13    On time
## 18:39  London Paddington                       14    18:47
## 18:39  Manchester Piccadilly                   7     On time
## 18:41  Bristol Temple Meads                    15    On time
## 18:42  London Paddington                       8     On time
## 18:45  Swansea                                 12    On time
## 18:53  London Paddington                       9     On time
## 18:58  Liskeard                                11    On time
## 18:59  London Paddington                       8     On time
## 19:00  Great Malvern                           12    On time
## 19:01  London Paddington                       9     On time
## 19:05  Bournemouth                             8     On time
## 19:09  London Paddington                       14    On time
## 19:10  Didcot Parkway                          15    On time
## 19:12  London Paddington                       9     On time
## 19:13  London Paddington                       13    On time
## 19:14  Taunton                                 12    On time
## 19:21  Bedwyn                                  1     On time
## 19:23  London Paddington                       9     On time
## 19:26  London Paddington                       8     On time
## 19:34  Basingstoke                             2     On time
## 19:39  London Paddington                       14    On time
## 19:39  Manchester Piccadilly                   8     On time
## 19:40  Paignton                                11    On time
## 19:49  Swansea                                 12    On time
## 19:53  London Paddington                       9     On time
## 19:56  Hereford                                12    On time
## 19:57  Plymouth                                11    On time
## 18:04  Guildford                               BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:10  Ascot                                   BUS   On time
## 18:25  Ascot                                   BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:40  Ascot                                   BUS   On time
## 18:40  Guildford                               BUS   On time
## 18:55  Ascot                                   BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:10  Ascot                                   BUS   On time
## 19:18  Guildford                               BUS   On time
## 19:25  Ascot                                   BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:40  Ascot                                   BUS   On time
## 19:55  Ascot                                   BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-04 18:03:52
## Time   To                                      Plat  Expected
## 17:55  Weston-super-Mare                       9     18:03
## 18:00  Cheltenham Spa                          9     18:09
## 18:00  London Paddington                       11    18:02
## 18:02  London Paddington                       12    18:06
## 18:07  Swansea                                 8     18:13
## 18:12  Great Malvern                           9     18:19
## 18:14  Ealing Broadway                         15    18:19
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:16  London Paddington                       12    18:19
## 18:25  Bristol Temple Meads                    9     On time
## 18:28  Didcot Parkway                          8     On time
## 18:28  Plymouth                                7     On time
## 18:31  Ealing Broadway                         14    On time
## 18:38  Basingstoke                             2     On time
## 18:42  London Paddington                       13    On time
## 18:43  Newbury                                 1     On time
## 18:46  London Paddington                       15    On time
## 18:48  London Paddington                       12    On time
## 18:48  Oxford                                  8     On time
## 18:55  Weston-super-Mare                       9     On time
## 19:00  London Paddington                       11    On time
## 19:01  Ealing Broadway                         14    On time
## 19:01  Plymouth                                8     On time
## 19:02  London Paddington                       12    On time
## 19:09  Swansea                                 9     On time
## 19:14  Ealing Broadway                         15    On time
## 19:14  Hereford                                9     On time
## 19:15  London Paddington                       12    On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:25  Bristol Temple Meads                    9     On time
## 19:28  Didcot Parkway                          13    On time
## 19:28  Plymouth                                8     On time
## 19:31  Ealing Broadway                         14    On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       11    On time
## 19:43  Bedwyn                                  1     On time
## 19:50  London Paddington                       12    On time
## 19:52  Bournemouth                             8     On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:59  Ealing Broadway                         14    On time
## 20:00  London Paddington                       11    On time
## 20:02  London Paddington                       12    On time
## 18:12  Ascot                                   BUS   On time
## 18:28  Ascot                                   BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:42  Ascot                                   BUS   On time
## 18:45  Guildford                               BUS   On time
## 18:58  Ascot                                   BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:12  Ascot                                   BUS   On time
## 19:28  Ascot                                   BUS   On time
## 19:30  Guildford                               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:42  Ascot                                   BUS   On time
## 19:58  Ascot                                   BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
