# Scheduling your invoice calculations using bluectl

!!! warning
    This guide is only applicable to Ripple users.

In this guide, we will try and create an invoicing calculation schedule for Ripple every 3rd day of each month. At the moment, only one schedule is allowed per Ripple account.

Make sure to install [`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) first.

Note that creating a calculation schedule automatically enables your notification channels as well. If you don't specify a notification channel during schedule creation, a default email-type notification channel will be created using your primary email address. At the moment, only email-type notification channels are supported.

``` sh
$ bluectl cost aws calculation schedule create "0 0 3 * *"
```

Run the following command to see your current schedule:

``` sh
$ bluectl cost aws calculation schedule list
```

!!! info "--notification-channel"
    If you want to use an [existing notification channel](https://app.alphaus.cloud/ripple/notification-setting), use the `--notification-channel=id` flag. You can get your channel ids using the following command:

    ``` sh
    $ bluectl notification channels list
    ```

Finally, run the following command to delete your schedule:

``` sh
$ bluectl cost aws calculation schedule rm -
```
