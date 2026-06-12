# ESP32-APS-ECU

## Récupérer localement les données APSystems avec un ESP32

Ce projet documente la mise en œuvre d'une solution permettant de récupérer directement les données de production de micro-onduleurs APSystems à l'aide d'un ESP32 et d'un module radio CC2530.

L'objectif est de disposer localement des informations de production sans dépendre d'un ECU APSystems ni d'un service cloud externe.

---

## Origine du projet

Cette réalisation s'appuie sur l'excellent travail réalisé par l'auteur du projet open source :

**ESP32-read-APS-inverters**

https://github.com/patience4711/ESP32-read-APS-inverters

Le firmware, l'architecture logicielle et le protocole radio utilisés sont issus de ce projet.

Cette documentation n'a pas vocation à remplacer la documentation officielle mais à partager un retour d'expérience complet de mise en œuvre sur une installation réelle.

---

## Objectifs de ce retour d'expérience

Ce retour d'expérience couvre :

* le choix de la solution retenue ;
* l'approvisionnement du matériel ;
* le flashage du module CC2530 ;
* la mise en œuvre de l'ESP32 ;
* la récupération des données APSystems ;
* l'intégration MQTT ;
* l'intégration Jeedom ;
* les difficultés rencontrées ;
* les résultats obtenus ;
* les limites identifiées.

---

## Installation concernée

Installation photovoltaïque résidentielle composée de :

* micro-onduleurs APSystems DS3-L ;
* passerelle Jeedom ;
* réseau WiFi domestique ;
* broker MQTT local.

Les principes décrits restent applicables à d'autres modèles compatibles avec le projet d'origine.

---

## Architecture cible

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

L'ensemble des données de production est récupéré localement puis publié vers le système domotique sans dépendance à Internet.

---

## Sommaire

1. Pourquoi ce projet ?
2. Architecture générale
3. Matériel utilisé
4. Flashage du CC2530
5. Déploiement de l'ESP32
6. Appairage avec les micro-onduleurs
7. Intégration MQTT
8. Intégration Jeedom
9. Retour d'expérience
10. Limites et perspectives

---

## Avertissement

Cette documentation correspond à mon environnement de test et à mes choix d'intégration.

Les informations fournies sont données à titre informatif et doivent être adaptées à votre propre installation.
