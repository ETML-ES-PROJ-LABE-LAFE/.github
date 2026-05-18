# Validation des JWT

Pour faire suite à notre discussion sur la gestion des JWT, notamment lors de la validation d’un token existant.

## Intention
Il est important d’éviter de faire des appels systématiques à votre fournisseur d’identité, par exemple à Keycloak, lors de la validation des requêtes. Si chaque requête impliquait un appel à Keycloak, le système d’authentification deviendrait un point de contention et pourrait rapidement saturer.

## Solution possible
Voici une solution standard basée sur des *tokens JWT self-contained*.

**Rôle de Keycloak** 

* Emettre les tokens JWT
* Signer les tokens
* Exposer les clés publiques via JWKS.

[Keycloack and JWKS](https://documentation.cloud-iam.com/resources/configure-remote-jwks.html)

**Rôle de NGINX**

Introduction : NGINX ne permet pas nativement (dans sa version open-source) de valider des JWT, ni de gérer un cache de clé publiques JWKS afin de valider luer signature.

Ces fonctionnalités ne sont disponibles que via extensions ou composants externes, par exemple :

* OpenResty (Lua)
* oauth2-proxy
* un service de validation externe via auth_request
* NGINX Plus (module JWT natif)

Ce qui permettrait ensuite à notre API Gateway s'assurer les services suivants:

* Jouer le rôle de gateway
* Déléguer ou effectuer la validation JWT via modules/extensions
* Vérifier localement les tokens si un mécanisme de validation est configuré (Lua, NGINX Plus, ou service externe)
* Router les requêtes vers les services backend uniquement si le token est valide

