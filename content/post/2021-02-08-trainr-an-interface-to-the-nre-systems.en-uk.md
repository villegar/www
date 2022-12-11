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

## Example (Last rendered on 2022-12-11 08:03)

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
## Reading (RDG) Station Board on 2022-12-11 08:03:48
## Time   From                                    Plat  Expected
## 08:02  Ascot                                   4     On time
## 08:06  London Paddington                       14    08:08
## 08:22  London Paddington                       13    On time
## 08:27  Guildford                               5     On time
## 08:27  London Paddington                       13B   On time
## 08:32  Ascot                                   6     On time
## 08:32  Basingstoke                             2     On time
## 08:37  London Paddington                       9     On time
## 08:40  London Paddington                       14    On time
## 08:54  Bristol Temple Meads                    15    On time
## 08:57  London Paddington                       12B   On time
## 09:02  Ascot                                   4     On time
## 09:03  London Paddington                       14    On time
## 09:06  London Paddington                       12    On time
## 09:08  Didcot Parkway                          15A   On time
## 09:10  London Paddington                       7     On time
## 09:15  London Paddington                       12    On time
## 09:15  Newbury                                 3     On time
## 09:23  Salisbury                               2     On time
## 09:28  London Paddington                       7     On time
## 09:29  Oxford                                  15    On time
## 09:32  Basingstoke                             2     On time
## 09:33  Ascot                                   4     On time
## 09:33  London Paddington                       14    On time
## 09:37  Bristol Parkway                         15    On time
## 09:39  Guildford                               5     On time
## 09:45  London Paddington                       9     On time
## 09:56  London Paddington                       9     On time
## 09:57  Worcester Foregate Street               10A   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-11 08:03:52
## Time   To                                      Plat  Expected
## 08:06  Newbury                                 12B   On time
## 08:11  London Paddington                       13A   On time
## 08:21  Guildford                               15A   On time
## 08:24  Ascot                                   4     On time
## 08:24  London Paddington                       14    On time
## 08:24  Penzance                                13    On time
## 08:28  Didcot Parkway                          13B   On time
## 08:34  Bedwyn                                  12B   On time
## 08:37  Basingstoke                             2     On time
## 08:38  Exeter St Davids                        9     On time
##        via Bristol                             
## 08:40  Guildford                               5     On time
## 08:54  Abbey Wood                              14    On time
## 08:54  Ascot                                   6     On time
## 08:57  London Paddington                       15    On time
## 08:59  Swansea                                 12B   On time
## 09:10  Ealing Broadway                         15A   On time
## 09:11  Great Malvern                           12    On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Didcot Parkway                          12    On time
## 09:18  Penzance                                7     On time
## 09:21  Guildford                               13    On time
## 09:24  Abbey Wood                              14    On time
## 09:24  Ascot                                   4     On time
## 09:28  Salisbury                               2     On time
## 09:29  Weston-super-Mare                       7     On time
## 09:31  London Paddington                       15    On time
## 09:37  Basingstoke                             2     On time
## 09:41  Guildford                               6     On time
## 09:43  Bedwyn                                  1     On time
## 09:43  London Paddington                       15    On time
## 09:48  Oxford                                  9     On time
## 09:52  Southampton Central                     8     On time
## 09:54  Abbey Wood                              14    On time
## 09:54  Ascot                                   4     On time
## 09:58  Swansea                                 9     On time
## 10:00  London Paddington                       10A   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
```
