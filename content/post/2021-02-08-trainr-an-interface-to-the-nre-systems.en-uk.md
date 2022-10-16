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

## Example (Last rendered on 2022-10-16 06:09)

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
## Reading (RDG) Station Board on 2022-10-16 06:09:27
## Time   From                                    Plat  Expected
## 07:28  Southall                                13    07:39
## 07:43  Southall                                14    Delayed
## 07:49  Redhill                                 5     08:17
## 08:06  Ealing Broadway                         14    On time
## 08:20  London Paddington                       12    On time
## 08:27  Ealing Broadway                         13    On time
## 08:33  Basingstoke                             2     On time
## 08:37  London Paddington                       7     On time
## 08:44  Salisbury                               1     On time
## 08:47  London Paddington                       14    On time
## 08:58  London Paddington                       9B    On time
## 09:03  London Paddington                       14    On time
## 09:04  Didcot Parkway                          15    On time
## 07:25  Heathrow Central Bus Stn                BUS   On time
## 07:56  Staines                                 BUS   On time
## 07:57  Heathrow Central Bus Stn                BUS   On time
## 08:26  Staines                                 BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:45  Staines                                 BUS   On time
## 08:56  Staines                                 BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-16 06:09:32
## Time   To                                      Plat  Expected
## 07:10  London Paddington                       14A   On time
## 07:38  Basingstoke                             12B   On time
## 07:39  Redhill                                 15A   On time
## 07:54  London Paddington                       14    On time
## 08:06  Newbury                                 12B   On time
## 08:11  London Paddington                       13    On time
## 08:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:22  Penzance                                12    On time
## 08:24  London Paddington                       14    On time
## 08:29  Didcot Parkway                          13    On time
## 08:34  Bedwyn                                  15    On time
## 08:38  Basingstoke                             2     On time
## 08:39  Exeter St Davids                        7     On time
##        via Bristol                             
## 08:40  Redhill                                 15    On time
## 08:54  Ealing Broadway                         14    On time
## 09:01  Swansea                                 9B    On time
## 09:06  Ealing Broadway                         15    On time
## 07:26  Staines                                 BUS   On time
## 07:30  Heathrow Airport T3 (Bus)               BUS   On time
## 07:50  Staines                                 BUS   On time
## 07:57  Staines                                 BUS   On time
## 08:00  Heathrow Airport T3 (Bus)               BUS   On time
## 08:25  Staines                                 BUS   On time
## 08:27  Staines                                 BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:55  Staines                                 BUS   On time
## 08:57  Staines                                 BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
