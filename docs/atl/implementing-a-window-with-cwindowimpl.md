---
title: Mise en œuvre d’une fenêtre avec CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319446"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Mise en œuvre d’une fenêtre avec CWindowImpl

Pour implémenter une `CWindowImpl`fenêtre, tirer une classe de . Dans votre classe dérivée, déclarez une carte de message et le gestionnaire de message fonctionne. Vous pouvez maintenant utiliser votre classe de trois façons différentes :

- [Créer une fenêtre basée sur une nouvelle classe Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Superclasse une classe Windows existante](#_atl_superclassing_an_existing_windows_class)

- [Sous-classez une fenêtre existante](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>Création d’une fenêtre basée sur une nouvelle classe Windows

`CWindowImpl`contient la [macro DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) pour déclarer les informations de classe Windows. Cette macro implémente la `GetWndClassInfo` fonction, qui utilise [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) pour définir les informations d’une nouvelle classe Windows. Lorsqu’on `CWindowImpl::Create` l’appelle, cette classe Windows est enregistrée et une nouvelle fenêtre est créée.

> [!NOTE]
> `CWindowImpl`passe NULL `DECLARE_WND_CLASS` à la macro, ce qui signifie ATL va générer un nom de classe Windows. Pour spécifier votre propre nom, passez `CWindowImpl`une corde à DECLARE_WND_CLASS dans votre classe dérivée.

## <a name="example"></a>Exemple

Voici un exemple d’une classe qui implémente une fenêtre basée sur une nouvelle classe Windows :

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Pour créer une fenêtre, `CMyWindow` créez une `Create` instance de la méthode, puis appelez la méthode.

> [!NOTE]
> Pour remplacer les informations par défaut `GetWndClassInfo` de la classe Windows, implémentez la méthode dans votre catégorie dérivée en définissant les `CWndClassInfo` membres aux valeurs appropriées.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>Superclasser une classe Windows existante

La macro [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) vous permet de créer une fenêtre qui superclasse une classe Windows existante. Spécifier `CWindowImpl`cette macro dans votre classe dérivée. Comme toute autre fenêtre ATL, les messages sont traités par une carte de message.

Lorsque vous utilisez DECLARE_WND_SUPERCLASS, une nouvelle classe Windows sera enregistrée. Cette nouvelle classe sera la même que la classe existante que `CWindowImpl::WindowProc` vous spécifiez, mais remplacera la procédure de fenêtre par (ou avec votre fonction qui l’emporte sur cette méthode).

## <a name="example"></a>Exemple

Voici un exemple d’une classe qui superclasse la classe Edit standard :

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Pour créer la fenêtre Edit surclassée, créez une instance de `CMyEdit` la méthode et appelez ensuite la `Create` méthode.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>Sous-classe d’une fenêtre existante

Pour sous-classer une fenêtre `CWindowImpl` existante, extraire une classe et déclarez une carte de message, comme dans les deux cas précédents. Notez, cependant, que vous ne spécifiez aucune information de classe Windows, puisque vous sous-classez une fenêtre déjà existante.

Au lieu `Create`d’appeler, appelez `SubclassWindow` et passez-le la poignée à la fenêtre existante que vous voulez sous-classe. Une fois que la fenêtre est `CWindowImpl::WindowProc` sous-classée, elle utilisera (ou votre fonction qui l’emporte sur cette méthode) pour diriger les messages vers la carte de message. Pour détacher une fenêtre sous-classée `UnsubclassWindow`de votre objet, appelez . La procédure de fenêtre d’origine de la fenêtre sera alors restaurée.

## <a name="see-also"></a>Voir aussi

[Mise en œuvre d’une fenêtre](../atl/implementing-a-window.md)
