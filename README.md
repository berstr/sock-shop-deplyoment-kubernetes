1. MUST: set the value of env variable NEW_RELIC_LICENSE_KEY to the correct account license key before calling kubectl apply.

2. Optional: set the value of NEW_RELIC_APP_NAME to something different than the default: sock-shop-payment

--------------------------

Instead of changing the manifest files to set the correct NEW_RELIC_LICENSE_KEY and optionally a different NEW_RELIC_APP_NAME, you can also use the following command to set these values when applying the manifest file.

For example, the following command will set the NEW_RELIC_LICENSE_KEY and pipe it into the kubectl apply command:

sed -e 's|<.*NEW_RELIC_LICENSE_KEY.*>|ThisIsMyCorrectLicenseKey|g' payment.yaml | kubectl apply -f -

If you also want to change the NEW_RELIC_APP_NAME, you could use this command:

sed -e 's|value:.*sock-shop-payment.*|value: bernd-sock-shop-payment|g' payment.yaml | sed -e 's|<.*NEW_RELIC_LICENSE_KEY.*>|ThisIsMyCorrectLicenseKey|g' - | kubectl apply -f -
