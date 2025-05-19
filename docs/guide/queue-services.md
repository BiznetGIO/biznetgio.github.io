## Overview
This document outlines the new Queue Service architecture implementation, focusing on offloading actions from HB (Host Bridge) and facilitating future migration any services. 


## System Architecture
### General Flow


<p align="center">
	<img src="../img/queue-topology.png">
</p>

HB -> Queue Service -> Broker -> Service Notifier -> HB


## Component Details

### 1. Host Bridge (HB)
- Initiates create commands to Queue Service
- Receives webhook notifications for service completion
- Handles error notifications for further investigation

### 2. Queue Service
- Processes create commands from HB
- Transmits required information to Broker
- Manages service-specific operations

### 3. Message Broker
- Handles topic-based message routing
- Topic format: `service/topic`
- Example: `neo-wp/create-neo-wp`
- Manages action execution

### 4. Service Notifier
#### Responsibilities:
- Performs third-party service status checks
- Executes jobs across different services
- Contains service-specific modules
- Sends completion webhooks to HB

#### Operations:
- Status verification
- Service activation checks
- Webhook management

## Data Flow

### Normal Flow
1. HB initiates create command
2. Queue Service processes and forwards to Broker
3. Broker routes to appropriate service
4. Service Notifier performs checks
5. Webhook sent to HB with completion status
6. Payload returned matches initial create payload

### Error Handling
- Direct error notification to HB for:
  - Third-party service failures
  - Integration issues
  - Service-specific errors

## Implementation Notes
- Each service requires specific notification modules
- Service activation verification varies by service type
- Payload requirements differ based on service specifications

## Future Considerations
- Scalability for additional services
- Odoo migration compatibility
- Service-specific customizations

## Initial Implementation
Queue message service will serve as the first service to implement this architecture, serving as a model for future service integrations.

## Standardize Modules Functions
Template modules should be define on modules folder with spesific name microservice : 'modules/<service_name>'

example template file : 

```
'modules/app_platform.py'
'modules/neo_lite.py'
'modules/neo_metal.py'
```

Example implementations :
script code : `modules/counter.py`
```
import requests


def multiply(number: str):
    return 2 * int(number)

def count_words_at_url(url: str):
    """Just an example function that's called async."""
    print("module loaded")
    resp = requests.get(url)
    print(resp.text)
    return len(resp.text.split())
```

APis request and response output :

<p align="center">
	<img src="../img/multiply.png">
</p>
multiply 

<p align="center">
	<img src="../img/count_word.png">
</p>
count_words_at_url 



## Webhook Mechanism to Host Bridge  
This standardize from queue service to HB (Host Bridge) process.

```
{
data : // return data from worker,
payload : // payload data request to ms
}
```
