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

## Example (Last rendered on 2022-06-19 08:04)

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
## Reading (RDG) Station Board on 2022-06-19 08:04:04
## Time   From                                    Plat  Expected
## 09:05  London Paddington                       8B    On time
## 09:10  Didcot Parkway                          15A   09:12
## 09:10  Swindon                                 9     On time
## 09:12  London Paddington                       12B   On time
## 09:14  London Paddington                       8     On time
## 09:22  Newbury                                 15    On time
## 09:23  London Paddington                       9     On time
## 09:33  Clapham Junction                        4     On time
## 09:33  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    10    On time
## 09:40  Gatwick Airport                         13    On time
## 09:44  Bristol Parkway                         10    09:46
## 09:47  Oxford                                  10    On time
## 09:47  Salisbury                               1     On time
## 09:50  London Paddington                       8     On time
## 09:57  Worcester Foregate Street               10A   On time
## 09:58  Didcot Parkway                          15    On time
## 10:03  London Paddington                       14    On time
## 10:03  London Waterloo                         4     10:27
## 10:05  Southampton Central                     12B   On time
## 10:08  Redhill                                 6     On time
## 10:09  Weston-super-Mare                       10    On time
## 10:10  London Paddington                       9     On time
## 10:16  London Paddington                       13B   On time
## 10:26  London Paddington                       7     On time
## 10:30  Bedwyn                                  13    On time
## 10:31  London Paddington                       9     On time
## 10:33  Basingstoke                             2     On time
## 10:33  London Paddington                       14    On time
## 10:33  London Waterloo                         4     On time
## 10:38  Gatwick Airport                         5     On time
## 10:39  Birmingham New Street                   13    On time
## 10:41  Exeter St Davids                        11    On time
## 10:43  Swansea                                 10    On time
## 10:47  Salisbury                               1     On time
## 10:50  London Paddington                       9     On time
## 10:53  London Paddington                       8     On time
## 10:57  Great Malvern                           11    On time
## 10:59  London Paddington                       7     On time
## 11:03  London Waterloo                         4     On time
## 09:18  Basingstoke                             BUS   On time
## 09:45  Heathrow Central Bus Stn                BUS   On time
## 10:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-19 08:04:09
## Time   To                                      Plat  Expected
## 09:10  Great Malvern                           8B    On time
## 09:11  London Paddington                       9     On time
## 09:12  Ealing Broadway                         15A   09:13
## 09:12  Salisbury                               1     On time
## 09:15  Manchester Piccadilly                   7B    On time
##        via Stoke-on-Trent                      
## 09:18  Didcot Parkway                          12B   On time
## 09:18  Plymouth                                8     On time
## 09:20  Gatwick Airport                         13A   On time
##        via Guildford                           
## 09:24  London Waterloo                         4     On time
## 09:29  Ealing Broadway                         14    On time
## 09:29  Weston-super-Mare                       9     On time
## 09:38  Basingstoke                             12B   On time
## 09:41  London Paddington                       10    On time
## 09:41  Redhill                                 13    On time
## 09:44  Bedwyn                                  12B   On time
## 09:47  London Paddington                       10    On time
## 09:52  Bournemouth                             7B    On time
## 09:52  Carmarthen                              8     On time
## 09:54  London Waterloo                         4     On time
## 09:59  Ealing Broadway                         14A   On time
## 09:59  London Paddington                       10A   On time
## 10:11  Hereford                                9     On time
## 10:11  London Paddington                       10    On time
## 10:12  Salisbury                               1     On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Stoke-on-Trent                      
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:24  London Waterloo                         4     10:30
## 10:26  Didcot Parkway                          13B   On time
## 10:28  Plymouth                                7     On time
## 10:29  Ealing Broadway                         14A   On time
## 10:38  Basingstoke                             2     On time
## 10:40  Swindon                                 9     On time
## 10:41  Redhill                                 6     On time
## 10:43  Newbury                                 13B   On time
## 10:44  London Paddington                       11    On time
## 10:46  London Paddington                       10    On time
## 10:52  Swansea                                 9     On time
## 10:54  London Waterloo                         4     On time
## 10:56  Weston-super-Mare                       8     On time
## 10:59  London Paddington                       11    On time
## 11:01  Ealing Broadway                         14A   On time
## 11:01  Paignton                                7     On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
