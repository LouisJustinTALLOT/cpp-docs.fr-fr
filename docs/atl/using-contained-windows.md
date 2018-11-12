---
title: À l’aide de la relation contenant-contenu Windows
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 800ae7cab5fd99bfa140b481f87b1615ff5b2a13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485369"
---
# <a name="using-contained-windows"></a>À l’aide de la relation contenant-contenu Windows

ATL implémente les fenêtres contenues avec [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Une fenêtre contenue représente une fenêtre qui délègue ses messages à un objet conteneur au lieu de les gérer dans sa propre classe.

> [!NOTE]
>  Vous n’avez pas besoin de dériver une classe à partir de `CContainedWindowT` afin d’utiliser les fenêtres de relation contenant-contenus.

Avec windows de relation contenant-contenus, vous pouvez soit surclasser une classe Windows existante ou une sous-classe une fenêtre existante. Pour créer une fenêtre qui surclasse une Windows existants de classe, commencez par spécifier le nom de classe existant dans le constructeur pour le `CContainedWindowT` objet. Appelez ensuite `CContainedWindowT::Create`. Pour sous-classer une fenêtre existante, vous n’avez pas besoin de spécifier un nom de classe Windows (passez NULL au constructeur). Appelez simplement la `CContainedWindowT::SubclassWindow` méthode avec le handle vers la fenêtre sous-classée.

Vous utilisez généralement la relation contenant-contenus windows en tant que membres de données d’une classe de conteneur. Le conteneur pas nécessairement être une fenêtre ; Toutefois, elle doit dériver de [CMessageMap](../atl/reference/cmessagemap-class.md).

Une fenêtre contenue utiliser des cartes de messages de remplacement pour gérer ses messages. Si vous avez plusieurs fenêtres de relation contenant-contenu, vous devez déclarer que plusieurs autres tables des messages, correspondant chacune à une fenêtre distincte de relation contenant-contenue.

## <a name="example"></a>Exemple

Voici un exemple d’une classe de conteneur avec deux fenêtres de relation contenant-contenus :

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Pour plus d’informations sur les fenêtres de relation contenant-contenus, consultez la [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) exemple.

## <a name="see-also"></a>Voir aussi

[Classes de fenêtre](../atl/atl-window-classes.md)

