---
title: Optimisation de la persistance et de l'initialisation
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 294d9c43f5f767329c04932c574485d7dca704e9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342135"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimisation de la persistance et de l'initialisation

Par défaut, la persistance et l'initialisation dans un contrôle sont gérées par la fonction membre `DoPropExchange`. Dans un contrôle type, cette fonction contient des appels à plusieurs **PX_** fonctions (`PX_Color`, `PX_Font`, et ainsi de suite), une pour chaque propriété.

L'avantage de cette approche est qu'une seule implémentation `DoPropExchange` peut être utilisée pour l'initialisation, pour la persistance au format binaire et pour la persistance au soi-disant format "conteneur de propriétés" utilisé par certains conteneurs. Cette unique fonction fournit toutes les informations sur les propriétés et leurs valeurs par défaut dans un emplacement pratique.

Toutefois, cette généralité se produit au détriment de l'efficacité. Le **PX_** fonctions obtiennent leur flexibilité via des implémentations multicouche qui sont fondamentalement moins efficaces que les approches plus directes, mais moins souples. En outre, si le contrôle passe une valeur par défaut à un **PX_** que valeur par défaut doit être fournie à chaque fois, même dans les situations où la valeur par défaut ne peut pas nécessairement être utilisée de la fonction. Si la génération de la valeur par défaut est une tâche non triviale (par exemple, si la valeur est obtenue à partir d’une propriété ambiante), le travail supplémentaire non nécessaire est effectué dans les cas où la valeur par défaut n’est pas utilisée.

Vous pouvez améliorer les performances de persistance binaire de votre contrôle en remplaçant sa fonction `Serialize`. L'implémentation par défaut de cette fonction membre passe un appel à votre fonction `DoPropExchange`. En la remplaçant, vous pouvez fournir une implémentation plus directe pour la persistance binaire. Par exemple, observez la fonction `DoPropExchange` suivante :

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Pour améliorer les performances de la persistance binaire de ce contrôle, vous pouvez remplacer la fonction `Serialize` comme suit :

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

La variable locale `dwVersion` peut être utilisée pour détecter la version de l'état persistant chargé ou enregistré du contrôle. Vous pouvez utiliser cette variable au lieu d’appeler [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion).

Pour enregistrer un peu d’espace dans le format persistant pour un **BOOL** propriété (et pour qu’il soit compatible avec le format produit par `PX_Bool`), vous pouvez stocker la propriété comme un **octets**, comme suit :

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Notez que, dans le cas de charge, une variable temporaire est utilisée et sa valeur est ensuite affectée, au lieu d’effectuer un cast *m_boolProp* à un **octets** référence. La technique entraînerait un seul octet de *m_boolProp* en cours de modification, en laissant les octets restants non initialisés.

Pour le même contrôle, vous pouvez optimiser l’initialisation du contrôle en substituant [COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) comme suit :

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Bien que les fonctions `Serialize` et `OnResetState` aient été substituées, la fonction `DoPropExchange` doit être conservée intacte, car elle est encore utilisée pour la persistance au format de conteneur de propriétés. Il est important de conserver ces trois fonctions pour garantir que le contrôle gère ses propriétés de manière cohérente, quel que soit le mécanisme de persistance utilisé par le conteneur.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)
