CurrencyEditText
================

CurrencyEditText is an extension of Android's EditText view object. It is a module designed to provide ease-of-use when using an EditText field for gathering currency information from a user. 

CurrencyEditText provides support for a large number of localities/currencies. USD/GPB/Euro are officially supported, though all currencies as supported by ISO 4217 should work.

If you find that a certain currency is causing issues, please open an Issue in the Issue Tracker.


Using The Module
================

Using the module is not much different from using any other EditText view. Simply define the view in your XML layout:

        <com.blackcat.currencytextbox.CurrencyEditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            />

You're done! The CurrencyEditText module handles all the string manipulation and input monitoring required to allow for a clean, easy-to-use
currency entry system.

Attributes
===============

By default, CurrencyEditText provides a 'hint' value for the text box. This default value is the Currency Code symbol for the users given Locale setting. This is 
useful for debugging purposes, as well as provides clean and easy to understand guidance to the user. 

If you'd prefer to set your own hint text, simply set the hint the same was you would for any other EditText field. You can do this either in your XML layout
or in code.

If you'd like to disable the default hint entirely, simply set the DefaultHint attribute in your XML layout to false:

        <com.blackcat.currencytextbox.CurrencyEditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            CurrencyTextBox:enable_default_hint="false"
            />

Alternatively, you can also call SetDefaultHintEnabled(false) on the CurrencyEditText object in your code:

        CurrencyEditText tb = (CurrencyEditText) findViewById(R.id.test);
        tb.setDefaultHintEnabled(false);


Retrieving and Handling Input
=============================

As CurrencyEditText is an extension of the EditText class, it contains all the same getters and setters that EditText provides. 

To retrieve the fully formatted String value as shown to the user, simply call your CurrencyEditText objects getText() method.

However, you'll likely need to actually do something useful with the users input. To help developers more easily retrieve this information, CurrencyEditText provides a getRawValue() method. This method provides back the raw numeric values as they were input by the user, and should be treated as if it were a whole value of the users local currency.
For example, if the text of the field is $13.37, this method will return an integer with a value of 1337, as penny is the lowest denomination for USD. 

It is the responsibility of the calling application to handle this value appropriately. Keep in mind that dividing this number to convert it to some other denomination
 could possibly result in floating point rounding errors, and should be done with great caution. 
 
To help developers better facilitate the need to properly handle locale differences in currency, CurrencyEditText also provides a getLocale() method.

This method is really just a convenience method for retrieving information about a users locale. It is functionally equivalent to pulling the locale from the users configuration on their device. It is recommended 
that developers take a look at what the Locale and Currency classes offer in terms of denominations, decimal placement, string formatting, etc. 


Why doesn't CurrencyEditText do \<x\>?
====================================

CurrencyEditText is designed to be a small, lightweight module to provide ease-of-use to developers. If there is functionality missing that you would like to see added, 
submit a new Issue and label it as an Enhancement, and I will take a look. I make no guarantees that I will agree to implement it.

Use at your own risk!
=====================

As called out in the Apache license (which this project falls under), by using this software you agree to use it AS-IS. I make no claims that this code is
100% bug-free or otherwise without issue. While I've done my best to ensure that rounding errors don't come into play and that all codeflows have been tested, I cannot 
guarantee or provide any sort of warranty that this code will work for you. The onus is on you, and you alone, to analyze this software and determine if it's featureset and quality meet your needs.