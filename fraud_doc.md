# Client side changes
### Include finix javascript as follows to get session_id 
``` javascript
 <script src='https://forms.finixpymnts.com/finix.js' async></script>

 <script type="text/javascript">
		/* 1st argument -> environment. Values are qa, sandbox, production */
		/* 1st argument -> merchantId*/
    	const FinixAuth = window.Finix.Auth('qa', 'MUeDVrf2ahuKc9Eg5TeZugvs')

	const sessionKey = FinixAuth.getSessionKey();
 </script>
```

# Authorization with fraud

### fraud_session_id below is from the client : sessionKey above
``` bash
curl https://finix.sandbox-payments-api.com/authorizations \
    -H "Content-Type: application/vnd.json+api" \
    -u  USsRhsHYZGBPnQw8CByJyEQW:8a14c2f9-d94b-4c72-8f5c-a62908e5b30e \
    -d '
	{
	    "fraud_session_id": "FSpowiefljwlef98732rjlfjlw",
	    "source": "PIe2YvpcjvoVJ6PzoRPBK137",
	    "merchant_identity": "IDpYDM7J9n57q849o9E9yNrG",
	    "tags": {
	        "order_number": "21DFASJSAKAS"
	    },
	    "currency": "USD",
	    "amount": 100,
	    "processor": "DUMMY_V1"
	}'
```

# Transfer with fraud

### fraud_session_id below is from the client : sessionKey above
``` bash
curl https://finix.sandbox-payments-api.com/transfers \
    -H "Content-Type: application/vnd.json+api" \
    -u  USsRhsHYZGBPnQw8CByJyEQW:8a14c2f9-d94b-4c72-8f5c-a62908e5b30e \
    -d '
	{
	    "fraud_session_id": "FSpowiefljwlef98732rjlfjlw",
	    "merchant": "MUeDVrf2ahuKc9Eg5TeZugvs",
	    "currency": "USD",
	    "amount": 662154,
	    "source": "PIe2YvpcjvoVJ6PzoRPBK137",
	    "tags": {
	        "test": "sale"
	    }
	}'
```
