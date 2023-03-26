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

## Example (Last rendered on 2023-03-26 08:03)

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
## Reading (RDG) Station Board on 2023-03-26 08:03:27
## Time   From                                    Plat  Expected
## 08:57  London Paddington                       9B    09:00
## 08:58  London Paddington                       14    09:06
## 09:11  Didcot Parkway                          -     On time
## 09:15  London Paddington                       12B   On time
## 09:16  London Paddington                       9B    On time
## 09:18  London Paddington                       7     On time
## 09:19  Newbury                                 15    On time
## 09:27  London Paddington                       9     On time
## 09:28  London Paddington                       14    On time
## 09:28  Swindon                                 13A   On time
## 09:39  Basingstoke                             12B   On time
## 09:40  Bristol Parkway                         11    On time
## 09:40  Guildford                               7A    On time
## 09:47  Salisbury                               1     On time
## 09:57  London Paddington                       9     On time
## 09:58  Didcot Parkway                          15A   On time
## 09:59  Didcot Parkway                          11A   On time
## 09:59  London Paddington                       14    On time
## 10:06  Southampton Central                     12B   On time
## 10:08  Guildford                               5     On time
## 10:10  Weston-super-Mare                       10    On time
## 10:16  London Paddington                       13B   On time
## 10:18  Bedwyn                                  12    On time
## 10:19  London Paddington                       9B    On time
## 10:25  Port Talbot Parkway                     11    On time
## 10:27  London Paddington                       7     On time
## 10:29  London Paddington                       14    On time
## 10:32  Basingstoke                             2     On time
## 10:35  Exeter St Davids                        11    On time
## 10:38  Guildford                               7A    On time
## 10:39  Didcot Parkway                          13    On time
## 10:40  Bristol Parkway                         10    On time
## 10:44  London Paddington                       8     On time
## 10:46  London Paddington                       9     On time
## 10:47  Salisbury                               1     On time
## 10:57  London Paddington                       8     On time
## 10:58  London Paddington                       14    On time
## 10:59  Didcot Parkway                          11    On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:26  Staines                                 BUS   On time
## 09:27  Staines                                 -     Cancelled
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:56  Staines                                 BUS   On time
## 09:57  Staines                                 BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:26  Staines                                 -     Cancelled
## 10:27  Staines                                 BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:56  Staines                                 BUS   On time
## 10:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-26 08:03:31
## Time   To                                      Plat  Expected
## 08:59  Swansea                                 9B    09:01
## 09:12  Ealing Broadway                         -     On time
## 09:15  Didcot Parkway                          8     On time
## 09:18  Didcot Parkway                          9B    On time
## 09:20  Didcot Parkway                          12B   On time
## 09:20  Penzance                                7     On time
## 09:21  Guildford                               13A   On time
## 09:24  Abbey Wood                              14    On time
## 09:34  London Paddington                       13A   On time
## 09:35  Weston-super-Mare                       9     On time
## 09:37  Basingstoke                             7B    On time
## 09:41  Guildford                               13A   On time
## 09:43  Bedwyn                                  7B    On time
## 09:45  London Paddington                       11    On time
## 09:52  Bournemouth                             8     On time
## 09:54  Abbey Wood                              14    On time
## 09:59  Swansea                                 9     On time
## 10:00  London Paddington                       11A   On time
## 10:12  Salisbury                               1     On time
## 10:14  Ealing Broadway                         15A   On time
## 10:15  Didcot Parkway                          12B   On time
## 10:15  London Paddington                       10    On time
## 10:20  Didcot Parkway                          9B    On time
## 10:21  Guildford                               7A    On time
## 10:24  Abbey Wood                              14    On time
## 10:27  London Paddington                       11    On time
## 10:28  Didcot Parkway                          13B   On time
## 10:28  Penzance                                7     On time
## 10:37  Basingstoke                             2     On time
## 10:41  Guildford                               5     On time
## 10:43  Newbury                                 15    On time
## 10:45  Bristol Parkway                         8     On time
## 10:45  London Paddington                       11    On time
## 10:47  London Paddington                       10    On time
## 10:54  Abbey Wood                              14    On time
## 10:55  Weston-super-Mare                       9     On time
## 11:00  London Paddington                       11    On time
## 11:01  Paignton                                8     On time
## 09:25  Staines                                 BUS   On time
## 09:27  Staines                                 BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:55  Staines                                 -     Cancelled
## 09:57  Staines                                 BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:25  Staines                                 BUS   On time
## 10:27  Staines                                 BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:55  Staines                                 BUS   On time
## 10:57  Staines                                 -     Cancelled
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
