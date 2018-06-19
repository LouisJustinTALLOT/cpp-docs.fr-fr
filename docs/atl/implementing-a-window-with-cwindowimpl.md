---
title: Implémentation d’une fenêtre avec CWindowImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CWindowImpl
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9c1fc32d2265f6853c4dd34a3eb463609fca52b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356545"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implémentation d’une fenêtre avec CWindowImpl
Pour implémenter une fenêtre, dérivez une classe de `CWindowImpl`. Dans votre classe dérivée, déclarez une table des messages et les fonctions de gestionnaire de messages. Vous pouvez maintenant utiliser votre classe de trois façons différentes :  
  
-   [Créer une fenêtre basée sur une nouvelle classe Windows](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [Surclasser une classe Windows existante](#_atl_superclassing_an_existing_windows_class)  
  
-   [Sous-classer une fenêtre existante](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Création d’une fenêtre basée sur une nouvelle classe Windows  
 `CWindowImpl` contient le [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) macro pour déclarer les informations de classe Windows. Cette macro implémente la `GetWndClassInfo` (fonction), qui utilise [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) pour définir les informations d’une nouvelle classe de Windows. Lorsque `CWindowImpl::Create` est appelée, ce Windows classe est enregistrée et une nouvelle fenêtre est créée.  
  
> [!NOTE]
>  `CWindowImpl` passe **NULL** à la `DECLARE_WND_CLASS` (macro), ce qui signifie que ATL générera un nom de classe Windows. Pour spécifier votre propre nom, passez une chaîne à `DECLARE_WND_CLASS` dans votre `CWindowImpl`-classe dérivée.  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’une classe qui implémente une fenêtre basée sur une nouvelle classe Windows :  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]  
  
 Pour créer une fenêtre, créez une instance de `CMyWindow` , puis appelez le **créer** (méthode).  
  
> [!NOTE]
>  Pour remplacer les informations de classe Windows par défaut, vous devez implémenter la `GetWndClassInfo` méthode dans votre classe dérivée en définissant le `CWndClassInfo` membres sur les valeurs appropriées.  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a> Surclasser une classe Windows existante  
 Le [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) (macro) vous permet de créer une fenêtre qui superclasses un Windows existant classe. Spécifiez cette macro dans votre `CWindowImpl`-classe dérivée. Comme toute autre fenêtre ATL, les messages sont traités par une table des messages.  
  
 Lorsque vous utilisez `DECLARE_WND_SUPERCLASS`, une nouvelle classe Windows sera inscrit. Cette nouvelle classe doit être le même que la classe existante que vous spécifiez, mais remplacez la procédure de fenêtre avec `CWindowImpl::WindowProc` (ou avec votre fonction qui substitue cette méthode).  
  
## <a name="example"></a>Exemple  
 Suivant est un exemple d’une classe que l’édition standard de superclasses classe :  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]  
  
 Pour créer la fenêtre d’édition superclasse, créez une instance de `CMyEdit` , puis appelez le **créer** (méthode).  
  
##  <a name="_atl_subclassing_an_existing_window"></a> Sous-classer une fenêtre existante  
 Pour sous-classer une fenêtre existante, dérivez une classe de `CWindowImpl` et déclarez une table des messages, comme dans les deux cas précédents. Notez, toutefois, que vous ne spécifiez pas de toutes les informations de classe Windows, car vous allez sous-classer une fenêtre qui existe déjà.  
  
 Au lieu d’appeler **créer**, appelez `SubclassWindow` et lui passer le descripteur dans la fenêtre existante que vous souhaitez sous-classer. Une fois que la fenêtre est sous-classée, elle utilisera `CWindowImpl::WindowProc` (ou votre fonction qui substitue cette méthode) pour diriger les messages vers la table des messages. Pour détacher une fenêtre sous-classée de votre objet, appelez `UnsubclassWindow`. Procédure de fenêtre d’origine de la fenêtre est ensuite être restaurée.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une fenêtre](../atl/implementing-a-window.md)

