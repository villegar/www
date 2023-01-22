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

## Example (Last rendered on 2023-01-22 16:03)

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
## Reading (RDG) Station Board on 2023-01-22 16:03:08
## Time   From                                    Plat  Expected
## 15:56  Great Malvern                           10A   15:58
## 15:58  Exeter St Davids                        11    16:02
## 16:07  London Paddington                       9     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:12  London Paddington                       8B    16:14
## 16:12  Newbury                                 3     16:16
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       12    On time
## 16:24  London Paddington                       9     On time
## 16:27  London Paddington                       7     On time
## 16:28  Abbey Wood                              14    On time
## 16:32  Basingstoke                             2     On time
## 16:32  Gloucester                              10A   On time
## 16:39  Bath Spa                                11    On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:45  Swansea                                 10    On time
## 16:54  London Paddington                       9     On time
## 16:55  Hereford                                10    On time
## 16:57  London Paddington                       7     On time
## 16:58  Abbey Wood                              14    On time
## 16:58  Penzance                                11    On time
## 17:06  Bournemouth                             8     On time
## 17:07  London Paddington                       7     On time
## 17:09  Weston-super-Mare                       10    On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       12    On time
## 17:13  London Paddington                       9     On time
## 17:20  Bedwyn                                  3     On time
## 17:24  London Paddington                       9     On time
## 17:27  London Paddington                       7     On time
## 17:28  Abbey Wood                              14    On time
## 17:32  Basingstoke                             2     On time
## 17:36  Paignton                                10    On time
## 17:39  Bath Spa                                9     On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:44  Swansea                                 11    On time
## 17:54  London Paddington                       9     On time
## 17:57  Hereford                                10    On time
## 17:57  London Paddington                       8     On time
## 17:57  Plymouth                                11    On time
## 17:58  Abbey Wood                              14    On time
## 16:04  Guildford                               BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:06  Ascot                                   BUS   On time
## 16:21  Ascot                                   BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:36  Ascot                                   BUS   On time
## 16:40  Guildford                               BUS   On time
## 16:51  Ascot                                   BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:06  Ascot                                   BUS   On time
## 17:18  Guildford                               BUS   On time
## 17:21  Ascot                                   BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 17:36  Ascot                                   BUS   On time
## 17:51  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-22 16:03:12
## Time   To                                      Plat  Expected
## 16:00  London Paddington                       11    16:03
## 16:02  London Paddington                       10A   On time
## 16:10  Swansea                                 9     On time
## 16:14  Ealing Broadway                         15    On time
## 16:14  Hereford                                8B    16:15
## 16:15  London Paddington                       10    On time
## 16:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 16:23  Abbey Wood                              14    On time
## 16:25  Didcot Parkway                          12    On time
## 16:26  Bath Spa                                9     On time
## 16:28  Penzance                                7     On time
## 16:36  London Paddington                       10A   On time
## 16:37  Basingstoke                             2     On time
## 16:43  Newbury                                 3     On time
## 16:45  London Paddington                       11    On time
## 16:49  London Paddington                       10    On time
## 16:53  Abbey Wood                              14    On time
## 16:56  Plymouth                                9     On time
##        via Bristol                             
## 17:00  London Paddington                       11    On time
## 17:01  Plymouth                                7     On time
## 17:02  London Paddington                       10    On time
## 17:10  Swansea                                 7     On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           9     On time
## 17:15  London Paddington                       10    On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:23  Abbey Wood                              14    On time
## 17:25  Didcot Parkway                          12    On time
## 17:26  Bath Spa                                9     On time
## 17:28  Penzance                                7     On time
## 17:37  Basingstoke                             2     On time
## 17:43  Bedwyn                                  3     On time
## 17:45  London Paddington                       10    On time
## 17:49  London Paddington                       9     On time
## 17:52  Bournemouth                             8B    On time
## 17:53  Abbey Wood                              14    On time
## 17:55  London Paddington                       11    On time
## 17:56  Weston-super-Mare                       9     On time
## 18:00  Gloucester                              8     On time
## 18:00  London Paddington                       11    On time
## 18:02  London Paddington                       10    On time
## 16:16  Ascot                                   BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:31  Ascot                                   BUS   On time
## 16:45  Guildford                               BUS   On time
## 16:46  Ascot                                   BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:01  Ascot                                   BUS   On time
## 17:16  Ascot                                   BUS   On time
## 17:23  Guildford                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:31  Ascot                                   BUS   On time
## 17:46  Ascot                                   BUS   On time
## 17:56  Guildford                               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:01  Ascot                                   BUS   On time
```
