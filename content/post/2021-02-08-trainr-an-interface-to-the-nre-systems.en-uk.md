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

## Example (Last rendered on 2023-01-29 08:03)

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
## Reading (RDG) Station Board on 2023-01-29 08:03:58
## Time   From                                    Plat  Expected
## 08:06  London Paddington                       14    On time
## 08:15  London Paddington                       8     On time
## 08:23  London Paddington                       7     On time
## 08:38  London Paddington                       9     On time
## 08:42  London Paddington                       14    On time
## 08:54  Bristol Temple Meads                    11    On time
## 08:56  London Paddington                       14    On time
## 08:58  London Paddington                       7     On time
## 09:00  Salisbury                               1     On time
## 09:09  London Paddington                       7B    On time
## 09:11  Didcot Parkway                          15    On time
## 09:12  London Paddington                       10    On time
## 09:14  London Paddington                       13    On time
## 09:19  Newbury                                 15    On time
## 09:23  London Paddington                       7     On time
## 09:23  Swindon                                 11    On time
## 09:26  London Paddington                       14    On time
## 09:29  Oxford                                  15    On time
## 09:37  Basingstoke                             1     On time
## 09:37  Bristol Parkway                         10    On time
## 09:47  London Paddington                       9     On time
## 09:47  Salisbury                               1     On time
## 09:56  London Paddington                       14    On time
## 09:57  Worcester Foregate Street               10    On time
## 09:58  London Paddington                       7     On time
## 08:03  Staines                                 BUS   On time
## 08:18  North Camp                              BUS   On time
## 08:19  Bracknell                               BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:33  Bracknell                               BUS   On time
## 08:49  Bracknell                               BUS   On time
## 08:58  Basingstoke                             BUS   On time
## 09:03  Bracknell                               BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:15  North Camp                              BUS   On time
## 09:19  Bracknell                               BUS   On time
## 09:33  Bracknell                               BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:49  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-29 08:04:01
## Time   To                                      Plat  Expected
## 08:11  London Paddington                       13    On time
## 08:20  Penzance                                8     On time
## 08:22  London Paddington                       14    On time
## 08:40  Exeter St Davids                        9     On time
##        via Bristol                             
## 08:46  Didcot Parkway                          7     On time
## 08:50  Basingstoke                             12B   On time
## 08:52  Abbey Wood                              14    On time
## 08:57  London Paddington                       11    On time
## 09:00  Cardiff Central                         7     On time
## 09:11  Great Malvern                           7B    On time
## 09:12  Ealing Broadway                         15    On time
## 09:12  Salisbury                               1     On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 09:18  Didcot Parkway                          13    On time
## 09:18  Penzance                                10    On time
## 09:22  Abbey Wood                              14    On time
## 09:27  London Paddington                       11    On time
## 09:31  London Paddington                       15    On time
## 09:35  Weston-super-Mare                       7     On time
## 09:37  Basingstoke                             12B   On time
## 09:43  Bedwyn                                  1     On time
## 09:43  London Paddington                       10    On time
## 09:50  Oxford                                  9     On time
## 09:52  Abbey Wood                              14    On time
## 09:52  Bournemouth                             8     On time
## 10:00  Cardiff Central                         7     On time
## 10:02  London Paddington                       10    On time
## 08:05  Bracknell                               BUS   On time
## 08:21  Bracknell                               BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:35  Bracknell                               BUS   On time
## 08:40  North Camp                              BUS   On time
## 08:51  Bracknell                               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:05  Bracknell                               BUS   On time
## 09:21  Bracknell                               BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:30  North Camp                              BUS   On time
## 09:35  Bracknell                               BUS   On time
## 09:45  North Camp                              BUS   On time
## 09:51  Bracknell                               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
```
