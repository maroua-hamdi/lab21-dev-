# Lab 21 : Capteurs embarqués Android

## Cours
**Programmation Mobile : Android avec Java**

---

## Présentation du Lab

Ce laboratoire porte sur l’utilisation des **capteurs embarqués Android** dans une application mobile développée avec **Android Studio** et le langage **Java**.

Les capteurs embarqués permettent à une application Android de récupérer des informations physiques provenant de l’appareil, comme le mouvement, l’orientation, la rotation, la proximité ou encore le champ magnétique.

Dans ce Lab 21, l’objectif est de créer une application Android capable de détecter les capteurs disponibles sur l’émulateur Android et d’afficher certaines valeurs mesurées en temps réel.

---

## Objectif général

L’objectif principal de ce laboratoire est de comprendre comment Android permet d’accéder aux capteurs embarqués à travers l’API **SensorManager**.

L’application réalisée permet de :

- Afficher la liste des capteurs disponibles dans l’émulateur Android
- Afficher les informations détaillées de chaque capteur
- Lire les valeurs détectées par un capteur
- Afficher une mesure du champ magnétique
- Tester le fonctionnement sur un émulateur Android Pixel 5
- Comprendre l’utilité des capteurs dans les applications mobiles

---

## Technologies utilisées

- Android Studio
- Java
- Android SDK
- Android Emulator
- Pixel 5 API 33
- SensorManager
- SensorEventListener
- Interface XML Android

---

## Capteurs étudiés

### 1. Accéléromètre

L’accéléromètre permet de mesurer l’accélération de l’appareil selon les trois axes :

- Axe X
- Axe Y
- Axe Z

Il est utilisé dans les applications de mouvement, les jeux mobiles, les applications sportives et les systèmes de détection d’orientation.

---

### 2. Gyroscope

Le gyroscope permet de mesurer la rotation de l’appareil.

Il est utilisé dans les applications qui nécessitent une détection précise des mouvements de rotation, comme les jeux 3D, la réalité augmentée et les applications de navigation.

---

### 3. Capteur de champ magnétique

Le capteur magnétique permet de mesurer le champ magnétique autour de l’appareil.

Il est souvent utilisé pour créer une boussole numérique ou pour déterminer l’orientation de l’appareil par rapport au champ magnétique terrestre.

Dans ce laboratoire, ce capteur est utilisé pour afficher une valeur détectée du champ magnétique.

---

### 4. Capteur d’orientation

Le capteur d’orientation permet de connaître la position ou la direction de l’appareil.

Il peut être utilisé dans les applications de navigation, de réalité augmentée ou de détection de position.

---

## Structure générale du projet

La structure générale du projet Android est la suivante :

    app/
    |
    ├── java/
    │   └── com.example.sensor/
    │       ├── MainActivity.java
    │       ├── SensorActivity.java
    │       └── ListSensorActivity.java
    |
    ├── res/
    │   ├── layout/
    │   │   ├── activity_main.xml
    │   │   ├── activity_sensor.xml
    │   │   └── activity_list_sensor.xml
    │   |
    │   └── values/
    │       ├── colors.xml
    │       ├── strings.xml
    │       └── themes.xml
    |
    └── AndroidManifest.xml

---

## Principe de fonctionnement

L’application utilise la classe **SensorManager** fournie par Android.

Cette classe permet de :

- Récupérer les capteurs disponibles sur l’appareil
- Obtenir un capteur précis
- Écouter les changements de valeurs d’un capteur
- Afficher les mesures détectées dans l’interface graphique

Le principe général est le suivant :

1. Déclaration d’un objet SensorManager
2. Récupération de la liste des capteurs disponibles
3. Affichage des informations de chaque capteur
4. Sélection d’un capteur précis
5. Écoute des changements avec SensorEventListener
6. Affichage des valeurs dans l’application

---

## Exemple de récupération des capteurs

    SensorManager sensorManager = (SensorManager) getSystemService(SENSOR_SERVICE);
    List<Sensor> sensors = sensorManager.getSensorList(Sensor.TYPE_ALL);

Ce code permet de récupérer tous les capteurs disponibles dans l’émulateur Android ou dans un téléphone réel.

---

## Exemple d’écoute d’un capteur

    @Override
    public void onSensorChanged(SensorEvent event) {
        float x = event.values[0];
        float y = event.values[1];
        float z = event.values[2];
    }

Cette méthode est appelée automatiquement lorsque les valeurs du capteur changent.

---

