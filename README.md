#Chowder M-Pesa Checkout Android Libarary

This library, using the M-Pesa C2B APIs will allow you to prompt a user to make a payment from their M-Pesa accounts to a PayBill number without having to leave your app. 

For successful requests, Safaricom will send push USSD to the user's mobile device and prompt them to enter their Bonga PIN.

Get the sample apk from [here](https://github.com/IanWambai/Chowder/tree/master/sample/chowder_sample.apk), click on 'View the full file' to download it, or find it in the 'sample' folder:

The screenshots below show how it works.

![](images/hints.png?raw=true)
![](images/details.png?raw=true)
![](images/payment_ready.png?raw=true)
![](images/transaction_in_progress.png?raw=true)
![](images/ussd_push.png?raw=true)
![](images/ussd_accept.png?raw=true)
![](images/transaction_done.png?raw=true)

#Use Cases
You can easily use Chowder in your Android app for the following cases:
* Having a user pay before accessing your app, or certain features in your app
* Having a list of items, such as products, tickets, meals, books, music ,images or other media, and having the user reliably pay to access them
* In app purchases in games
* Having a user pay to access the premium/ad-free version of your app
* Subscribing a user and having them pay again after a set period of time
* Any form of payment you need a user to do for you to provide them goods/services via Android

#Usage

Add this to the build.gradle file of your module

    dependencies {
        compile 'com.toe.chowder:chowder:0.5.0'
    }

#Sample Code

Get the test `merchant_id` and `passkey` from the sample project.

        Chowder chowder = new Chowder(MainActivity.this, MERCHANT_ID, PASSKEY, amount, phoneNumber.replaceAll("\\+", ""), productId);
        chowder.processPayment();
        chowder.paymentCompleteDialog = new AlertDialog.Builder(MainActivity.this)
                .setPositiveButton("Confirm", new DialogInterface.OnClickListener() {
                    public void onClick(DialogInterface dialog, int which) {
                        //Check user's SMS inbox for confirmation text
                        //You can also use a callback URL to confirm the transaction, but I'll add that soon
                    }
                });

And you are done!