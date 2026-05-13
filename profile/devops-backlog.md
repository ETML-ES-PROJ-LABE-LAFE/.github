# DEVOPS Backlog

---

## Story - Front-end deploiement

### Description

Cette issue est dédiée à la configuration du mécanisme de déploiement de l'application front-end codée en vue.js.

## Critères

- [ ] La couverture de test atteint min 80%. [Github action, vue js code coverage](https://github.com/bahmutov/code-coverage-vue-example).
- [ ] Uniquement le code nécessaire et déployé sur le S3. [Vuejs - production deployment](https://vuejs.org/guide/best-practices/production-deployment).
- [ ] Le cache CLOUD-FRONT est remis à jour à chaque déploiement. [Github action, S3 and Cloud Front](https://github.com/marketplace/actions/s3-and-cloudfront-deploy).

---

## Story - Back-end deploiement

### Description

Cette issue est dédiée à la configuration du mécanisme de déploiement des microservices Spring du backend.

## Critères

- [ ] La couverture de test atteint min 80%. Un taux inférieure empêche la publication de l'image. [Github Actions - Code Coverage](https://github.com/marketplace/actions/code-coverage-summary-action).
- [ ] Les images prêtes pour le déploiement sont mises à disposition dans votre organisation.[Github Containers Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry).
- [ ] Une politique de "tag" est appliqué par vos équipes (:dev, :stage, ...)
- [ ] Les bonnes pratiques Docker sont appliquées. [Docker - Building Best Practices](https://docs.docker.com/build/building/best-practices/)
