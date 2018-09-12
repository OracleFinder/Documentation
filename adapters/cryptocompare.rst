*************
CryptoCompare
*************

.. index:: CryptoCompare

Overview
========

Adapter for use on Google Cloud Platform or AWS Lambda. Upload Zip and use trigger URL as bridge endpoint.


Installation
============

Build
-----

.. code-block:: bash
	
	npm install

.. code-block:: bash
	:caption: Create ZIP:
	
	zip -r cl-cc.zip .


.. tip::

	You can use one of our precompiled ZIP files from `Releases <https://github.com/OracleFinder/CryptoCompareExternalAdapter/releases>`_. Most recent release: `cl-cc-aws-gcp.zip <https://github.com/OracleFinder/CryptoCompareExternalAdapter/releases/download/v1.0/cl-cc-aws-gcp.zip>`_

Upload
------

Create a cloud function in GCP or Lambda, upload the ZIP file and set the handler function according to the platform you are using.

- GCP: ``gcpservice``
- AWS: ``handler``

Test Cases (GCP/AWS test events)
================================

Fail
----

.. code-block:: json
	:caption: Event:
	
	{
		"id": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {}
	}


.. code-block:: json
	:caption: Result:
	
	{
		"jobRunID": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"Response": "Error",
			"Message": "",
			"Type": 1,
			"Aggregated": false,
			"Data": [],
			"Path": "/data/",
			"ErrorsSummary": "Not implemented"
		}
	}

Pass
----

.. code-block:: json
	:caption: Event:
	
	{
		"id": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"endpoint": "price",
			"fsym": "ETH",
			"tsyms": "USD"
		}
	}

.. code-block:: json
	:caption: Result:
	
	{
		"jobRunID": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"USD": 285.58
		}
	}

.. code-block:: json
	:caption: Event:
	
	{
		"id": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"endpoint": "price",
			"fsym": "ETH",
			"tsyms": "USD,EUR,JPY"
		}
	}

.. code-block:: json
	:caption: Event:
	
	{
		"id": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"endpoint": "pricemulti",
			"fsyms": "BTC,ETH",
			"tsyms": "USD,EUR"
		}
	}

.. code-block:: json
	:caption: Event:
	
	{
		"id": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"endpoint": "pricemultifull",
			"fsyms": "BTC,ETH",
			"tsyms": "USD,EUR"
		}
	}

.. code-block:: json
	:caption: Event:
	
	{
		"id": "278c97ffadb54a5bbb93cfec5f7b5503",
		"data": {
			"endpoint": "generateAvg",
			"fsym": "ETH",
			"tsym": "USD",
			"exchange": "Kraken"
		}
	}
