# Pourquoi ce projet ?

## Contexte

Mon installation photovoltaïque est équipée de micro-onduleurs APSystems DS3-L.

Comme de nombreux utilisateurs, j'ai initialement utilisé l'écosystème proposé par le constructeur pour consulter les données de production.

Cette approche fonctionne correctement pour un usage standard, mais présente plusieurs limitations lorsqu'on souhaite intégrer les données photovoltaïques dans une démarche de supervision énergétique plus globale.

---

## Les limites de l'écosystème constructeur

### Dépendance au cloud

Les données de production sont principalement accessibles via les services cloud du constructeur.

Cette architecture implique :

* une connexion Internet permanente ;
* une dépendance à la disponibilité des services externes ;
* une perte de maîtrise sur l'accès aux données.

En cas d'arrêt du service ou d'évolution de la politique du fournisseur, l'accès aux données peut être impacté.

---

### Intégration domotique limitée

L'objectif était de pouvoir exploiter les données photovoltaïques au sein de Jeedom afin de :

* construire des tableaux de bord personnalisés ;
* historiser les données localement ;
* créer des scénarios d'automatisation ;
* croiser les informations avec d'autres équipements de la maison.

Les solutions disponibles nécessitaient souvent :

* des appels vers des API cloud ;
* des développements spécifiques ;
* des dépendances externes supplémentaires.

---

### Maîtrise des données

L'un des objectifs du projet est de conserver localement les données de production :

* sans dépendance à un service tiers ;
* sans limitation d'accès ;
* avec la possibilité d'historiser les mesures aussi longtemps que souhaité.

---

## Objectifs recherchés

Le projet devait permettre :

### Fonctionnels

* récupérer les données des micro-onduleurs ;
* disposer des mesures en temps réel ;
* intégrer les données dans Jeedom ;
* publier les mesures via MQTT.

### Techniques

* fonctionner entièrement sur le réseau local ;
* éviter toute dépendance à Internet ;
* s'appuyer sur du matériel peu coûteux ;
* rester simple à maintenir dans le temps.

---

## Pourquoi ESP32-read-APS-inverters ?

Après analyse des différentes approches disponibles, le projet open source ESP32-read-APS-inverters s'est imposé comme une solution particulièrement intéressante.

Ses principaux atouts sont :

* communication directe avec les micro-onduleurs ;
* fonctionnement autonome ;
* absence de dépendance au cloud ;
* matériel simple et économique ;
* communauté active ;
* compatibilité avec plusieurs générations de micro-onduleurs APSystems.

---

## Démarche retenue

La stratégie choisie a été la suivante :

1. mettre en œuvre la solution proposée par le projet open source ;
2. comprendre son architecture ;
3. intégrer les données dans l'écosystème Jeedom ;
4. évaluer sa stabilité dans le temps ;
5. documenter les résultats obtenus.

L'objectif n'était pas uniquement d'obtenir les données de production, mais également de comprendre le fonctionnement général de la solution afin d'en garantir la pérennité.

---

## Résultat attendu

À terme, l'ensemble des données photovoltaïques doit être disponible localement selon l'architecture suivante :

```text
Micro-onduleurs APSystems
            ↓
         CC2530
            ↓
          ESP32
            ↓
          MQTT
            ↓
         Jeedom
```

L'installation devient ainsi indépendante du cloud pour la collecte et l'exploitation des données de production.
