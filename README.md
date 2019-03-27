# z/OS Connect EE API Mediation Layer Sample Configuration

This repository contains a sample configuration file for the Zowe API Mediation Layer that allows z/OS Connect EE servers to appear in the API Catalog.

Full details on how to configure the API Mediation layer are available on the [Zowe site](https://zowe.github.io/docs-site/latest/extend/extend-apiml/api-mediation-onboard-an-existing-rest-api-service-without-code-changes.html#identify-the-api-that-you-want-to-expose)

## Updating the sample

The [sample file](./zosconnect.yml) can be updated with the information about your specific z/OS Connect EE server.

* The `instanceBaseUrls` list needs to be updated with the servers hostname and port.
* The `swaggerUrl` needs to be updated with the server hostname and port.

## License
```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```