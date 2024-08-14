# SEPA-QR-for-Woocommerce (GDPR-compliant)

A plugin to add SEPA QR codes as payment option to your WooCommerce
order confirmations. This way, customers can pay with whatever (SEPA-compliant) payment app they're familiar with.

# History

This plugin is based on [the work by Coernel82](https://github.com/Coernel82/SEPA-QR-for-Woocommerce/).

What this plugin adds is image support. The original plugin used
Base64 encoded images, but not all email clients support this.

# Prerequisite

php GD2 extension must be installed as the QR-Code generator by [fellwell15](https://github.com/fellwell5/bezahlcode/) requires this. **I guess this is a standard module and for most people nothing has to be done here!**

# Installation

Currently, download the code and upload it to your plugin directory.

The original plugin can be found in the [WordPress Plugin directory](https://wordpress.org/plugins/mxp-sepa-qr-code-addon-for-woocommerce).
This version can't yet.

## Manual installation

* Download the ZIP-file via "Code --> Download Zip"
* Extract ZIP-File and make a new ZIP-File from the mxp-sepaqr directory
* In Woocommerce via "install" and upload or manually placing mxp-sepaqr.zip into the plugin folder.

# What it does
places an image with the SEPA-QR-Code in the
* thank-you-page after placing an order
* email you get from woocommerce

In the backend:
* the QR code generator creates the QR-code locally. There is **no Google-API nor external server in use**!
* the QR code generator is from [fellwell15](https://github.com/fellwell5/bezahlcode/)
* plugin registers a get-parameter (configurable, default mxp_qr) for testing purposes and, if desired, to create links to the cached QR codes.
* the prefix mxp is used throghout the plugin to avoid collisions with other plugins and functions. mxp stands for www.musicalexperten.de (musical experts). Remember where you've seen it first! ;-)


# Translation
https://translate.wordpress.org/projects/wp-plugins/mxp-sepa-qr-code-addon-for-woocommerce/

# Configuration / if it does not work

The plugin comes with a little fallback: In case the BIC, IBAN, etc. are not shown open the **mxp-sepaqr.php** in the [programing code](https://github.com/petermorlion/SEPA-QR-for-Woocommerce/blob/afbacf58264c7afccd6b7f29e3f3105cb0e95b3b/mxp-sepaqr/mxp-sepaqr.php#L45-L50) you can hardcode some variables and translations. You'll find explanations in the comments.

## Advanced configuration of the qr-code itself
Have a look at [fellwell15](https://github.com/fellwell5/bezahlcode/)

# Testing and troubleshooting

## Simple way

Install the plugin and order s.th. in your shop using BACS (direct bank transfer).

## To test if the QR-Code generator is working

www.yourwebpage.de/?mxp_qr=something  = creates a real QR with dummyvalues 11-11
[Working example](https://www.musicalexperten.de/?mxp_qr=something)

## To find an existing cached QR-Code, query for a valid md5 string. If it does not exist in cache or transients, a sad smiley will appear.

www.yourwebpage.de/?mxp_qr=351436ef4b279e1811a6c68a2dd58b1b 
results in a sad smiley. [Working example](https://www.musicalexperten.de/?mxp_qr=351436ef4b279e1811a6c68a2dd58b1b)

# Remarks
Storing the QR code in cache or transients is only needed if you want to use a link instead of a picture inside the email. Details in the program code.

# Support
Feel free to open GitHub issues and I will follow up on them.

# Full integration in Woocommerce
I am more then happy if someone integrates the code into the Woocommerce core! The topic is discussed here: https://github.com/woocommerce/woocommerce/issues/27661

Once this is integrated in WooCommerce, this plugin will probably no
longer serve a purpose.
