---
title: "Notions de base de barre d’outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RT_TOOLBAR
dev_langs:
- C++
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 136b9f5dd36c9e4092b8e5c15ac1738541cf71f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-fundamentals"></a>Notions de base de barre d'outils
Cet article décrit l’implémentation MFC de base qui vous permet d’ajouter une barre d’outils par défaut pour votre application en sélectionnant une option dans l’Assistant Application. Les sujets abordés sont les suivantes :  
  
-   [L’option de la barre d’outils Assistant Application](#_core_the_appwizard_toolbar_option)  
  
-   [La barre d’outils dans le code](#_core_the_toolbar_in_code)  
  
-   [Modification de la ressource de barre d’outils](#_core_editing_the_toolbar_resource)  
  
-   [Plusieurs barres d’outils](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a>L’Option de barre d’outils Assistant Application  
 Pour obtenir une seule barre d’outils avec les boutons par défaut, sélectionnez l’option de la barre d’outils ancrage Standard dans la page fonctionnalités de l’Interface utilisateur. Cela ajoute du code à votre application qui :  
  
-   Crée l’objet de barre d’outils.  
  
-   Gère la barre d’outils, et notamment la possibilité pour ancrer ou faire flotter.  
  
##  <a name="_core_the_toolbar_in_code"></a>La barre d’outils dans le Code  
 La barre d’outils est un [CToolBar](../mfc/reference/ctoolbar-class.md) objet déclaré comme un membre de données de votre application **CMainFrame** classe. En d’autres termes, l’objet de barre d’outils est incorporé dans l’objet de fenêtre frame principale. Cela signifie que MFC crée la barre d’outils lorsqu’il crée la fenêtre frame et détruit la barre d’outils lorsqu’il détruit la fenêtre frame. La déclaration de classe partielle suivante, pour une application d’interface (multidocument MDI) document plusieurs, présente les membres de données pour une barre d’outils incorporée et une barre d’état incorporée. Il montre également la substitution de la `OnCreate` fonction membre.  
  
 [!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]  
  
 Création de la barre d’outils se produit dans **CMainFrame::OnCreate**. MFC appelle [OnCreate](../mfc/reference/cwnd-class.md#oncreate) après la création de la fenêtre pour le frame mais avant de devenir visible. La valeur par défaut `OnCreate` que l’Assistant Application génère d’effectue les tâches suivantes de la barre d’outils :  
  
1.  Appelle le `CToolBar` l’objet [créer](../mfc/reference/ctoolbar-class.md#create) fonction membre à créer sous-jacent [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objet.  
  
2.  Appels [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) pour charger les informations de ressource de barre d’outils.  
  
3.  Appelle des fonctions permettant d’ancrage flottante et info-bulles. Pour plus d’informations sur ces appels, consultez l’article [ancrées et flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md).  
  
> [!NOTE]
>  L’exemple général MFC [DOCKTOOL](../visual-cpp-samples.md) comprend des illustrations des anciennes et nouvelles barres d’outils MFC. Les barres d’outils qui utilisent **COldToolbar** nécessitent des appels à l’étape 2 pour `LoadBitmap` (au lieu de `LoadToolBar`) et `SetButtons`. Les nouvelles barres d’outils nécessitent des appels à `LoadToolBar`.  
  
 L’ancrage, flottant et outil conseils appels sont facultatifs. Vous pouvez supprimer des lignes à partir de `OnCreate` si vous préférez. Le résultat est une barre d’outils reste fixe, flottante ou re-Impossible d’et ne peut pas afficher les info-bulles.  
  
##  <a name="_core_editing_the_toolbar_resource"></a>Modification de la ressource de barre d’outils  
 La barre d’outils par défaut que vous obtenez avec l’Assistant Application est basée sur un **RT_TOOLBAR** ressource personnalisée, introduite dans la version 4.0 de MFC. Vous pouvez modifier cette ressource avec la [éditeur de barre d’outils](../windows/toolbar-editor.md). L’éditeur vous permet de facilement ajouter, supprimer et réorganiser les boutons. Il contienne un éditeur graphique pour les boutons qui sont très similaires à l’éditeur graphique en général dans Visual C++. Si vous avez modifié des barres d’outils dans les versions précédentes de Visual C++, vous trouverez la tâche beaucoup plus facile maintenant.  
  
 Pour vous connecter à un bouton de barre d’outils à une commande, attribuez au bouton un ID de commande, tel que `ID_MYCOMMAND`. Spécifiez l’ID de commande dans la page de propriétés du bouton dans l’éditeur de la barre d’outils. Puis créez une fonction de gestionnaire pour la commande (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md) pour plus d’informations).  
  
 Nouvelle [CToolBar](../mfc/reference/ctoolbar-class.md) fonctions membres fonctionnent avec les **RT_TOOLBAR** ressource. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) maintenant prend la place de [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) pour charger l’image bitmap des images de bouton de barre d’outils, et [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) pour définir les styles des boutons et lier avec les images bitmap.  
  
 Pour plus d’informations sur l’utilisation de l’éditeur de la barre d’outils, consultez [barre d’outils Éditeur](../windows/toolbar-editor.md).  
  
##  <a name="_core_multiple_toolbars"></a>Plusieurs barres d’outils  
 L’Assistant Application fournit une barre d’outils par défaut. Si vous avez besoin de plusieurs barres d’outils dans votre application, vous pouvez modéliser votre code pour les barres d’outils supplémentaires en fonction du code généré par l’Assistant pour la barre d’outils par défaut.  
  
 Si vous souhaitez afficher une barre d’outils à la suite d’une commande, vous devez :  
  
-   Créer une nouvelle ressource de barre d’outils avec la barre d’outils Éditeur, puis chargez-le dans `OnCreate` avec la [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) fonction membre.  
  
-   Incorporer un nouveau [CToolBar](../mfc/reference/ctoolbar-class.md) objet dans votre classe de fenêtre frame principale.  
  
-   Assurez-vous que les appels de la fonction appropriée dans `OnCreate` pour ancrer ou faire flotter la barre d’outils, définir les styles et ainsi de suite.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Implémentation de barre d’outils MFC (informations de vue d’ensemble des barres d’outils)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Ancrer et rendre flottantes les barres d’outils](../mfc/docking-and-floating-toolbars.md)  
  
-   [Barre d’outils info-bulles](../mfc/toolbar-tool-tips.md)  
  
-   Le [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classes  
  
-   [Utilisation du contrôle de barre d’outils](../mfc/working-with-the-toolbar-control.md)  
  
-   [À l’aide de vos anciennes barres d’outils](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de la barre d’outils MFC](../mfc/mfc-toolbar-implementation.md)

