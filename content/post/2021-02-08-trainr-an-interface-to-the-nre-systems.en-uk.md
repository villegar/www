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

## Example (Last rendered on 2021-03-06 18:11)

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
## Reading (RDG) Station Board on 2021-03-06 18:11:12
## Time   From                                    Plat  Expected
## 17:48  Port Talbot Parkway                     -     Delayed
## 18:01  Didcot Parkway                          -     On time
## 18:11  London Paddington                       -     Delayed
## 18:13  London Paddington                       -     18:08
## 18:17  London Paddington                       -     On time
## 18:17  Plymouth                                -     On time
## 18:26  London Paddington                       -     On time
## 18:27  Bedwyn                                  -     On time
## 18:32  London Paddington                       -     On time
## 18:33  Redhill                                 -     On time
## 18:33  Swindon                                 -     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:41  Manchester Piccadilly                   -     On time
## 18:42  Newbury                                 -     On time
## 18:43  London Paddington                       -     On time
## 18:44  London Paddington                       -     On time
## 18:46  Port Talbot Parkway                     -     Cancelled
## 18:53  London Paddington                       -     On time
## 18:54  Great Malvern                           -     On time
## 18:56  London Paddington                       -     Cancelled
## 18:57  Basingstoke                             -     On time
## 19:01  Didcot Parkway                          -     On time
## 19:08  Bournemouth                             -     On time
## 19:11  London Paddington                       -     On time
## 19:13  London Paddington                       -     On time
## 19:16  London Paddington                       -     On time
## 19:17  Penzance                                -     On time
## 19:27  Bedwyn                                  -     On time
## 19:33  Redhill                                 -     On time
## 19:37  London Paddington                       -     On time
## 19:38  Newbury                                 -     On time
## 19:39  Manchester Piccadilly                   -     On time
## 19:40  Bristol Temple Meads                    -     On time
## 19:43  London Paddington                       -     On time
## 19:44  London Paddington                       -     On time
## 19:46  Port Talbot Parkway                     -     Delayed
## 19:53  London Paddington                       -     On time
## 19:54  Great Malvern                           -     On time
## 19:56  London Paddington                       -     On time
## 19:57  Basingstoke                             -     On time
## 18:12  Ascot                                   -     On time
## 18:27  Ascot                                   -     On time
## 18:42  Ascot                                   -     On time
## 18:57  Ascot                                   -     On time
## 19:12  Ascot                                   -     On time
## 19:27  Ascot                                   -     On time
## 19:42  Ascot                                   -     On time
## 19:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 18:11:14
## Time   To                                      Plat  Expected
## 17:50  London Paddington                       -     Delayed
## 18:10  Newbury                                 -     On time
## 18:13  Ealing Broadway                         -     On time
## 18:13  Port Talbot Parkway                     -     Delayed
## 18:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 18:19  London Paddington                       -     On time
## 18:19  Worcester Foregate Street               -     On time
## 18:22  Ealing Broadway                         -     On time
## 18:28  Penzance                                -     On time
## 18:30  London Paddington                       -     On time
## 18:34  Bedwyn                                  -     On time
## 18:35  London Paddington                       -     On time
## 18:36  Redhill                                 -     On time
## 18:42  London Paddington                       -     On time
## 18:49  Bournemouth                             -     On time
## 18:50  London Paddington                       -     Cancelled
## 18:52  Basingstoke                             -     On time
## 18:52  Ealing Broadway                         -     On time
## 18:53  Didcot Parkway                          -     On time
## 18:55  Taunton                                 -     On time
## 18:56  London Paddington                       -     On time
## 18:58  Cheltenham Spa                          -     Cancelled
## 19:10  Newbury                                 -     On time
## 19:13  Port Talbot Parkway                     -     On time
## 19:15  Ealing Broadway                         -     On time
## 19:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 19:19  Hereford                                -     On time
## 19:19  London Paddington                       -     On time
## 19:20  Gatwick Airport                         -     On time
##        via Guildford                           
## 19:22  Ealing Broadway                         -     On time
## 19:30  London Paddington                       -     On time
## 19:40  Bedwyn                                  -     On time
## 19:41  London Paddington                       -     On time
## 19:48  London Paddington                       -     Delayed
## 19:52  Basingstoke                             -     On time
## 19:52  Ealing Broadway                         -     On time
## 19:53  Didcot Parkway                          -     On time
## 19:55  Weston-super-Mare                       -     On time
## 19:56  London Paddington                       -     On time
## 19:58  Cheltenham Spa                          -     On time
## 18:17  Ascot                                   -     On time
## 18:32  Ascot                                   -     On time
## 18:47  Ascot                                   -     On time
## 19:02  Ascot                                   -     On time
## 19:17  Ascot                                   -     On time
## 19:32  Ascot                                   -     On time
## 19:47  Ascot                                   -     On time
## 20:02  Ascot                                   -     On time
```
