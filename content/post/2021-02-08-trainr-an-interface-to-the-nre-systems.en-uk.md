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

## Example (Last rendered on 2021-05-02 06:12)

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
## Reading (RDG) Station Board on 2021-05-02 06:12:17
## Time   From                                    Plat  Expected
## 07:33  Gatwick Airport                         5     On time
## 07:52  London Paddington                       14    On time
## 08:28  London Paddington                       13    On time
## 08:33  Basingstoke                             2     On time
## 08:45  Salisbury                               1     On time
## 08:58  London Paddington                       7     On time
## 09:01  London Paddington                       9B    On time
## 07:55  Staines                                 BUS   On time
## 08:15  Staines                                 BUS   On time
## 08:25  Virginia Water                          BUS   On time
## 08:45  Virginia Water                          BUS   On time
## 08:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-02 06:12:19
## Time   To                                      Plat  Expected
## 07:38  Basingstoke                             13B   On time
## 07:39  Redhill                                 15A   On time
## 08:00  London Paddington                       13    On time
## 08:10  London Paddington                       15A   On time
## 08:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:27  London Paddington                       14    On time
## 08:30  Plymouth                                13    On time
## 08:38  Basingstoke                             2     On time
## 08:38  Didcot Parkway                          14    On time
## 08:39  Redhill                                 15A   On time
## 08:59  Ealing Broadway                         14    On time
## 09:00  Penzance                                7     On time
## 09:04  Swansea                                 9B    On time
## 07:26  Virginia Water                          BUS   On time
## 07:36  Virginia Water                          BUS   On time
## 07:45  Newbury                                 BUS   On time
## 07:56  Virginia Water                          BUS   On time
## 08:06  Virginia Water                          BUS   On time
## 08:26  Virginia Water                          BUS   On time
## 08:33  Bedwyn                                  BUS   On time
## 08:36  Virginia Water                          BUS   On time
## 08:56  Virginia Water                          BUS   On time
## 09:06  Virginia Water                          BUS   On time
```
