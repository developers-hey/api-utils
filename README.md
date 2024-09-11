# API Utilities / Utilerias de APIs

This repository contains utilities or artifacts to facilitate the consumption and testing of the Hey Banco and Banregio API's.  
`Spanish translation:` Este repositorio contiene utilerias o artefactos para facilitar el consumo y testeo de las APIs de Hey Banco y Banregio.

1. Java client to perform the payload encryption/decryption required to be sent in Postman requests. `Spanish translation:` Cliente Java para realizar el cifrado/descifrado de carga útil que requiere enviar en las peticiones de Postman.
* Directory/Directorio: Client JWS-JWE
2. Postman Collections, allows developers to interact with various APIs efficiently `Spanish translation:` Colecciones Postman, permite a los desarrolladores interactuar con diversas APIs de manera eficiente.
* Directory/Directorio: Postman-Collection

## Requisites / Requisitos 📋
1. You need to have the following installed. `Spanish translation:`  Necesitas tener instalado lo siguiente.

* JDK 11 or +
* [Postman](https://www.postman.com/downloads/)

2. Unzip your **API Kit** files that contains SSL certificates and credentials as following describe. `Spanish translation:` Descomprime tus archivos de API kit que contiene certificados SSL y credenciales como se describe a continuación:

| Folder / Carpeta                      |    File / Archivo            | Content / Contenido                                 |
|:------------------------------------- |:-----------------------------|:----------------------------------------------------|
| `Client_Credentials_{API-product}_{Environment}.zip`  | **Consumer.txt**               | The app identifier of the API consumer (B-Application). `Spanish translation:` El identificador de aplicación del consumidor de API (B-Application). |
| `Client_Credentials_{API-product}_{Environment}.zip`  | **Token.txt**                  | Credentials to get the JWT token used to consume the API. `Spanish translation:` Credenciales para obtener el token JWT utilizado para consumir la API. |
| `Client_Certificates_{API-product}_{Environment}.zip`  | **Client_Passwd.txt**          | Password for KeyStore, TrustStore and PrivateKey files. `Spanish translation:` Contraseña para archivos KeyStore, TrustStore y PrivateKey. |
| `Client_Certificates_{API-product}_{Environment}.zip`  | **Client_KeyStore_mTLS.p12**   | List of client private keys to establish a mutual TLS connection with each API. `Spanish translation:` Lista de llaves privadas del cliente para establecer una conexión TLS mutua con cada API. |
| `Client_Certificates_{API-product}_{Environment}.zip`  | **Server_PublicKey_JWE.pem**   | Server public key to encrypt API requests payloads using JWE and JWS standards. `Spanish translation:` Clave pública del servidor para encriptar los payload de petición a la API utilizando los estándares JWE y JWS.           |

---
 
## Setup 🛠️
1. **Java Client:** Enter the following information on the main screen. `Spanish translation:` **Cliente Java:** Ingresar la siguiente información en la pantalla principal.
* Public Key: Select the path to the Server_PublicKey_JWE.pem file. `Spanish translation:` Llave Pública: Seleccionar la ruta del archivo Server_PublicKey_JWE.pem
* Key Store: Select the path to the Client_KeyStore_mTLS.p12 file. `Spanish translation:` Almacén de Llaves: Seleccionar la ruta del archivo Client_KeyStore_mTLS.p12
* Keystore Password: Enter the password obtained from the Client_Passwd.txt file. `Spanish translation:` Contraseña del almacen: Ingresar la contraseña obtenida del archivo Client_Passwd.txt
* B-Application: Enter the B Application obtained from the Consumer.txt file. `Spanish translation:` B-Application: Ingresar el BApplication obtenido del archivo Consumer.txt

2. **Postman:** Configure the following: `Spanish translation:` Configurar lo siguiente:
* Add the certificate in Postman of the domain of the APIs that are required to be tested in the Configuration option -> Certificates, file Client_KeyStore_mTLS.p12 `Spanish translation:` Agregar el certificado en Postman del dominio de las APIs que se requiere probar en la opción de Configuración -> Certificados, archivo Client_KeyStore_mTLS.p12
* Configure the environment variables of the domain to be tested, obtain the necessary information from the API Kit. `Spanish translation:` Configurar las variables de ambiente del dominio a probar, obtener la información necesaria del API Kit.  

##  Testing ⚙️

* Java Client/Cliente Java
```bash
cd Client\ JWS-JWE
java -jar ClientJWSJWE-1.1.3.jar
```
* Postman Collections/Colecciones Postman: Select the environment variable and request of the API that you want to test, if it is required to send a payload in the request it must be previously encrypted using the Java Client. `Spanish translation:` Seleccionar la variable de ambiente  y petición de la API que desea probar,  si se requiere enviar carga útil en la petición deberá encriptarse previamente usando el Cliente Java.

### Autors / Autores ✒️
- [Hey, Tech developers](mailto:developers@hey.inc?subject=API%20Snippets)


### Notes / Notas 📄

* To consume the API is needed internet connection reaching out the followings DNS: `Spanish translation:` Para consumir la API se necesita conexión a internet llegando a los siguientes DNS:

  * Hey Banco
    *  Token(Sandbox): https://sbox-api-tech.hey.inc/auth/v1/oidc/token
    *  API(Sandbox): https://sbox-api-tech.hey.inc/{api-product}/{api-version}/{api}
    *  Token(Live): https://api-tech.hey.inc/auth/v1/oidc/token
    *  API(Live): https://api-tech.hey.inc/{api-product}/{api-version}/{api}


  * Banregio
    *  Token(Sandbox): https://sbox-open-api.banregio.com/auth/v1/oidc/token
    *  API(Sandbox): https://sbox-open-api.banregio.com/{api-product}/{api-version}/{api}
    *  Token(Live): https://open-api.banregio.com/auth/v1/oidc/token
    *  API(Live): https://open-api.banregio.com/{api-product}/{api-version}/{api}

