# Notrix Python SDK

## Installation
```commandline
pip install notrix
```

## Basic usage

```python
from notrix import Client, CheckoutSessionLineItem

client = Client("SECRET_API_KEY", "PROJECT_ID")

checkout_session = client.create_checkout_session(
    success_url="https://myshop.com/successful-payment",
    cancel_url="https://myshop.com/payment-canceled",
    items=[
        CheckoutSessionLineItem(
            name="Bike",
            description="green bike",
            price=28.2,  # USD
            quantity=1,
            imageURL="https://images.com/bike",
        )
    ]
)

print(checkout_session.link())  # Redirect the user to this payment page link in order to pay
```

```python
from notrix import Client

client = Client("<SECRET_API_KEY>", "PROJECT_ID")

payment_confirmed = client.is_paid(checkout_session.paymentRequestToken)  # True / False
```