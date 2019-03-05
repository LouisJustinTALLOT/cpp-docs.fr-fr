---
title: CWinApp et l'Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: cb45c8ffae15628b0b99a1ebcd962d88d845f83b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266261"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp et l'Assistant Application MFC

Lorsqu’il crée une application squelette, l’Assistant Application MFC déclare une classe d’application dérivée de [CWinApp](../mfc/reference/cwinapp-class.md). L’Assistant Application MFC génère également un fichier d’implémentation qui contient les éléments suivants :

- Une table des messages pour la classe d’application.

- Un constructeur de classe vide.

- Une variable qui déclare le seul et unique objet de la classe.

- Une implémentation standard de votre `InitInstance` fonction membre.

La classe d’application est placée dans l’en-tête du projet et les principaux fichiers sources. Les noms de la classe et les fichiers créés sont basés sur le nom du projet que vous indiquez dans l’Assistant Application MFC. Le moyen le plus simple pour afficher le code de ces classes est via [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code).

Les implémentations standard et le mappage de message fourni conviennent à de nombreuses fins, mais vous pouvez les modifier en fonction des besoins. Est la plus intéressante de ces implémentations le `InitInstance` fonction membre. En règle générale, vous allez ajouter du code à l’implémentation squelette de `InitInstance`.

## <a name="see-also"></a>Voir aussi

[CWinApp : La classe d’Application](../mfc/cwinapp-the-application-class.md)<br/>
[Fonctions membres CWinApp remplaçables](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Services CWinApp spéciaux](../mfc/special-cwinapp-services.md)
