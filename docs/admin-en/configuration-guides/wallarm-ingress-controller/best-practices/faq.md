# FAQ

## How to check which client IP address is detected/used by the Ingress controller?

There are the following ways to check an IP address:

* Take a look at the controller container’s log and find records about handled requests - in the default logging format the first reported field is the detected client IP address. `25.229.38.234` is the detected IP address in the example below:
```
[wallarm-ingress-nginx-ingress-controller-775cf75564-6jlt9 nginx-ingress-controller] 25.229.38.234 - - [14/Mar/2020:23:55:11 +0000] "GET /ping HTTP/1.1" 200 893 "-" "curl/7.64.1" 172 0.020 [default-sise-80] [] 172.17.0.5:8080 893 0.020 200 d8402076753798d3b065269c16d4b34f 
```

* Go to your Wallarm account for the [US cloud](https://us1.my.wallarm.com) or for the [EU cloud](https://my.wallarm.com) > the **Events** section and expand request details. An IP address is displayed in the *Source* field. For example:

    ![!IP address from which the request was sent](../../../../images/admin-guides/configuration-guides/wallarm-ingress/request-ip-address.png)

    If the list of attacks is empty, you can send a [test attack](../../../../quickstart-en/qs-check-operation-en.md#2-run-a-test-attack) to the application protected by the Wallarm Ingress controller.
    
## How to check that the Ingress controller is receiving X-FORWARDED-FOR request header?

Please go to your Wallarm account for the [US cloud](https://us1.my.wallarm.com) or for the [EU cloud](https://my.wallarm.com) > the **Events** section and expand request details. In the displayed request details pay attention to the `X-FORWARDED-FOR` header. For example:

![!The X-FORWARDED-FOR header of the request](../../../../images/admin-guides/configuration-guides/wallarm-ingress/x-forwarded-for-header.png)

If the list of attacks is empty, you can send a [test attack](../../../../quickstart-en/qs-check-operation-en.md#2-run-a-test-attack) to the application protected by the Wallarm Ingress controller.