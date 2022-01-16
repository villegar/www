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

## Example (Last rendered on 2022-01-16 08:04)

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
## Reading (RDG) Station Board on 2022-01-16 08:04:03
## Time   From                                    Plat  Expected
## 07:55  London Paddington                       12    08:12
## 08:17  London Paddington                       7     On time
## 08:23  London Paddington                       13    On time
## 08:25  London Paddington                       12B   On time
## 08:34  Basingstoke                             2     On time
## 08:44  Salisbury                               1     On time
## 08:59  Didcot Parkway                          15    On time
## 09:00  London Paddington                       7     On time
## 09:03  London Paddington                       14    On time
## 09:07  London Paddington                       13    On time
## 09:10  Didcot Parkway                          15    On time
## 09:14  London Paddington                       12    On time
## 09:15  London Paddington                       7     On time
## 09:25  Oxford                                  15    On time
## 09:26  Newbury                                 2     On time
## 09:31  London Paddington                       7     On time
## 09:33  Basingstoke                             1     On time
## 09:42  London Paddington                       14    On time
## 09:47  Salisbury                               1     On time
## 09:49  Bristol Temple Meads                    11    On time
## 10:00  Worcester Foregate Street               14    On time
## 08:14  Bracknell                               BUS   On time
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 08:30  Bracknell                               BUS   On time
## 08:32  Guildford                               BUS   On time
## 08:44  Bracknell                               BUS   On time
## 09:00  Bracknell                               BUS   On time
## 09:14  Bracknell                               BUS   On time
## 09:18  Swindon                                 BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
## 09:30  Bracknell                               BUS   On time
## 09:44  Bracknell                               BUS   On time
## 09:44  Guildford                               BUS   On time
## 09:50  Swindon                                 BUS   On time
## 10:00  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-16 08:04:05
## Time   To                                      Plat  Expected
## 08:04  Exeter St Davids                        12    08:15
##        via Bristol                             
## 08:07  Newbury                                 13B   On time
## 08:10  London Paddington                       15    On time
## 08:22  Penzance                                7     On time
## 08:25  London Paddington                       14    On time
## 08:27  Swansea                                 12B   On time
## 08:34  Bedwyn                                  14B   On time
## 08:38  Basingstoke                             2     On time
## 08:38  Didcot Parkway                          13    On time
## 08:55  Ealing Broadway                         14    On time
## 09:00  London Paddington                       15    On time
## 09:07  Weston-super-Mare                       7     On time
## 09:10  Ealing Broadway                         15    On time
## 09:10  Great Malvern                           13    On time
## 09:12  Salisbury                               1     On time
## 09:15  Oxford                                  8     On time
## 09:18  Didcot Parkway                          12    On time
## 09:18  Plymouth                                7     On time
## 09:27  Ealing Broadway                         14    On time
## 09:30  London Paddington                       15    On time
## 09:33  Carmarthen                              7     On time
## 09:38  Basingstoke                             1     On time
## 09:44  Bedwyn                                  7B    On time
## 09:50  London Paddington                       11    On time
## 09:52  Bournemouth                             8     On time
## 09:57  Ealing Broadway                         14    On time
## 10:03  London Paddington                       14    On time
## 08:06  Bracknell                               BUS   On time
## 08:20  Swindon                                 BUS   On time
## 08:21  Bracknell                               BUS   On time
## 08:35  Guildford                               BUS   On time
## 08:36  Bracknell                               BUS   On time
## 08:50  Swindon                                 BUS   On time
## 08:51  Bracknell                               BUS   On time
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 09:06  Bracknell                               BUS   On time
## 09:08  Guildford                               BUS   On time
## 09:20  Swindon                                 BUS   On time
## 09:21  Bracknell                               BUS   On time
## 09:36  Bracknell                               BUS   On time
## 09:46  Guildford                               BUS   On time
## 09:51  Bracknell                               BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
