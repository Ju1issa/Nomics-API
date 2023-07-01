# Nomics-API
This script uses the Nomics API to fetch real-time market data for multiple cryptocurrencies
import requests

def get_crypto_market_data(crypto_symbols):
    url = f'https://api.nomics.com/v1/currencies/ticker?key=YOUR_API_KEY&ids={",".join(crypto_symbols)}&convert=USD'
    response = requests.get(url)
    data = response.json()
    if isinstance(data, list):
        return data
    return None

# Example usage
crypto_symbols = ['BTC', 'ETH', 'XRP']

market_data = get_crypto_market_data(crypto_symbols)
if market_data:
    print("Real-time market data:")
    for currency in market_data:
        print(f"Name: {currency['name']}")
        print(f"Symbol: {currency['symbol']}")
        print(f"Price: ${currency['price']}")
        print(f"Market Cap: ${currency['market_cap']}")
        print(f"24h Volume: ${currency['volume']}")
        print("------------------------")
else:
    print("Failed to retrieve market data")

