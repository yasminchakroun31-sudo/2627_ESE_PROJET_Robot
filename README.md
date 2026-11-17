# 2627_ESE_PROJET_PAC-Man🤖🗑️
PAC-Man 

### Équipe
- **Yesmine Chakroun** (yasminechakroun31-sudo)
- **Wejdene Hazami**
- **Roua Jaouadi**

### Objectif
Concevoir un robot mobile qui repère, attrape, différencie et dépose des canettes en fonction de leur couleur.

### Timeline
- **Challenge:** 15 janvier 2027
- **Fin semestre:** 16 janvier 2027

---

## Bring-up du PCB

Cette section décrit tous les tests à réaliser pour valider une carte neuve. Les tests se font **dans l'ordre** : chaque test suppose que les précédents sont réussis.

### Matériel nécessaire
- Multimètre et oscilloscope numérique
- Source d'alimentation de la carte : **[À COMPLÉTER : batterie LiPo 2S 7,4 V ou alimentation de labo]**
- STLINK-V3MINIE (programmation et débogage SWD)
- Logiciels : STM32CubeProgrammer, STM32CubeIDE

### Repérage des points de test
<!-- Ajouter une photo de la carte avec les test points annotés -->
<!-- ![Carte annotée](docs/images/pcb_annote.jpg) -->

| Test point | Signal | Valeur attendue |
|---|---|---|
| TP? | 3,3 V | 3,2 V – 3,4 V |
| TP? | 5 V | 4,9 V – 5,1 V |
| TP? | GND | 0 V |

### Tests d'alimentation

#### Test 1 : Soudure du solder bridge
- **Objectif :** **[À COMPLÉTER : rôle du solder bridge]**
- **Démarche :** souder le pont **[À COMPLÉTER : nom, ex. SB1]**, puis vérifier au multimètre (mode continuité) que les deux pastilles sont reliées et qu'il n'y a pas de court-circuit avec la masse.
- **Test réussi si :** continuité entre les deux pastilles, pas de continuité avec GND.
- **Test échoué si :** pas de continuité (soudure froide) ou court-circuit vers GND.
- **Résultat :** ✅ **[À COMPLÉTER : date]**
- **Problèmes rencontrés et solutions :** aucun.

#### Test 2 : Tension 3,3 V
- **Objectif :** vérifier que le régulateur fournit 3,3 V au microcontrôleur et aux capteurs.
- **Matériel :** oscilloscope numérique (masse de la sonde sur **[À COMPLÉTER : TP GND]**).
- **Démarche :** alimenter la carte par **[À COMPLÉTER : source d'alimentation]**, mesurer sur les test points **[À COMPLÉTER : TP_3V3, ...]**.
- **Test réussi si :** tension entre 3,2 V et 3,4 V, stable.
- **Test échoué si :** tension absente, inférieure à 3,2 V, ou qui oscille.
- **Résultat :** ✅ 3,3 V mesurés sur **[À COMPLÉTER : liste des TP]** (**[À COMPLÉTER : date]**)
- **Problèmes rencontrés et solutions :** aucun.

#### Test 3 : Masse et LEDs d'alimentation
- **Objectif :** vérifier la continuité de la masse et l'allumage des LEDs d'alimentation.
- **Démarche :** vérifier la continuité GND entre **[À COMPLÉTER : points]**, puis mettre sous tension et observer les LEDs **[À COMPLÉTER : noms des LEDs]**.
- **Test réussi si :** continuité GND correcte et chaque LED d'alimentation s'allume.
- **Test échoué si :** une LED reste éteinte (vérifier son sens et sa résistance).
- **Résultat :** ✅ **[À COMPLÉTER : date]**

### Tests des composants de la carte

#### Test 4 : Connexion SWD au STM32
- **Objectif :** vérifier que le microcontrôleur est vivant et programmable par l'interface SWD.
- **Matériel :** STLINK-V3MINIE, STM32CubeProgrammer, fils de liaison.
- **Démarche :**
  1. Alimenter la carte (les LEDs d'alimentation doivent s'allumer).
  2. Relier le connecteur SWD de la carte au ST-Link : SWDIO, SWCLK, GND, T_VCC (3,3 V), NRST.
  3. Dans STM32CubeProgrammer : ST-LINK, port SWD, mode Normal → Connect.
  4. Lire la mémoire Flash à l'adresse 0x08000000.
- **Test réussi si :** « Connected », Device = STM32G43x/G44x, CPU Cortex-M4, Flash 128 KB, lecture mémoire réussie.
- **Test échoué si :** « No STM32 target found » / « Unable to get core ID ».
- **Résultat :** ✅ 17/11/2026

![Connexion SWD réussie](docs/images/swd_connected.png)

- **Problèmes rencontrés et solutions :** aucun.

#### Test 5 : Horloge interne HSI (clignotement)
*À venir.*

#### Test 6 : LEDs (chenillard)
*À venir.*

#### Test 7 : Quartz HSE
*À venir.*

#### Test 8 : USART (rebouclage TX → RX)
*À venir.*

### Tests des périphériques (un par un)

#### Test 9 : APDS-9960 (couleur)
*À venir.*

#### Test 10 : VL53L0X (distance)
*À venir.*

#### Test 11 : MPU6050 (IMU)
*À venir.*

#### Test 12 : Moteurs + DRV8833
*À venir.*

#### Test 13 : Encodeurs
*À venir.*

#### Test 14 : Servo de la pince
*À venir.*

#### Test 15 : Liaison UART avec l'ESP32
*À venir.*

### Bilan du bring-up

| Test | Résultat | Date |
|---|---|---|
| 1. Solder bridge | ✅ | |
| 2. Tension 3,3 V | ✅ | |
| 3. Masse et LEDs d'alimentation | ✅ | |
| 4. Connexion SWD | ✅ | 17/11/2026 |
| 5. HSI | ⏳ | |
| 6. LEDs | ⏳ | |
| 7. HSE | ⏳ | |
| 8. USART | ⏳ | |
| 9 à 15. Périphériques | ⏳ | |

---

## Architecture logicielle
*À venir : diagrammes, objets actifs, machine à états du robot.*