# Laravel Smart Trading Package

A Laravel package with machine learning capabilities.

## Introduction

This package provides a complete solution for integrating smart trading capabilities into any laravel application, with machine learning at it's core.

The modular design makes it easy to customize and extend for specific trading needs.

## Key Features

### 1. Modular Architecture

- Clean separation of concerns with interfaces
- Easy to extend with new strategies- or exchanges
- Dependency injection for all major components

### 2. Machine Learning integration

- Uses Rubix ML for PHP-based machine learning
- Supports model persistence and training
- Feature extraction from market data

### 3. Exchange Agnostic

- CCXT library for unified exchange API
- Easy to add support for new exchanges
- Sandbox mode for testing

### 4. Risk Management

- Built-in risk controls
- Position sizing based on risk level
- Drawdown and exposuremonitoring

### 5. Laravel integration

- Databse migrations and models
- Artisan commands for management
- Event system for trading notifications

## Package Usage Examples

### 1. Register the package in your laravel application

- Add the following to your *config/app.php*
```php
    `providers` => [
        // ...
        SmartTrading\Providers\SmartTradingServiceProvider::class,
    ],

    `alias` => [
        // ...
        'SmartTrading' => SmartTrading\Facades\SmartTrading::class,
    ],
```

### 2. Publish configuration

```bash
    php artisan vendor:publish --tag=smart-trading-config
```

### 3. Train the ML model

```bash
    php artisan smart-trading:train --samples=5000
```

### 4. Run a trading bot

```bash 
    php artisan smart-trading:run my_bot --symbol=BTC/USDT
```

### 5. Programmatic usage

```php
    use SmartTrading\Facades\SmartTrading;

    // Execute a bot
    $bot = \SmartTrading\Models\Bot::find(1);
    SmartTrading::executeBot($bot);
    
    // Train model with custom options
    $results = SmartTrading::trainModel([
        'test_size' => 0.3,
        'features' => [
            'rsi', 'volume', 'price_change'
        ]
    ]);
```