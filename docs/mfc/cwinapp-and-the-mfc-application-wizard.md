---
description: 'En savoir plus sur les éléments suivants : CWinApp et l’Assistant Application MFC'
title: CWinApp et l'Assistant Application MFC
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1ce1f0a84aa5a0f123f9fa8654d1ce286c47d1d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309262"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp et l'Assistant Application MFC

Lorsqu’il crée une application squelette, l’Assistant Application MFC déclare une classe d’application dérivée de [CWinApp](reference/cwinapp-class.md). L’Assistant Application MFC génère également un fichier d’implémentation qui contient les éléments suivants :

- Une table des messages pour la classe d’application.

- Constructeur de classe vide.

- Variable qui déclare le seul objet de la classe.

- Implémentation standard de votre `InitInstance` fonction membre.

La classe d’application est placée dans l’en-tête du projet et les fichiers sources principaux. Les noms de la classe et des fichiers créés sont basés sur le nom de projet que vous fournissez dans l’Assistant Application MFC. Le moyen le plus simple d’afficher le code de ces classes est de [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code).

Les implémentations standard et la table des messages fournies conviennent à de nombreuses fins, mais vous pouvez les modifier si nécessaire. La fonction membre est le plus intéressant de ces implémentations `InitInstance` . En général, vous allez ajouter du code à l’implémentation squelettique de `InitInstance` .

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](cwinapp-the-application-class.md)<br/>
[Fonctions membres CWinApp remplaçables](overridable-cwinapp-member-functions.md)<br/>
[Services CWinApp spéciaux](special-cwinapp-services.md)
