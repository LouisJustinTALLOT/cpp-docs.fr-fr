---
title: CWinApp et l'Assistant Application MFC
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1a46842d7b4d6a588da585d63e2ad56982bb0ff8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447041"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp et l'Assistant Application MFC

Lorsqu’il crée une application squelette, l’Assistant Application MFC déclare une classe d’application dérivée de [CWinApp](../mfc/reference/cwinapp-class.md). L’Assistant Application MFC génère également un fichier d’implémentation qui contient les éléments suivants :

- Une table des messages pour la classe d’application.

- Constructeur de classe vide.

- Variable qui déclare le seul objet de la classe.

- Implémentation standard de votre fonction membre `InitInstance`.

La classe d’application est placée dans l’en-tête du projet et les fichiers sources principaux. Les noms de la classe et des fichiers créés sont basés sur le nom de projet que vous fournissez dans l’Assistant Application MFC. Le moyen le plus simple d’afficher le code de ces classes est de [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code).

Les implémentations standard et la table des messages fournies conviennent à de nombreuses fins, mais vous pouvez les modifier si nécessaire. La fonction membre `InitInstance` est le plus intéressant de ces implémentations. En général, vous allez ajouter du code à l’implémentation squelettique de `InitInstance`.

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)<br/>
[Fonctions membres CWinApp remplaçables](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Services CWinApp spéciaux](../mfc/special-cwinapp-services.md)
