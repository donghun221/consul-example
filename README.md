# Consul Demo UI Link
http://http://124.156.122.145

# Register A service
curl --request PUT --data @service.json http://124.156.122.145/v1/catalog/register


    JEREMYYIN-MB0:consul-example donghun221$ curl --request PUT --data @service.json http://124.156.122.145/v1/catalog/register
    true

# Verify Service
http://124.156.122.145/v1/catalog/service/fake-service-2

    JEREMYYIN-MB0:consul-example donghun221$ curl http://124.156.122.145/v1/catalog/service/fake-service-2
    [  
       {  
          "ID":"40e4a323-2192-161a-0510-9bf59fe950b5",
          "Node":"fake-node-2",
          "Address":"2.2.2.2",
          "Datacenter":"hkdc",
          "TaggedAddresses":{  
             "lan":"2.2.2.2",
             "wan":"2.2.2.2"
          },
          "NodeMeta":{  
             "external-node":"true",
             "external-probe":"true"
          },
          "ServiceKind":"",
          "ServiceID":"fake-service-2",
          "ServiceName":"fake-service-2",
          "ServiceTags":[  
             "fake"
          ],
          "ServiceAddress":"2.2.2.2",
          "ServiceWeights":{  
             "Passing":1,
             "Warning":1
          },
          "ServiceMeta":{  
    
          },
          "ServicePort":8000,
          "ServiceEnableTagOverride":false,
          "ServiceProxyDestination":"",
          "ServiceProxy":{  
    
          },
          "ServiceConnect":{  
    
          },
          "CreateIndex":1466709,
          "ModifyIndex":1466709
       }
    ]

# Remember ModifyIndex
- 1466709

# Send a transaction with warning
    JEREMYYIN-MB0:consul-example donghun221$ curl --request PUT --data @txn.json http://124.156.122.145/v1/txn
    {  
       "Results":[  
          {  
             "Check":{  
                "Node":"fake-node-2",
                "CheckID":"service:fake-service-2",
                "Name":"Fake Check",
                "Status":"warning",
                "Notes":"",
                "Output":"",
                "ServiceID":"fake-service-2",
                "ServiceName":"fake-service-2",
                "ServiceTags":[  
                   "fake"
                ],
                "Definition":{  
                   "Interval":"10s",
                   "Timeout":"5s",
                   "HTTP":"http://localhost:8080i/health"
                },
                "CreateIndex":1466709,
                "ModifyIndex":1467067
             }
          }
       ],
       "Errors":null
    }

# API
## Register Service
| Method | Path | Produces |
|--|--|--|
| PUT | /catalog/register | application/json |

[https://www.consul.io/api/catalog.html#register-entity](https://www.consul.io/api/catalog.html#register-entity)

## Update status
| Method | Path | Produces |
|--|--|--|
| PUT | /txn | application/json |

[https://www.consul.io/api/txn.html#check](https://www.consul.io/api/txn.html#check)
