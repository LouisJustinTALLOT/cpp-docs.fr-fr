---
description: 'En savoir plus sur : utilisation des fenêtres contenues'
title: Utilisation des fenêtres contenues
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 11beb998365a10a8126e37ecbf7388ec6177e659
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138214"
---
# <a name="using-contained-windows"></a>Utilisation des fenêtres contenues

ATL implémente les fenêtres contenues avec [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Une fenêtre contenue représente une fenêtre qui délègue ses messages à un objet conteneur au lieu de les gérer dans sa propre classe.

> [!NOTE]
> Vous n’avez pas besoin de dériver une classe de `CContainedWindowT` pour pouvoir utiliser des fenêtres contenues.

Avec les fenêtres contenues, vous pouvez superclasser une classe Windows existante ou une sous-classe dans une fenêtre existante. Pour créer une fenêtre qui surclasse une classe Windows existante, spécifiez d’abord le nom de la classe existante dans le constructeur de l' `CContainedWindowT` objet. Appelez ensuite `CContainedWindowT::Create` . Pour sous-classer une fenêtre existante, vous n’avez pas besoin de spécifier un nom de classe Windows (passer NULL au constructeur). Appelez simplement la `CContainedWindowT::SubclassWindow` méthode avec le handle de la fenêtre en cours de sous-classe.

En général, vous utilisez des fenêtres à relation contenant-contenu comme données membres d’une classe de conteneur. Le conteneur n’a pas besoin d’être une fenêtre ; Toutefois, il doit dériver de [CMessageMap](../atl/reference/cmessagemap-class.md).

Une fenêtre contenue peut utiliser des tables de messages de remplacement pour gérer ses messages. Si vous avez plusieurs fenêtres contenues, vous devez déclarer plusieurs tables de messages secondaires, chacune d’elles correspondant à une fenêtre distincte contenue.

## <a name="example"></a>Exemple

Voici un exemple de classe de conteneur avec deux fenêtres à relation contenant-contenu :

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Pour plus d’informations sur les fenêtres contenues, consultez l’exemple [SubEdit](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) .

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
