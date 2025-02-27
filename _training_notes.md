# Cloud CDN cache modes
- use_origin_headers : requries origin response to set valid cache directives . on client side extra managebility. user or app has better control.
- cache_all_static : cache everything, even if client set no-store, no-cache directive. however it will adjust according if user set different cache directives.
- force_cache_all: unconditionally caches every responses. overriding any cache directives set by client/origin

# Backend Services vs Backend Bucket vs Target pools vs NEG
- A Backend Bucket allow you to use Google Cloud Storage bucket with HTTP(S) load balancing. It can handle request for static content. This option would be useful for a webpage that with static content and it would avoid the costs of resources than a instance would need.
- The Backend Service is a centralized service that manages backends, which in turn manage an indeterminate number of instances that handle user requests.
- The Target Pools defines a group of instances like instance group minus all the complicated stuff such as instance template, autoscaler, autohealing, rolling updates and so on
- When a forwarding rule directs traffic to a target pool, Google Compute Engine picks an instance from these target pools based on a hash of the source IP and port and the destination IP and port. It uses forwarding rules instead to defines a group of instances that should receive incoming traffic
- This is why they both are listed as backend-services, because at the end they both do the same, but they specify for two different kind of load balancer. The backend service works for HTTP(S) load balancer and target pools are used for forwarding rules.
Network Endpoint Groups can be pointing to serverless (Cloud Functions, Cloud Run) or Hybrid (on-prem VMs via VPN or Interconnect or peering)

