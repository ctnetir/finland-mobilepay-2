|Android|iOS|
|:-:|:-:|

# Cordova Plugin for Finnish MobilePay AppSwitch
======
Thank you [mrlund](https://github.com/mrlund) for opensourcing this project.

This is a fork from his [repository](https://github.com/mrlund/cordova-mobilepay-appswitch). The original plugin was made for Dankse Bank MobilePay AppSwitch. In this one I made a quick change so it works with Finnish MobilePay App.

> This plugin is not developed, published or otherwise affiliated with Danske Bank or MobilePay, but is a private project released "as-is" to the public by the author.  


## <a id="reference"></a>Reference
## Installation

    cordova plugin add https://github.com/phuwin/cordova-mobilepay-appswitch -variable URL_IDENTIFIER="com.example.myapp" --variable URL_SCHEME="myAppUrlScheme" --variable MERCHANT_ID="APPDK0000000000"

## Supported Platforms

- Android
- iOS

## Methods

- window.CordovaMobilePayAppSwitch.startPayment

## Objects (Read-Only)

- Amount
- OrderId
- Result
- Success
- Failed
- Error

## window.CordovaMobilePayAppSwitch.startPayment

Starts the payment through MobilePay and returns the `success`
callback with a `Result` object as the parameter.  If there is an
error, the `failed` callback is passed a
`Error` object.

    window.CordovaMobilePayAppSwitch.startPayment(amount,
                                             [orderId],
                                             [success],
                                             [failed]);

### Parameters

- __amount__: The amount to be charged.

- __orderId__: _(Optional)_ The order id to identify the order.

- __success__: _(Optional)_ The callback that executes on success.

- __failed__: _(Optional)_ The callback that executes on failure.


### Example

```javascript

    // amount
    //
    var amount = '150'

    //orderId
    //
    var orderId = '1234'

    // onSuccess Callback
    // This method accepts a Result object, which contains the
    // transactionId
    //
    var onSuccess = function(result) {
        alert('OrderId: '          + result.orderId          + '\n' +
              'TransactionId: '         + result.transactionId         + '\n' +
              'AmountWithdrawnFromCard: '          + result.amountWithdrawnFromCard          + '\n' +
    };

    // onError Callback receives an errorr string
    //
    function onError(error) {
        alert('message: ' + error + '\n');
    }

    window.CordovaMobilePayAppSwitch.startPayment(amount, orderId, onSuccess, onError);

```

