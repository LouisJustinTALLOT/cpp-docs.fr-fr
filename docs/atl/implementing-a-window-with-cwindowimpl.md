---
description: 'En savoir plus sur : implémentation d’une fenêtre avec CWindowImpl'
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
ms.openlocfilehash: 4010450b21a7cbbb4c4f1e4b7a39f594ce1e466e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152879"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implémentation d’une fenêtre avec CWindowImpl

Pour implémenter une fenêtre, dérivez une classe de `CWindowImpl` . Dans votre classe dérivée, déclarez une table des messages et les fonctions de gestionnaire de messages. Vous pouvez désormais utiliser votre classe de trois façons différentes :

- [Créer une fenêtre basée sur une nouvelle classe Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Superclasser une classe Windows existante](#_atl_superclassing_an_existing_windows_class)

- [Sous-classe une fenêtre existante](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Création d’une fenêtre basée sur une nouvelle classe Windows

`CWindowImpl` contient la macro [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) pour déclarer des informations de classe Windows. Cette macro implémente la `GetWndClassInfo` fonction, qui utilise [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) pour définir les informations d’une nouvelle classe Windows. Lorsque `CWindowImpl::Create` est appelé, cette classe Windows est inscrite et une nouvelle fenêtre est créée.

> [!NOTE]
> `CWindowImpl` passe la valeur NULL à la `DECLARE_WND_CLASS` macro, ce qui signifie qu’ATL générera un nom de classe Windows. Pour spécifier votre propre nom, transmettez une chaîne à DECLARE_WND_CLASS dans votre `CWindowImpl` classe dérivée de.

## <a name="example-implement-a-window"></a>Exemple : implémenter une fenêtre

Voici un exemple de classe qui implémente une fenêtre basée sur une nouvelle classe Windows :

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Pour créer une fenêtre, créez une instance de, puis `CMyWindow` appelez la `Create` méthode.

> [!NOTE]
> Pour substituer les informations de classe Windows par défaut, implémentez la `GetWndClassInfo` méthode dans votre classe dérivée en affectant `CWndClassInfo` aux membres les valeurs appropriées.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a> Superclassement d’une classe Windows existante

La macro [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) vous permet de créer une fenêtre qui surclasse une classe Windows existante. Spécifiez cette macro dans votre `CWindowImpl` classe dérivée de. À l’instar de toute autre fenêtre ATL, les messages sont gérés par une table des messages.

Quand vous utilisez DECLARE_WND_SUPERCLASS, une nouvelle classe Windows est inscrite. Cette nouvelle classe sera la même que la classe existante que vous spécifiez, mais elle remplacera la procédure de fenêtre par `CWindowImpl::WindowProc` (ou par votre fonction qui remplace cette méthode).

## <a name="example-superclass-the-edit-class"></a>Exemple : superclasser la classe d’édition

Voici un exemple de classe qui superclasse la classe d’édition standard :

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Pour créer la fenêtre de modification superclassée, créez une instance de, puis `CMyEdit` appelez la `Create` méthode.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a> Sous-classement d’une fenêtre existante

Pour obtenir la sous-classe d’une fenêtre existante, dérivez une classe de `CWindowImpl` et déclarez une table des messages, comme dans les deux cas précédents. Notez, toutefois, que vous ne spécifiez pas d’informations sur les classes Windows, car vous allez sous-classe une fenêtre déjà existante.

Au lieu d’appeler `Create` , appelez `SubclassWindow` et transmettez-lui le descripteur de la fenêtre existante que vous souhaitez sous-classe. Une fois la fenêtre sous-classée, elle utilise `CWindowImpl::WindowProc` (ou votre fonction qui remplace cette méthode) pour diriger les messages vers la table des messages. Pour détacher une fenêtre sous-classée de votre objet, appelez `UnsubclassWindow` . La procédure de fenêtre d’origine de la fenêtre sera alors restaurée.

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)
