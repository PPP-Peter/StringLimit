# Nova String Limit Field




## Installation

``` php
composer require composer require pppcreative/string-limit
```

## Usage

``` php
use ppp\StringLimit\StringLimit;

StringLimit::make(__('name'), 'name')->max(10)->rules('max:10'),
```


