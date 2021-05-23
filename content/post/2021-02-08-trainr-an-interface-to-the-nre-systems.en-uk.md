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

## Example (Last rendered on 2021-05-23 06:12)

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
## Reading (RDG) Station Board on 2021-05-23 06:12:33
## Time   From                                    Plat  Expected
## 08:14  Ealing Broadway                         14    On time
## 08:30  London Paddington                       9     On time
## 08:59  London Paddington                       9B    On time
## 09:10  Didcot Parkway                          15    On time
## 07:27  Guildford                               BUS   On time
## 08:07  Ascot                                   BUS   On time
## 08:21  Ascot                                   BUS   On time
## 08:27  Guildford                               BUS   On time
## 08:37  Ascot                                   BUS   On time
## 08:51  Ascot                                   BUS   On time
## 09:00  Basingstoke                             BUS   On time
## 09:07  Ascot                                   BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-23 06:12:34
## Time   To                                      Plat  Expected
## 07:12  London Paddington                       -     Cancelled
## 07:59  London Paddington                       9     On time
## 08:10  London Paddington                       15    On time
## 08:10  Newbury                                 12B   On time
## 08:30  London Paddington                       14    On time
## 08:31  Exeter St Davids                        9     On time
## 08:34  Bedwyn                                  15B   On time
## 08:38  Basingstoke                             12B   On time
## 08:38  Didcot Parkway                          14    On time
## 08:55  Ealing Broadway                         13    On time
## 09:00  Swansea                                 9B    On time
## 09:10  Ealing Broadway                         15    On time
## 07:15  Ascot                                   BUS   On time
## 07:20  Basingstoke                             BUS   On time
## 07:30  Ascot                                   BUS   On time
## 07:45  Ascot                                   BUS   On time
## 07:46  Guildford                               BUS   On time
## 08:00  Ascot                                   BUS   On time
## 08:15  Ascot                                   BUS   On time
## 08:30  Ascot                                   BUS   On time
## 08:35  Guildford                               BUS   On time
## 08:45  Ascot                                   BUS   On time
## 09:00  Ascot                                   BUS   On time
## 09:08  Guildford                               BUS   On time
```
