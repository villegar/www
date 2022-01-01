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

## Example (Last rendered on 2022-01-01 06:03)

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
## Reading (RDG) Station Board on 2022-01-01 06:03:27
## Time   From                                    Plat  Expected
## 06:11  Didcot Parkway                          15    On time
## 06:13  London Paddington                       14    On time
## 06:18  London Paddington                       12B   On time
## 06:34  Didcot Parkway                          15    On time
## 06:41  Bristol Temple Meads                    10    On time
## 06:43  London Paddington                       13    On time
## 06:46  London Paddington                       12B   On time
## 06:47  London Paddington                       9B    On time
## 06:53  London Paddington                       9     On time
## 06:55  Oxford                                  10A   On time
## 07:03  Didcot Parkway                          12    On time
## 07:11  Bristol Parkway                         10    On time
## 07:11  London Paddington                       8     On time
## 07:13  London Paddington                       14    On time
## 07:17  London Paddington                       9B    On time
## 07:23  London Paddington                       12B   On time
## 07:25  London Paddington                       9     On time
## 07:25  Oxford                                  10A   On time
## 07:32  Didcot Parkway                          15    On time
## 07:32  London Paddington                       7B    On time
## 07:33  Swindon                                 10    On time
## 07:38  Newbury                                 1     On time
## 07:40  Bristol Temple Meads                    10    On time
## 07:43  London Paddington                       14    On time
## 07:45  Swansea                                 10    On time
## 07:46  London Paddington                       12    On time
## 07:47  London Paddington                       9B    On time
## 07:51  London Paddington                       8B    On time
## 07:55  London Paddington                       9     On time
## 07:57  Basingstoke                             2     On time
## 06:03  Heathrow Central Bus Stn                -     On time
## 07:11  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-01 06:03:30
## Time   To                                      Plat  Expected
## 06:12  Newbury                                 13B   On time
## 06:14  London Paddington                       15    On time
## 06:19  Didcot Parkway                          12B   On time
## 06:19  Redhill                                 15A   On time
## 06:22  Ealing Broadway                         14    On time
## 06:34  Bedwyn                                  7B    On time
## 06:36  London Paddington                       15    On time
## 06:37  Basingstoke                             13    On time
## 06:42  London Paddington                       10    On time
## 06:49  Oxford                                  9B    On time
## 06:52  Ealing Broadway                         13    On time
## 06:55  Bristol Temple Meads                    9     On time
## 06:56  Didcot Parkway                          12B   On time
## 06:58  London Paddington                       10A   On time
## 07:01  Gatwick Airport                         14A   On time
##        via Guildford                           
## 07:07  Basingstoke                             15B   On time
## 07:12  London Paddington                       10    On time
## 07:12  Newbury                                 7B    On time
## 07:13  Swansea                                 8     On time
## 07:14  Ealing Broadway                         12    On time
## 07:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 07:20  Great Malvern                           9B    On time
## 07:20  Redhill                                 5     On time
## 07:26  Didcot Parkway                          12B   On time
## 07:26  London Paddington                       10A   On time
## 07:27  Bristol Temple Meads                    9     On time
## 07:29  Ealing Broadway                         14    On time
## 07:32  Basingstoke                             8B    On time
## 07:34  London Paddington                       10    On time
## 07:35  Bedwyn                                  7B    On time
## 07:42  London Paddington                       10    On time
## 07:45  Ealing Broadway                         15    On time
## 07:47  London Paddington                       10    On time
## 07:50  Oxford                                  9B    On time
## 07:53  Cheltenham Spa                          8B    On time
## 07:53  Didcot Parkway                          12    On time
## 07:54  London Waterloo                         6     On time
## 07:57  Bristol Temple Meads                    9     On time
## 07:59  Ealing Broadway                         14    On time
## 08:01  Gatwick Airport                         13    On time
##        via Guildford                           
## 08:02  Newbury                                 1     On time
## 07:00  Heathrow Central Bus Stn                BUS   On time
## 08:00  Heathrow Central Bus Stn                BUS   On time
```
