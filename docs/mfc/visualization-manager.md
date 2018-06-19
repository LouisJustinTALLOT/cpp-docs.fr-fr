---
title: Gestionnaire de visualisation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40d16e1373d347b4a715cd6f073211796913bd21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384213"
---
# <a name="visualization-manager"></a>Gestionnaire de visualisation
Le gestionnaire visuel est un objet qui contrôle l'apparence d'une application entière. Il agit comme une classe unique dans laquelle vous pouvez insérer l'intégralité du code de dessin pour votre application. La bibliothèque MFC inclut plusieurs gestionnaires visuels. Vous pouvez également créer votre propre gestionnaire visuel si vous souhaitez créer une vue personnalisée pour votre application. Les illustrations suivantes montrent la même application lorsque différents gestionnaires visuels sont activés :  
  
 ![MyApp rendu par CMFCVisualManagerWindows](../mfc/media/vmwindows.png "vmwindows")  
MyApp qui utilise le gestionnaire visuel CMFCVisualManagerWindows  
  
 ![MyApp rendu par CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "vmvs2005")  
MyApp qui utilise le gestionnaire visuel CMFCVisualManagerVS2005  
  
 ![MyApp rendu par CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "vmofficexp")  
MyApp qui utilise le gestionnaire visuel CMFCVisualManagerOfficeXP  
  
 ![MyApp rendu par CMFCVisualManagerOffice2003](../mfc/media/vmoffice2003.png "vmoffice2003")  
MyApp qui utilise le gestionnaire visuel CMFCVisualManagerOffice2003  
  
 ![MyApp rendu par CMFCVisualManagerOffice2007](../mfc/media/msoffice2007.png "msoffice2007")  
MyApp qui utilise le gestionnaire visuel CMFCVisualManagerOffice2007  
  
 Par défaut, le gestionnaire visuel gère le code de dessin pour plusieurs éléments d'interface utilisateur graphique. Pour fournir des éléments d'interface utilisateur personnalisés, vous devez remplacer les méthodes de dessin associées du gestionnaire visuel. Pour obtenir la liste de ces méthodes, consultez [CMFCVisualManager classe](../mfc/reference/cmfcvisualmanager-class.md). Les méthodes que vous pouvez remplacer pour fournir une apparence personnalisée sont toutes les méthodes qui commencent par `OnDraw`.  
  
 Votre application ne peut avoir qu'un seul objet `CMFCVisualManager`. Pour obtenir un pointeur vers le Gestionnaire visuel pour votre application, appelez la fonction statique [CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance). Étant donné que tous les gestionnaires visuels héritent de `CMFCVisualManager`, la méthode `CMFCVisualManager::GetInstance` obtient un pointeur vers le gestionnaire visuel approprié, même si vous créez un gestionnaire visuel personnalisé.  
  
 Si vous voulez créer un gestionnaire visuel personnalisé, vous devez le dériver d'un gestionnaire visuel qui existe déjà. La classe de dérivation par défaut est `CMFCVisualManager`. Toutefois, vous pouvez utiliser un autre gestionnaire visuel s'il ressemble plus à ce que vous souhaitez pour votre application. Par exemple, si vous souhaitez utiliser le gestionnaire visuel `CMFCVisualManagerOffice2007`, mais modifier uniquement l'apparence des séparateurs, vous pouvez dériver votre classe personnalisée de `CMFCVisualManagerOffice2007`. Dans ce scénario, vous devez remplacer uniquement les méthodes de dessin des séparateurs.  
  
 Deux méthodes sont possibles pour utiliser un gestionnaire visuel spécifique pour votre application. Consiste à appeler la [CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) (méthode) et passez le Gestionnaire visuel approprié en tant que paramètre. L'exemple de code suivant montre comment utiliser le gestionnaire visuel `CMFCVisualManagerVS2005` avec cette méthode :  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```  
  
 L'autre méthode permettant d'utiliser un gestionnaire visuel dans votre application est de le créer manuellement. L'application utilise alors ce nouveau gestionnaire visuel pour l'intégralité du rendu. Toutefois, comme il ne peut y avoir qu'un objet `CMFCVisualManager` par application, vous devrez supprimer le gestionnaire visuel actuel avant d'en créer un. Dans l'exemple suivant, `CMyVisualManager` est un gestionnaire visuel personnalisé dérivé de `CMFCVisualManager`. La méthode suivante modifie le gestionnaire visuel utilisé pour afficher votre application, selon un index :  
  
```  
void CMyApp::SetSkin (int index)  
{  
    if (CMFCVisualManager::GetInstance() != NULL)  
 {  
    delete CMFCVisualManager::GetInstance();

 }  
 
    switch (index)  
 {  
    case DEFAULT_STYLE: *// The following statement creates a new CMFCVisualManager  
    CMFCVisualManager::GetInstance();
break;  
 
    case CUSTOM_STYLE:  
    new CMyVisualManager;  
    break; 
 
    default: 
    CMFCVisualManager::GetInstance();
break;  
 }  
 
    CMFCVisualManager::GetInstance()->RedrawAll();

} 
```  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager, classe](../mfc/reference/cmfcvisualmanager-class.md)
