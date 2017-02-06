# benchmark

[![build status][travis-image]][travis-url]

[travis-image]: https://img.shields.io/travis/eggjs/benchmark.svg?style=flat-square
[travis-url]: https://travis-ci.org/eggjs/benchmark

egg benchmark

## Results

- node: 6.9.5
- koa: 1.2.4
- toa: 2.5.1
- egg: 0.10.0

Scene | QPS | Avg RT (ms) | Stdev RT | Max RT
---   | --- | ---         | ---      | ---
egg Hello World | 8917 | 4.68 | 3.56 | 108.21
koa Hello World | 10709 | 5.02 | 2.74 | 45.41
toa Hello World | 10041 | 5.38 | 2.20 | 47.18
egg nunjucks | 6732 | 7.25 | 4.81 | 257.58
koa nunjucks | 8596 | 6.03 | 6.35 | 162.53
toa nunjucks | 7869 | 6.32 | 3.16 | 59.54

## Default Middleware

- 15 middlewares (egg has 6 security middlewares enable by default)
- enable router

## Scenes

- Hello World: `$ EGG_SERVER_ENV=prod node benchmarks/simple/dispatch.js`
- nunjucks: `$ EGG_SERVER_ENV=prod node benchmarks/simple_view/dispatch.js`

## Scripts

- koa: `wrk http://remote-ip:7002/ -d 10 -c 50 -t 8`
- toa: `wrk http://remote-ip:7003/ -d 10 -c 50 -t 8`
- egg: `wrk http://remote-ip:7001/ -d 10 -c 50 -t 8`

## Server

- CPU x4: Intel(R) Xeon(R) CPU E5-2650 v2 @ 2.60GHz
- Mem: 10G

## Details

### Hello World

- koa

```bash
wrk http://10.209.84.139:7002/ -d 10 -c 50 -t 8
Running 10s test @ http://10.209.84.139:7002/
  8 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     4.68ms    3.56ms 108.21ms   97.60%
    Req/Sec     1.35k   270.38     2.86k    79.85%
  108162 requests in 10.10s, 16.19MB read
Requests/sec:  10709.54
Transfer/sec:      1.60MB
```

- toa

```bash
wrk http://10.209.84.139:7003/ -d 10 -c 50 -t 8
Running 10s test @ http://10.209.84.139:7003/
  8 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     5.02ms    2.74ms  45.41ms   92.83%
    Req/Sec     1.27k   140.46     2.59k    82.32%
  101410 requests in 10.10s, 17.02MB read
Requests/sec:  10041.10
Transfer/sec:      1.69MB
```

- egg

```bash
wrk http://10.209.84.139:7001/ -d 10 -c 50 -t 8
Running 10s test @ http://10.209.84.139:7001/
  8 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     5.38ms    2.20ms  47.18ms   76.67%
    Req/Sec     1.13k   219.26     2.56k    69.24%
  90065 requests in 10.10s, 25.34MB read
Requests/sec:   8917.43
Transfer/sec:      2.51MB
```

### nunjucks

- koa

```bash
wrk http://10.209.84.139:7002/ -d 10 -c 50 -t 8
Running 10s test @ http://10.209.84.139:7002/
  8 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     6.03ms    6.35ms 162.53ms   97.93%
    Req/Sec     1.09k   220.49     2.71k    82.02%
  86825 requests in 10.10s, 217.03MB read
Requests/sec:   8596.56
Transfer/sec:     21.49MB
```

- toa

```bash
wrk http://10.209.84.139:7003/ -d 10 -c 50 -t 8
Running 10s test @ http://10.209.84.139:7003/
  8 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     6.32ms    3.16ms  59.54ms   93.03%
    Req/Sec     0.99k   116.72     2.05k    80.72%
  79487 requests in 10.10s, 200.12MB read
Requests/sec:   7869.66
Transfer/sec:     19.81MB
```

- egg

```bash
wrk http://10.209.84.139:7001/ -d 10 -c 50 -t 8
Running 10s test @ http://10.209.84.139:7001/
  8 threads and 50 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     7.25ms    4.81ms 257.58ms   92.97%
    Req/Sec     0.85k   230.42     2.39k    62.89%
  67997 requests in 10.10s, 178.91MB read
Requests/sec:   6732.86
Transfer/sec:     17.72MB
```
