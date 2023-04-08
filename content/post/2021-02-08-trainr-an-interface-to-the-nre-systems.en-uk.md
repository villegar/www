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

## Example (Last rendered on 2023-04-08 04:03)

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
## Reading (RDG) Station Board on 2023-04-08 04:03:50
## Time   From                                    Plat  Expected
## 05:48  London Paddington                       8     On time
## 06:07  London Paddington                       14    On time
## 06:12  Didcot Parkway                          15    On time
## 06:13  Virginia Water                          4     On time
## 06:15  London Paddington                       12    On time
## 06:17  London Paddington                       -     Cancelled
## 06:32  Didcot Parkway                          15    On time
## 06:39  London Paddington                       14    On time
## 06:41  Bristol Temple Meads                    10    On time
## 06:43  London Waterloo                         6     On time
## 06:46  London Paddington                       8B    On time
## 06:47  London Paddington                       12    On time
## 06:48  Swansea                                 11    On time
## 06:53  London Paddington                       8     On time
## 06:55  Didcot Parkway                          10    On time
## 05:13  Heathrow Central Bus Stn                -     On time
## 06:13  Heathrow Central Bus Stn                -     On time
## 06:53  Bedwyn                                  BUS   On time
## 07:00  Basingstoke                             BUS   On time
## 07:02  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 04:03:54
## Time   To                                      Plat  Expected
## 05:09  London Waterloo                         5     On time
## 05:22  Redhill                                 14A   On time
## 05:39  London Waterloo                         6     On time
## 05:44  London Paddington                       15    On time
## 05:50  Didcot Parkway                          8     On time
## 05:54  London Paddington                       14    On time
## 05:55  Didcot Parkway                          13    On time
## 06:00  Gatwick Airport                         15    On time
##        via Guildford                           
## 06:09  London Waterloo                         5     On time
## 06:14  London Paddington                       15    On time
## 06:19  Didcot Parkway                          12    On time
## 06:19  Great Malvern                           -     Cancelled
## 06:19  Redhill                                 15A   On time
## 06:24  Ealing Broadway                         14    On time
## 06:35  London Paddington                       15    On time
## 06:39  London Waterloo                         4     On time
## 06:44  London Paddington                       10    On time
## 06:49  Didcot Parkway                          8B    On time
## 06:50  London Paddington                       11    On time
## 06:53  Didcot Parkway                          12    On time
## 06:54  Ealing Broadway                         14    On time
## 06:55  Bristol Temple Meads                    8     On time
## 06:58  London Paddington                       10    On time
## 07:01  Gatwick Airport                         13    On time
##        via Guildford                           
## 05:30  Heathrow Airport T3 (Bus)               BUS   On time
## 05:43  Basingstoke                             BUS   On time
## 05:43  Bedwyn                                  BUS   On time
## 06:00  Heathrow Airport T3 (Bus)               BUS   On time
## 06:10  Newbury                                 BUS   On time
## 06:30  Heathrow Airport T3 (Bus)               BUS   On time
## 06:34  Bedwyn                                  BUS   On time
## 06:40  Basingstoke                             BUS   On time
## 07:00  Heathrow Airport T3 (Bus)               BUS   On time
```