## Interface de l’application

L’application contient une interface simple composée de :

- Une barre supérieure violette
- Le titre de l’application : sensor
- Une page affichant la liste des capteurs disponibles
- Une page affichant la valeur du champ magnétique
- Des informations techniques sur chaque capteur

---

## Test avec l’émulateur Android

Le test a été réalisé avec un émulateur Android de type :

**Android Emulator - Pixel 5 API 33**

L’heure affichée sur l’émulateur est :

**10:09**

Deux écrans principaux ont été testés :

1. L’écran de la liste des capteurs disponibles
2. L’écran du champ magnétique

---


### Capture 1 : Liste des capteurs disponibles



<img width="270" height="557" alt="image" src="https://github.com/user-attachments/assets/1a9ee22b-9557-4d2f-9f11-53fc371034c3" />


---

### Capture 2 : Affichage du champ magnétique





<img width="269" height="553" alt="image" src="https://github.com/user-attachments/assets/19a79906-016a-468d-af6f-275aeb9fb9dc" />

---

## Résultat obtenu

### Résultat de la capture 1

La première capture montre l’écran qui affiche la liste des capteurs disponibles dans l’émulateur Android.

On peut observer plusieurs capteurs simulés par l’émulateur Pixel 5, notamment :

- Goldfish 3-axis Accelerometer
- Goldfish 3-axis Gyroscope
- Goldfish 3-axis Magnetic field sensor
- Goldfish Orientation sensor

Pour chaque capteur, l’application affiche plusieurs informations techniques :

- Id du capteur
- Nom du capteur
- Fournisseur
- Version
- Type Android
- Résolution
- Consommation électrique
- Portée maximale
- Délai minimal

Cette capture prouve que l’application arrive correctement à détecter et afficher les capteurs disponibles dans l’émulateur Android.

---

### Résultat de la capture 2

La deuxième capture montre l’écran du champ magnétique.

On peut observer :

- Le titre Champ magnétique
- La valeur détectée
- Les valeurs des axes X et Y
- Une zone graphique simple
- L’application exécutée dans un émulateur Pixel 5
- L’heure configurée à 10:09

Cette capture montre que l’application arrive à lire les données du capteur magnétique et à afficher les valeurs détectées dans l’interface.

---

## Analyse des résultats

Les résultats obtenus montrent que l’application fonctionne correctement avec les capteurs simulés par l’émulateur Android.

Même si l’émulateur ne possède pas de vrais capteurs physiques comme un téléphone réel, Android Studio fournit des capteurs simulés permettant de tester les fonctionnalités principales de l’application.

La liste des capteurs confirme que l’émulateur Pixel 5 fournit plusieurs capteurs utilisables dans le développement Android.

L’écran du champ magnétique montre que l’application peut récupérer les valeurs du capteur et les afficher en temps réel.

---

## Importance des capteurs dans Android

Les capteurs Android sont très importants dans le développement mobile moderne.

Ils permettent de créer des applications plus interactives et plus intelligentes.

Quelques exemples d’utilisation :

- Applications de sport
- Applications de santé
- Boussoles numériques
- Jeux mobiles
- Réalité augmentée
- Applications de navigation
- Détection de mouvement
- Mesure de l’orientation du téléphone
- Compteurs de pas
- Détection de proximité

---

## Difficultés rencontrées

Durant ce laboratoire, plusieurs points nécessitent de l’attention :

- Comprendre le rôle de SensorManager
- Identifier le bon type de capteur
- Utiliser correctement SensorEventListener
- Afficher les valeurs dans l’interface graphique
- Tester les capteurs avec un émulateur Android
- Vérifier les capteurs disponibles selon le type d’appareil utilisé

---

## Conclusion

Ce Lab 21 a permis de comprendre le fonctionnement des capteurs embarqués dans Android.

Grâce à l’utilisation de **SensorManager**, l’application peut accéder aux capteurs disponibles, lire leurs informations et afficher les valeurs détectées.

Le test sur l’émulateur Pixel 5 montre que l’application fonctionne correctement et que les capteurs simulés peuvent être utilisés pour développer et tester des fonctionnalités liées au mouvement, à l’orientation et au champ magnétique.

Ce laboratoire constitue une étape importante pour apprendre à développer des applications Android interactives utilisant les données physiques de l’appareil.

---

## Auteur

Réalisé par : **Hamdi Maroua**

Module : **Programmation Mobile : Android avec Java**

Lab : **Lab 21 - Capteurs embarqués Android**
