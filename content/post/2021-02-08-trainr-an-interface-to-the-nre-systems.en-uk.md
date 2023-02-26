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

## Example (Last rendered on 2023-02-26 10:03)

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
## Reading (RDG) Station Board on 2023-02-26 10:03:15
## Time   From                                    Plat  Expected
## 09:57  London Paddington                       7     10:03
## 09:57  Worcester Foregate Street               10A   10:02
## 09:58  Didcot Parkway                          14    On time
## 10:06  Southampton Central                     12B   On time
## 10:09  Weston-super-Mare                       10    10:16
## 10:12  London Paddington                       9     10:16
## 10:16  London Paddington                       13    10:20
## 10:25  Swansea                                 11    On time
## 10:26  London Paddington                       14    10:33
## 10:32  Basingstoke                             2     On time
## 10:39  Birmingham New Street                   13    On time
## 10:42  London Paddington                       9     On time
## 10:45  Exeter St Davids                        11A   On time
## 10:53  Bristol Parkway                         10    On time
## 10:54  London Paddington                       8     On time
## 10:56  Great Malvern                           11    On time
## 10:56  London Paddington                       14    On time
## 11:06  Southampton Central                     7     On time
## 11:09  Bristol Temple Meads                    10    On time
## 11:09  London Paddington                       8     On time
## 11:10  Didcot Parkway                          14    On time
## 11:12  London Paddington                       9     On time
## 11:15  London Paddington                       12    On time
## 11:15  Swansea                                 11    On time
## 11:27  Abbey Wood                              14    On time
## 11:33  Basingstoke                             2     On time
## 11:39  Manchester Piccadilly                   7     On time
## 11:48  Swansea                                 11    On time
## 11:51  Plymouth                                10    12:05
## 11:54  London Paddington                       8     On time
## 11:56  Abbey Wood                              14    On time
## 11:56  Great Malvern                           11A   On time
## 10:03  Bracknell                               BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:19  Bracknell                               BUS   On time
## 10:32  Guildford                               BUS   On time
## 10:33  Bracknell                               BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:49  Bracknell                               BUS   On time
## 11:03  Bedwyn                                  BUS   On time
## 11:03  Bracknell                               BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:18  Guildford                               BUS   On time
## 11:19  Bracknell                               BUS   On time
## 11:33  Bracknell                               BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 11:49  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-26 10:03:19
## Time   To                                      Plat  Expected
## 09:58  Swansea                                 7     10:04
## 10:02  London Paddington                       10A   10:03
## 10:13  London Paddington                       10    10:17
## 10:14  Ealing Broadway                         14    On time
## 10:14  Hereford                                9     10:17
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:22  Abbey Wood                              15    On time
## 10:26  Didcot Parkway                          13    On time
## 10:28  London Paddington                       11    On time
## 10:37  Basingstoke                             2     On time
## 10:43  Bristol Parkway                         9     On time
## 10:50  London Paddington                       11A   On time
## 10:52  Abbey Wood                              15    On time
## 10:55  Weston-super-Mare                       8     On time
## 11:00  London Paddington                       10    On time
## 11:02  London Paddington                       11    On time
## 11:03  Plymouth                                9     On time
## 11:10  Swansea                                 8     On time
## 11:13  London Paddington                       10    On time
## 11:14  Ealing Broadway                         14    On time
## 11:14  Great Malvern                           9     On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:20  London Paddington                       11    On time
## 11:22  Abbey Wood                              15    On time
## 11:26  Didcot Parkway                          12    On time
## 11:37  Basingstoke                             2     On time
## 11:50  London Paddington                       11    On time
## 11:52  Abbey Wood                              15    On time
## 11:52  Southampton Central                     7     On time
## 11:55  Bristol Temple Meads                    8     On time
## 11:58  London Paddington                       10    12:06
## 12:02  London Paddington                       11A   On time
## 10:05  Bracknell                               BUS   On time
## 10:21  Bracknell                               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:35  Bracknell                               BUS   On time
## 10:43  Newbury                                 BUS   On time
## 10:45  Guildford                               BUS   On time
## 10:51  Bracknell                               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:05  Bracknell                               BUS   On time
## 11:21  Bracknell                               BUS   On time
## 11:23  Guildford                               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:35  Bracknell                               BUS   On time
## 11:43  Bedwyn                                  BUS   On time
## 11:51  Bracknell                               BUS   On time
## 11:56  Guildford                               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
