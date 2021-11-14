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

## Example (Last rendered on 2021-11-14 10:03)

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
## Reading (RDG) Station Board on 2021-11-14 10:03:45
## Time   From                                    Plat  Expected
## 09:58  Didcot Parkway                          10    On time
## 10:04  London Paddington                       9     On time
## 10:08  Eastleigh                               8     On time
## 10:12  London Paddington                       14    On time
## 10:12  London Paddington                       9     On time
## 10:14  Bedwyn                                  15    10:34
## 10:22  London Waterloo                         6     On time
## 10:23  London Paddington                       8     On time
## 10:26  London Paddington                       7     10:28
## 10:26  Swansea                                 11    On time
## 10:33  Basingstoke                             2     On time
## 10:37  Birmingham New Street                   8     On time
## 10:42  Exeter St Davids                        11    On time
## 10:44  London Paddington                       14    On time
## 10:50  London Paddington                       9     On time
## 10:52  London Waterloo                         4     On time
## 10:53  Bristol Parkway                         10    On time
## 10:57  Great Malvern                           11    On time
## 11:06  London Paddington                       9     On time
## 11:08  Eastleigh                               7     On time
## 11:10  Didcot Parkway                          10    On time
## 11:12  London Paddington                       9B    On time
## 11:12  London Paddington                       14    On time
## 11:15  Bristol Parkway                         11    On time
## 11:19  Bedwyn                                  1     On time
## 11:22  London Waterloo                         6     On time
## 11:23  London Paddington                       9     On time
## 11:26  London Paddington                       7     On time
## 11:33  Basingstoke                             2     On time
## 11:38  Manchester Piccadilly                   7     On time
## 11:43  Swansea                                 11    On time
## 11:44  London Paddington                       14    On time
## 11:50  London Paddington                       9     On time
## 11:52  London Waterloo                         4     On time
## 11:57  Plymouth                                11    On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 10:30  Guildford                               BUS   On time
## 11:13  Guildford                               BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
## 11:54  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-14 10:03:47
## Time   To                                      Plat  Expected
## 10:06  Carmarthen                              9     On time
## 10:11  Ealing Broadway                         10    On time
## 10:14  Hereford                                9     On time
## 10:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 10:21  London Waterloo                         4     On time
## 10:22  Ealing Broadway                         14    On time
## 10:28  Plymouth                                7     On time
## 10:30  Didcot Parkway                          8     On time
## 10:30  London Paddington                       11    On time
## 10:38  Basingstoke                             2     On time
## 10:44  Newbury                                 3     On time
## 10:45  London Paddington                       11    On time
## 10:51  London Waterloo                         6     On time
## 10:52  Ealing Broadway                         14    On time
## 10:55  Weston-super-Mare                       9     On time
## 11:00  London Paddington                       10    On time
## 11:05  London Paddington                       11    On time
## 11:09  Swansea                                 9     On time
## 11:12  Ealing Broadway                         10    On time
## 11:14  Great Malvern                           9B    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:17  London Paddington                       11    On time
## 11:21  London Waterloo                         4     On time
## 11:22  Ealing Broadway                         14    On time
## 11:27  Plymouth                                7     On time
## 11:30  Didcot Parkway                          9     On time
## 11:38  Basingstoke                             2     On time
## 11:44  Bedwyn                                  1     On time
## 11:46  London Paddington                       11    On time
## 11:51  London Waterloo                         6     On time
## 11:52  Ealing Broadway                         14    On time
## 11:52  Eastleigh                               7     On time
## 11:55  Exeter St Davids                        9     On time
##        via Bristol                             
## 12:00  London Paddington                       11    On time
## 10:05  Guildford                               BUS   On time
## 10:45  Guildford                               BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 11:30  Guildford                               BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
