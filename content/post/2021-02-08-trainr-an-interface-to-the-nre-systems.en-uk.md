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

## Example (Last rendered on 2024-01-27 05:06)

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
## Reading (RDG) Station Board on 2024-01-27 05:06:15.240411
## Time   From                                    Plat  Expected
## 05:49  London Paddington                       9     On time
## 06:09  Southampton Central                     12    On time
## 06:10  London Paddington                       14    On time
## 06:12  Didcot Parkway                          15    On time
## 06:15  London Paddington                       9     On time
## 06:17  Oxford                                  10    On time
## 06:18  London Paddington                       12    On time
## 06:40  Bristol Temple Meads                    10    On time
## 06:40  London Paddington                       14    On time
## 06:41  Didcot Parkway                          15    On time
## 06:44  London Paddington                       13    On time
## 06:45  London Paddington                       9     On time
## 06:46  Basingstoke                             2     On time
## 06:48  Swansea                                 10    On time
## 06:53  London Paddington                       9     On time
## 06:56  Bedwyn                                  13B   On time
## 06:56  Oxford                                  10    On time
## 05:05  Heathrow Airport T3 (Bus)               BUS   On time
## 05:35  Heathrow Airport T3 (Bus)               BUS   On time
## 06:00  Heathrow Airport T3 (Bus)               BUS   On time
## 06:12  Staines                                 BUS   On time
## 06:23  Bracknell                               BUS   On time
## 06:35  Heathrow Airport T3 (Bus)               BUS   On time
## 06:40  Bracknell                               BUS   On time
## 06:45  North Camp                              BUS   On time
## 06:53  Bracknell                               BUS   On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-27 05:06:17.6447
## Time   To                                      Plat  Expected
## 05:08  Bedwyn                                  13B   On time
## 05:39  Bedwyn                                  13B   On time
## 05:43  Basingstoke                             12    On time
## 05:43  London Paddington                       15    On time
## 05:50  Oxford                                  9     On time
## 05:55  Didcot Parkway                          13    On time
## 05:59  Abbey Wood                              14    On time
## 06:05  Basingstoke                             12    On time
## 06:12  Newbury                                 7     On time
## 06:13  London Paddington                       15    On time
## 06:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 06:19  Didcot Parkway                          12    On time
## 06:19  Great Malvern                           9     On time
## 06:20  London Paddington                       10    On time
## 06:29  Abbey Wood                              14    On time
## 06:34  Newbury                                 15B   On time
## 06:37  Basingstoke                             13A   On time
## 06:44  London Paddington                       10    On time
## 06:45  London Paddington                       15    On time
## 06:45  Newcastle                               8     On time
##        via Doncaster                           
## 06:49  Oxford                                  9     On time
## 06:50  London Paddington                       10    On time
## 06:52  Didcot Parkway                          13    On time
## 06:55  Bristol Temple Meads                    9     On time
## 06:58  London Paddington                       10    On time
## 06:59  Abbey Wood                              14    On time
## 05:08  Bracknell                               BUS   On time
## 05:08  North Camp                              BUS   On time
## 05:22  Bracknell                               BUS   On time
## 05:30  Heathrow Airport T3 (Bus)               BUS   On time
## 05:38  Bracknell                               BUS   On time
## 05:52  Bracknell                               BUS   On time
## 06:00  Heathrow Airport T3 (Bus)               BUS   On time
## 06:02  North Camp                              BUS   On time
## 06:08  Bracknell                               BUS   On time
## 06:22  Bracknell                               BUS   On time
## 06:25  Heathrow Airport T3 (Bus)               BUS   On time
## 06:38  Bracknell                               BUS   On time
## 06:52  Bracknell                               BUS   On time
## 06:52  North Camp                              BUS   On time
## 06:55  Heathrow Airport T3 (Bus)               BUS   On time
```
