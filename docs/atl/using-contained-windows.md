---
title: Utilisation de Windows contenus
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329309"
---
# <a name="using-contained-windows"></a>Utilisation de Windows contenus

Les outils ATL contenaient des fenêtres avec [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Une fenêtre contenue représente une fenêtre qui délègue ses messages à un objet conteneur au lieu de les manipuler dans sa propre classe.

> [!NOTE]
> Vous n’avez pas besoin `CContainedWindowT` d’extraire une classe pour utiliser des fenêtres contenues.

Avec les fenêtres contenues, vous pouvez soit superclasser une classe Windows existante, soit sous-classer une fenêtre existante. Pour créer une fenêtre qui surclasse une classe Windows existante, spécifiez d’abord le nom de classe existant dans le constructeur de l’objet. `CContainedWindowT` Ensuite, `CContainedWindowT::Create`appelez . Pour sous-classer une fenêtre existante, vous n’avez pas besoin de spécifier un nom de classe Windows (passez NULL au constructeur). Il suffit `CContainedWindowT::SubclassWindow` d’appeler la méthode avec la poignée à la fenêtre étant sous-classée.

Vous utilisez généralement des fenêtres contenues en tant que membres de données d’une classe de conteneurs. Le conteneur n’a pas besoin d’être une fenêtre; cependant, il doit dériver de [CMessageMap](../atl/reference/cmessagemap-class.md).

Une fenêtre contenue peut utiliser d’autres cartes de messages pour gérer ses messages. Si vous avez plus d’une fenêtre contenue, vous devez déclarer plusieurs cartes de messages alternatives, chacune correspondant à une fenêtre contenue séparée.

## <a name="example"></a>Exemple

Voici un exemple d’une classe de conteneurs avec deux fenêtres contenues:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Pour plus d’informations sur les fenêtres contenues, consultez l’échantillon [SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
