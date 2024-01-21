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

## Example (Last rendered on 2024-01-21 07:07)

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
## Reading (RDG) Station Board on 2024-01-21 07:07:07.260637
## Time   From                                    Plat  Expected
## 07:18  London Paddington                       13    07:24
## 07:38  London Paddington                       13    07:53
## 07:46  Guildford                               5     On time
## 08:02  Staines                                 4     On time
## 08:08  London Paddington                       14    On time
## 08:17  London Paddington                       12    On time
## 08:26  London Paddington                       12B   On time
## 08:30  London Paddington                       15    On time
## 08:32  Staines                                 6     On time
## 08:40  London Paddington                       14    On time
## 08:48  Guildford                               -     Cancelled
## 08:54  London Waterloo                         4     On time
## 09:01  Bristol Temple Meads                    14A   On time
## 09:02  London Paddington                       15    On time
## 07:45  Heathrow Airport T3 (Bus)               BUS   On time
## 08:15  Heathrow Airport T3 (Bus)               BUS   On time
## 08:45  Heathrow Airport T3 (Bus)               BUS   On time
## 08:46  Basingstoke                             BUS   On time
## 08:55  Oxford                                  BUS   On time
## 09:00  Didcot Parkway                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-21 07:07:10.030419
## Time   To                                      Plat  Expected
## 07:21  Guildford                               -     Cancelled
## 07:42  London Paddington                       15A   On time
## 07:50  London Waterloo                         6     On time
## 07:53  London Paddington                       13    07:56
## 07:56  Guildford                               14A   On time
## 08:06  Newbury                                 12B   On time
## 08:21  Guildford                               5     On time
## 08:21  London Paddington                       15    On time
## 08:21  Penzance                                12    On time
## 08:23  London Paddington                       14    On time
## 08:24  London Waterloo                         4     On time
## 08:31  Swansea                                 12B   On time
## 08:34  Bedwyn                                  13    On time
## 08:50  London Waterloo                         6     On time
## 08:53  Ealing Broadway                         14    On time
## 08:56  Guildford                               5     On time
## 09:03  London Paddington                       14A   On time
## 07:25  Heathrow Airport T3 (Bus)               BUS   On time
## 07:37  Basingstoke                             BUS   On time
## 07:55  Heathrow Airport T3 (Bus)               BUS   On time
## 08:10  Didcot Parkway                          BUS   On time
## 08:25  Heathrow Airport T3 (Bus)               BUS   On time
## 08:30  Oxford                                  BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
