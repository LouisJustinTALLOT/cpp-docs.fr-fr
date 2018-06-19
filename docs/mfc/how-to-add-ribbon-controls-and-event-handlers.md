---
title: 'Comment : ajouter des contrôles de ruban et des gestionnaires d’événements | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 176323137b2ace0d27d9de162da7fa022441aa88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344417"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Comment : ajouter des contrôles de ruban et des gestionnaires d'événements
Contrôles de ruban sont des éléments, tels que des boutons et des zones de liste déroulante, que vous ajoutez à panneaux. Les panneaux sont des zones de la barre du ruban qui affichent un groupe de contrôles connexes.  
  
 Dans cette rubrique, vous ouvrir le Concepteur de ruban, ajouter un bouton et puis de lier un événement qui affiche « Hello World ».  
  
### <a name="to-open-the-ribbon-designer"></a>Pour ouvrir le Concepteur de ruban  
  
1.  Dans Visual Studio, sur le **vue** menu, cliquez sur **affichage des ressources**.  
  
2.  Dans **affichage des ressources**, double-cliquez sur la ressource de ruban pour l’afficher dans l’aire de conception.  
  
### <a name="to-add-a-button-and-an-event-handler"></a>Pour ajouter un bouton et un gestionnaire d’événements  
  
1.  À partir de la **barre d’outils**, cliquez sur **bouton** et faites-le glisser dans un panneau dans l’aire de conception.  
  
2.  Cliquez avec le bouton droit, puis cliquez sur **ajouter un gestionnaire d’événements**.  
  
3.  Dans le **Assistant Gestionnaire d’événements**, confirmez les paramètres par défaut, puis cliquez sur **ajouter et modifier des**. Pour plus d’informations, consultez [Assistant Gestionnaire d’événements](../ide/event-handler-wizard.md).  
  
4.  Dans l’éditeur de code, ajoutez le code suivant dans la fonction de gestionnaire de configuration :  
  
 ```  
    MessageBox((LPCTSTR)L"Hello World");

 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple RibbonGadgets : Application de Gadgets de ruban](../visual-cpp-samples.md)   
 [Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

