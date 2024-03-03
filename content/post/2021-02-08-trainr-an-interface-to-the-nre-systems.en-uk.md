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

## Example (Last rendered on 2024-03-03 11:06)

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
## Reading (RDG) Station Board on 2024-03-03 11:06:06.622269
## Time   From                                    Plat  Expected
## 10:57  Great Malvern                           11    11:04
## 11:00  London Paddington                       9     11:04
## 11:02  Cardiff Central                         10    On time
## 11:06  Bournemouth                             8     11:03
## 11:09  Bristol Temple Meads                    11    11:11
## 11:12  London Paddington                       14    On time
## 11:12  London Paddington                       9     On time
## 11:19  Bedwyn                                  1     On time
## 11:27  London Paddington                       7     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Didcot Parkway                          12    On time
## 11:35  Plymouth                                11    On time
## 11:39  Manchester Piccadilly                   7B    On time
## 11:42  Abbey Wood                              14    On time
## 11:47  London Paddington                       13    On time
## 11:47  Salisbury                               2     On time
## 11:49  Cardiff Central                         11A   On time
## 11:54  London Paddington                       8     On time
## 11:57  Great Malvern                           10A   On time
## 11:58  Plymouth                                11    On time
## 12:01  London Paddington                       9     On time
## 12:05  Bournemouth                             13B   On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:12  Abbey Wood                              14    On time
## 12:12  London Paddington                       8     On time
## 12:14  Swindon                                 11    On time
## 12:19  Newbury                                 1     On time
## 12:27  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          11A   On time
## 12:32  Basingstoke                             2     On time
## 12:35  Didcot Parkway                          12    On time
## 12:40  Manchester Piccadilly                   7B    On time
## 12:42  Abbey Wood                              14    On time
## 12:47  London Paddington                       13    On time
## 12:47  Salisbury                               2     On time
## 12:49  Cardiff Central                         11    On time
## 12:53  Plymouth                                13    On time
## 12:54  London Paddington                       8     On time
## 12:57  Great Malvern                           10A   On time
## 12:57  London Paddington                       7     On time
## 13:00  London Paddington                       9     On time
## 11:09  Bracknell                               BUS   On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:27  Bracknell                               BUS   On time
## 11:32  North Camp                              BUS   On time
## 11:39  Bracknell                               BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:57  Bracknell                               BUS   On time
## 12:09  Bracknell                               BUS   On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:20  North Camp                              BUS   On time
## 12:27  Bracknell                               BUS   On time
## 12:37  North Camp                              BUS   On time
## 12:39  Bracknell                               BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 12:57  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-03 11:06:10.647013
## Time   To                                      Plat  Expected
## 11:03  London Paddington                       11    11:06
## 11:05  Cardiff Central                         9     On time
## 11:06  London Paddington                       10    On time
## 11:12  London Paddington                       11    On time
## 11:12  Salisbury                               2     On time
## 11:14  Great Malvern                           9     On time
## 11:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:15  London Paddington                       15A   On time
## 11:26  Didcot Parkway                          12A   On time
## 11:28  Plymouth                                7     On time
## 11:29  Abbey Wood                              14    On time
## 11:36  London Paddington                       11    On time
## 11:37  Basingstoke                             2     On time
## 11:43  Bedwyn                                  1     On time
## 11:48  Swindon                                 13    On time
## 11:52  Bournemouth                             7B    On time
## 11:55  London Paddington                       11A   On time
## 11:56  Bristol Temple Meads                    8     On time
## 11:59  Abbey Wood                              14    On time
## 12:02  London Paddington                       10A   On time
## 12:04  London Paddington                       11    On time
## 12:05  Cardiff Central                         9     On time
## 12:12  London Paddington                       10    On time
## 12:12  Salisbury                               2     On time
## 12:14  Hereford                                8     On time
## 12:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 12:15  London Paddington                       11    On time
## 12:26  Didcot Parkway                          12    On time
## 12:28  Plymouth                                7     On time
## 12:29  Abbey Wood                              14    On time
## 12:36  London Paddington                       11A   On time
## 12:37  Basingstoke                             2     On time
## 12:43  Newbury                                 1     On time
## 12:48  Swindon                                 13    On time
## 12:52  Bournemouth                             7B    On time
## 12:55  London Paddington                       11    On time
## 12:56  Weston-super-Mare                       8     On time
## 12:59  Abbey Wood                              14    On time
## 13:01  Paignton                                7     On time
## 13:02  London Paddington                       10A   On time
## 13:04  London Paddington                       13    On time
## 13:05  Cardiff Central                         9     On time
## 11:07  Bracknell                               BUS   On time
## 11:23  Bracknell                               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:32  North Camp                              BUS   On time
## 11:37  Bracknell                               BUS   On time
## 11:53  Bracknell                               BUS   On time
## 11:55  North Camp                              BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:07  Bracknell                               BUS   On time
## 12:23  Bracknell                               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:37  Bracknell                               BUS   On time
## 12:38  North Camp                              BUS   On time
## 12:53  Bracknell                               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
