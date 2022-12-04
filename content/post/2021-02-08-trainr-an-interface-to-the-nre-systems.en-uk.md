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

## Example (Last rendered on 2022-12-04 10:04)

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
## Reading (RDG) Station Board on 2022-12-04 10:04:15
## Time   From                                    Plat  Expected
## 10:00  Didcot Parkway                          11    On time
## 10:00  London Paddington                       9     10:08
## 10:05  Southampton Central                     7     10:07
## 10:05  Worcester Foregate Street               10A   10:02
## 10:09  London Paddington                       14    On time
## 10:10  London Paddington                       8     10:13
## 10:10  Weston-super-Mare                       10    10:13
## 10:16  London Paddington                       9     On time
## 10:25  Swansea                                 11    Delayed
## 10:26  London Paddington                       7     On time
## 10:30  Bedwyn                                  13    10:36
## 10:33  Basingstoke                             2     On time
## 10:37  London Paddington                       9     On time
## 10:39  Birmingham New Street                   7     On time
## 10:40  London Paddington                       14    On time
## 10:41  Exeter St Davids                        11    On time
## 10:47  Salisbury                               1     On time
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:57  Great Malvern                           11    On time
## 10:59  London Paddington                       8     On time
## 11:01  London Paddington                       9     On time
## 11:06  Bournemouth                             8     On time
## 11:09  London Paddington                       14    On time
## 11:10  Didcot Parkway                          11    On time
## 11:10  London Paddington                       9     On time
## 11:14  Bristol Temple Meads                    10    On time
## 11:17  London Paddington                       9     On time
## 11:17  Swansea                                 11    On time
## 11:22  Bedwyn                                  1     On time
## 11:26  London Paddington                       8     On time
## 11:33  Basingstoke                             2     On time
## 11:35  Plymouth                                11    On time
## 11:39  London Paddington                       14    On time
## 11:39  Manchester Piccadilly                   8     On time
## 11:44  Swansea                                 10    On time
## 11:47  Salisbury                               1     On time
## 11:53  London Paddington                       9     On time
## 11:56  Great Malvern                           10    On time
## 11:58  Plymouth                                -     Cancelled
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:12  Ascot                                   BUS   On time
## 10:25  Ascot                                   BUS   On time
## 10:32  Guildford                               BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:40  Ascot                                   BUS   On time
## 10:55  Ascot                                   BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:10  Ascot                                   BUS   On time
## 11:18  Guildford                               BUS   On time
## 11:25  Ascot                                   BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 11:40  Ascot                                   BUS   On time
## 11:55  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-04 10:04:19
## Time   To                                      Plat  Expected
## 10:03  Swansea                                 9     10:09
## 10:07  London Paddington                       10A   On time
## 10:11  Hereford                                8     10:14
## 10:14  Ealing Broadway                         11    On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:18  London Paddington                       10    On time
## 10:26  Didcot Parkway                          9     On time
## 10:28  Plymouth                                7     On time
## 10:31  Ealing Broadway                         14    On time
## 10:35  London Paddington                       11    Delayed
## 10:38  Basingstoke                             2     On time
## 10:43  Newbury                                 15    On time
## 10:43  Swindon                                 9     On time
## 10:46  London Paddington                       11    On time
## 10:55  Weston-super-Mare                       9     On time
## 11:00  London Paddington                       10    On time
## 11:01  Ealing Broadway                         14    On time
## 11:01  Paignton                                8     On time
## 11:02  London Paddington                       11    On time
## 11:07  Swansea                                 9     On time
## 11:12  Great Malvern                           9     On time
## 11:12  Salisbury                               1     On time
## 11:14  Ealing Broadway                         11    On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:16  London Paddington                       10    On time
## 11:19  London Paddington                       11    On time
## 11:28  Didcot Parkway                          9     On time
## 11:28  Plymouth                                8     On time
## 11:31  Ealing Broadway                         14    On time
## 11:38  Basingstoke                             2     On time
## 11:42  London Paddington                       11    On time
## 11:43  Bedwyn                                  1     On time
## 11:45  London Paddington                       10    On time
## 11:52  Bournemouth                             8     On time
## 11:55  Bristol Temple Meads                    9     On time
## 12:00  London Paddington                       -     Cancelled
## 12:01  Ealing Broadway                         14    On time
## 12:02  London Paddington                       10    On time
## 10:12  Ascot                                   BUS   On time
## 10:28  Ascot                                   BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:42  Ascot                                   BUS   On time
## 10:45  Guildford                               BUS   On time
## 10:58  Ascot                                   BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:12  Ascot                                   BUS   On time
## 11:23  Guildford                               BUS   On time
## 11:28  Ascot                                   BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:42  Ascot                                   BUS   On time
## 11:56  Guildford                               BUS   On time
## 11:58  Ascot                                   BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
