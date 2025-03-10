# Exemples de Dockerfiles Multi-Stages

## Introduction
Ce dépôt contient des exemples de Dockerfiles multi-stages pour différentes applications. Les conteneurs multi-stages permettent de créer des images Docker optimisées, plus petites et plus sécurisées en séparant les étapes de construction (build) et d'exécution (runtime).

## Objectifs
- Comprendre les conteneurs multi-stages et les comparer aux méthodes traditionnelles de construction d'images Docker mono-stage.
- Identifier les avantages clés des conteneurs multi-stages.
- Explorer des cas d'utilisation ou des scénarios pratiques concrets.
- Maîtriser la conception et la syntaxe des Dockerfiles multi-stages efficaces.
- Analyser les potentiels inconvénients ou complexités liés à l'utilisation de conteneurs multi-stages et proposer des solutions ou des stratégies pour les surmonter.

## Exemples

### Application Go
```dockerfile
# Stage 1: Build
FROM golang:1.23 AS build
WORKDIR /src
COPY . .
RUN go build -o /app .

# Stage 2: Runtime
FROM scratch
COPY --from=build /app /app
CMD ["/app"]
