# Security configuration

When the z/OS Connect EE server is running with security on and requires an HTTPs connection then some additional configuration steps are required.

## HTTPs configuration

In order for the API Mediation Layer to establish a secure connection the certificate information of the two servers will need to be exchanged.

1. Extract the certificate from the z/OS Connect EE keyring in PEM format.
1. Import the certificate into the API Mediation Layer configuration by running the following command in the `<zowe_home>/api-mediation/` directory:

   ```sh
   scripts/apiml_cm.sh --action trust --certificate ~/serverCert.pem --alias <server name>
   ```
1. Import the API Mediation Layer certificate into the z/OS Connect EE truststore. The certificate is in the `<zowe_home>/api-mediation/keystore/localhost/localhost.keystore.cer` file.

Further information on configuring secure connections into z/OS Connect EE can be found in the [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SS4SVW_3.0.0/securing/config_tls_racf.html).

## User authentication

z/OS Connect EE will attempt to map the certificate used by the API Mediation Layer to a user ID available to the server.

In order to map the certificate the full distinguished name of the certificate is required. This is most easily seen in a browser that is connected to the API Mediation Layer. The sample certificate that is shipped with Zowe has the distinguished name:

```
CN=Zowe Service,OU=API Mediation Layer,O=Zowe Sample,L=Prague,ST=Prague,C=CZ
```

### Basic Registry

If using the basic registry functionality then the user is added with the using a user element.

```xml
<user name="Zowe Service" password="password"/>
```

The name matches the value in the `CN` part of the distinguished name.

_Note: the password is required but not used._

### SAF Registry

If using a SAF registry then the [instructions in the Knowledge Center](https://www.ibm.com/support/knowledgecenter/SS4SVW_3.0.0/securing/config_client_auth.html) should be followed to map the certificate to an appropriate user ID.