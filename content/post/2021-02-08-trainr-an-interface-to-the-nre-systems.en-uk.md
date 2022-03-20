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

## Example (Last rendered on 2022-03-20 16:03)

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
## Reading (RDG) Station Board on 2022-03-20 16:03:45
## Time   From                                    Plat  Expected
## 15:57  Hereford                                10    On time
## 15:59  London Paddington                       8     On time
## 16:07  London Paddington                       9     On time
## 16:08  Redhill                                 6     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       9B    On time
## 16:13  London Paddington                       14    On time
## 16:15  London Paddington                       12    On time
## 16:23  London Paddington                       9     On time
## 16:24  Exeter St Davids                        11    On time
## 16:29  Oxford                                  10A   On time
## 16:32  Gloucester                              11A   On time
## 16:33  Basingstoke                             2     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  Manchester Piccadilly                   13    16:41
## 16:43  London Paddington                       14    On time
## 16:46  London Paddington                       9B    On time
## 16:47  Cardiff Central                         10    On time
## 16:47  Salisbury                               1     On time
## 16:53  London Paddington                       9     17:00
## 16:57  Great Malvern                           10A   On time
## 16:59  London Paddington                       9     On time
## 17:07  London Paddington                       9     On time
## 17:07  Southampton Central                     8     On time
## 17:08  Redhill                                 6     On time
## 17:10  Weston-super-Mare                       10    On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       9     On time
## 17:13  London Paddington                       14    On time
## 17:15  London Paddington                       12    On time
## 17:16  Penzance                                11    On time
## 17:23  London Paddington                       -     Cancelled
## 17:29  Oxford                                  10    On time
## 17:33  Basingstoke                             2     On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:43  London Paddington                       14    On time
## 17:45  Cardiff Central                         11    On time
## 17:45  London Paddington                       9     On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Hereford                                10    On time
## 16:26  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
## 16:50  Newbury                                 BUS   On time
## 16:56  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:17  Newbury                                 BUS   On time
## 17:26  Staines                                 BUS   On time
## 17:27  Staines                                 BUS   On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 17:56  Staines                                 BUS   On time
## 17:57  Bedwyn                                  BUS   On time
## 17:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-20 16:03:48
## Time   To                                      Plat  Expected
## 16:02  London Paddington                       10    On time
## 16:05  Penzance                                8     On time
## 16:09  Port Talbot Parkway                     9     On time
## 16:11  London Paddington                       10    On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15    On time
## 16:15  Hereford                                9B    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 16:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:22  Ealing Broadway                         14    On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:25  London Paddington                       11    On time
## 16:31  London Paddington                       10A   On time
## 16:34  London Paddington                       11A   On time
## 16:38  Basingstoke                             2     On time
## 16:41  Redhill                                 6     On time
## 16:47  Oxford                                  9B    On time
## 16:50  London Paddington                       10    On time
## 16:52  Ealing Broadway                         14    On time
## 16:55  Plymouth                                9     17:01
##        via Bristol                             
## 17:01  London Paddington                       10A   On time
## 17:05  Plymouth                                9     On time
## 17:09  Port Talbot Parkway                     9     On time
## 17:12  London Paddington                       10    On time
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           9     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 17:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:18  London Paddington                       11    On time
## 17:22  Ealing Broadway                         14    On time
## 17:25  Bristol Temple Meads                    -     Cancelled
## 17:25  Didcot Parkway                          12    On time
## 17:31  London Paddington                       10    On time
## 17:38  Basingstoke                             2     On time
## 17:41  Redhill                                 6     On time
## 17:45  London Paddington                       10    On time
## 17:48  Oxford                                  9     On time
## 17:50  London Paddington                       11    On time
## 17:52  Ealing Broadway                         14    On time
## 17:52  Southampton Central                     8B    On time
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Gloucester                              8     On time
## 18:01  London Paddington                       10    On time
## 16:25  Staines                                 BUS   On time
## 16:27  Staines                                 BUS   On time
## 16:35  Newbury                                 BUS   On time
## 16:40  Newbury                                 BUS   On time
## 16:55  Staines                                 BUS   On time
## 16:57  Staines                                 BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 17:25  Staines                                 BUS   On time
## 17:27  Staines                                 BUS   On time
## 17:35  Bedwyn                                  BUS   On time
## 17:55  Staines                                 BUS   On time
## 17:57  Staines                                 BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
