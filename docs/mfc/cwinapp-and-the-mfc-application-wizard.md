---
title: CWinApp et l’Assistant Application MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 702c20fc9f303670d2add4ebf840785acff7750d
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026483"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp et l'Assistant Application MFC
Lorsqu’il crée une application squelette, l’Assistant Application MFC déclare une classe d’application dérivée de [CWinApp](../mfc/reference/cwinapp-class.md). L’Assistant Application MFC génère également un fichier d’implémentation qui contient les éléments suivants :  
  
-   Une table des messages pour la classe d’application.  
  
-   Un constructeur de classe vide.  
  
-   Une variable qui déclare le seul et unique objet de la classe.  
  
-   Une implémentation standard de votre `InitInstance` fonction membre.  
  
 La classe d’application est placée dans l’en-tête du projet et les principaux fichiers sources. Les noms de la classe et les fichiers créés sont basés sur le nom du projet que vous indiquez dans l’Assistant Application MFC. Le moyen le plus simple pour afficher le code de ces classes est via [affichage de classes](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
 Les implémentations standard et le mappage de message fourni conviennent à de nombreuses fins, mais vous pouvez les modifier en fonction des besoins. Est la plus intéressante de ces implémentations le `InitInstance` fonction membre. En règle générale, vous allez ajouter du code à l’implémentation squelette de `InitInstance`.  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : Classe d’Application](../mfc/cwinapp-the-application-class.md)   
 [Fonctions membres CWinApp remplaçables](../mfc/overridable-cwinapp-member-functions.md)   
 [Services CWinApp spéciaux](../mfc/special-cwinapp-services.md)

