# Cisco Datacenter Network Manager (DCNM) API Postman Collection

This repository contains the a Postman collection and environment variable file to leverage the REST API on DCNM.  This collection was tested and built using DCNM 11.5(1) within the DevNet Sandbox infrastructure.  As such, some variables will need to be reset if used outside of this testbed.

## Cisco DCNM Background

DCNM is a network management platform for all NX-OS-centric network deployments.  DCNM has several different installation personas, including LAN Fabric (BGP-EVPN with VXLAN), LAN Management (classic layer-2/layer-3 architecture), IP Fabric for Media (IPFM) and storage networking (SAN), however this collection covers the LAN fabric deployment model supporting an EVPN-VXLAN fabric backed by Nexus 9000-series switching.  APIs for other personas, while potentially overlapping, are not covered as part of this collection.

## Additional Resources
- [DCNM Sandbox on DevNet](https://devnetsandbox.cisco.com/RM/Diagram/Index/4b6f511a-4d7c-4764-927b-0fc591a661c6?diagramType=Topology)
- REST API documentation is available off-box [here](https://developer.cisco.com/docs/data-center-network-manager/11-5-1/)
- REST API documentation also available directly on the DCNM at `http://DCNM.IP.ADDRESS/api-docs`

## Covered APIs

- DCNM administration
- L4-L7 service operations
- Fabric, Network, Interface, VRF, and Link top-down operations
- LAN credential management
- Policy and Template operations
- Physical switch roles and discovery

## Notes about the included ENV variables

Prior to using any requests, please ensure you gather the token from your DCNM instance using the included API call `dcnm login - gather token`.  This call will log you into the DCNM (using credentials stored in the environment) and automatically store the key for use with every other request in the collection.

In order to keep the environment variables to a reasonable number, reuse was included.  While I made attempts to include commonly reused variables (fabric names, VRF names, etc), the variables may require a bit of context parsing to ensure the correct usage within a particular environment.  In some instances, variables are defined within the payload, but not inside of the environment file to discern that the specific variable should be replaced.  As a final note, for any API or payload referencing a device serial number -- please ensure correct serial numbers are inserted as appropriate.

_In some instances, Javascript tests have been included as part of the API request to populate another variable that would be used somewhere else in that folder of requests (VRF IDs, VLAN IDs, etc).  These can be overridden in the environment settings, but have been included for automated tasks (like using Runner)_
