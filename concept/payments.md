# Payments

The system could be integrated with multiple payment providers to auto-handle payment for applications and pay developers directly. 

For each app, the developers can set the price in the manifest file (see App Packaging) The user would have to accept the payment during the installation process. 

## Possible payment providers / methods

- Stripe
- Paymill
- Paypal
- Bitcoin 

## Example payment setup in the app.json

{
	…
	payment: {
		price: {
			EUR : 4.99,
			USD : 5.99,
			default : USD
		}
		service: {
			paypal: {…}
			amazon: {…}
		}
	}
}

Service setup is not yet clear. Developers should have a simple way to setup available payment services and configuration for them. (e.g. an email address for paypal)

## VAT collection

The best possible solution for any developer would be the option to let the system handle VAT calculation according to the user's and developer's configured countries. But this would make the system very complex and would need a lot of updates. 

## App Demos

Similar to the Google Play Store it should be possible to test apps before you have to buy them. Maybe something like a 3 day trial would be possible with each app unless the developer disables this. 



