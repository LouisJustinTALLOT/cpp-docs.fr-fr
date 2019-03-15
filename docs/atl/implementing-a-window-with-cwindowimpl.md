---
title: Implémentation d’une fenêtre avec CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 265c3145d8ceacae540286f72939dc046e7c8b35
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818074"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implémentation d’une fenêtre avec CWindowImpl

Pour implémenter une fenêtre, dérivez une classe de `CWindowImpl`. Dans votre classe dérivée, déclarez une table des messages et les fonctions de gestionnaire de message. Vous pouvez maintenant utiliser votre classe de trois façons différentes :

- [Créer une fenêtre basée sur une nouvelle classe Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Surclasser une classe Windows existante](#_atl_superclassing_an_existing_windows_class)

- [Sous-classe une fenêtre existante](#_atl_subclassing_an_existing_window)

##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Création d’une fenêtre basée sur une nouvelle classe Windows

`CWindowImpl` contient le [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) macro pour déclarer des informations sur la classe Windows. Cette macro implémente la `GetWndClassInfo` (fonction), qui utilise [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) pour définir les informations d’une nouvelle classe de Windows. Lorsque `CWindowImpl::Create` est appelée, cette Windows classe est enregistrée et une nouvelle fenêtre est créée.

> [!NOTE]
>  `CWindowImpl` transmet la valeur NULL pour le `DECLARE_WND_CLASS` macro, ce qui signifie que ATL générera un nom de classe Windows. Pour spécifier votre propre nom, passez une chaîne à DECLARE_WND_CLASS dans votre `CWindowImpl`-classe dérivée.

## <a name="example"></a>Exemple

Voici un exemple d’une classe qui implémente une fenêtre basée sur une nouvelle classe de Windows :

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Pour créer une fenêtre, créez une instance de `CMyWindow` , puis appelez le `Create` (méthode).

> [!NOTE]
>  Pour remplacer les informations de classe Windows par défaut, vous devez implémenter le `GetWndClassInfo` méthode dans votre classe dérivée en définissant le `CWndClassInfo` membres sur les valeurs appropriées.

##  <a name="_atl_superclassing_an_existing_windows_class"></a> Surclasser une classe Windows existante

Le [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) macro vous permet de créer une fenêtre qui surclasse une Windows existant classe. Spécifiez cette macro dans votre `CWindowImpl`-classe dérivée. Comme toute autre fenêtre ATL, les messages sont traités par une table des messages.

Lorsque vous utilisez DECLARE_WND_SUPERCLASS, une nouvelle classe de Windows sera enregistrée. Cette nouvelle classe doit être le même que la classe existante que vous spécifiez, mais remplacez la procédure de fenêtre avec `CWindowImpl::WindowProc` (ou avec votre fonction qui substitue cette méthode).

## <a name="example"></a>Exemple

Suivant est un exemple d’une classe qui surclasse l’édition standard classe :

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Pour créer la fenêtre d’édition superclasse, créez une instance de `CMyEdit` , puis appelez le `Create` (méthode).

##  <a name="_atl_subclassing_an_existing_window"></a> Sous-classement d’une fenêtre existante

Pour sous-classer une fenêtre existante, dérivez une classe de `CWindowImpl` et déclarez une table des messages, comme dans les deux cas précédents. Notez, toutefois, que vous ne spécifiez pas les informations de classe Windows, car vous allez sous-classer une fenêtre déjà existante.

Au lieu d’appeler `Create`, appelez `SubclassWindow` et passez-lui le handle vers la fenêtre existante que vous souhaitez la sous-classe. Une fois que la fenêtre est sous-classée, il utilisera `CWindowImpl::WindowProc` (ou votre fonction qui substitue cette méthode) pour diriger les messages vers la table des messages. Pour détacher une fenêtre sous-classé à partir de votre objet, appelez `UnsubclassWindow`. Procédure de fenêtre d’origine de la fenêtre est ensuite restaurée.

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)
