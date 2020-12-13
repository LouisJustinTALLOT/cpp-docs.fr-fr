---
description: 'En savoir plus sur : optimisation de la persistance et de l’initialisation'
title: Optimisation de la persistance et de l'initialisation
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 440239daa0ecfc4a5955a0ccbecb33bf801da7ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330155"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimisation de la persistance et de l'initialisation

Par défaut, la persistance et l'initialisation dans un contrôle sont gérées par la fonction membre `DoPropExchange`. Dans un contrôle classique, cette fonction contient des appels à plusieurs fonctions **PX_** ( `PX_Color` , `PX_Font` , etc.), une pour chaque propriété.

L'avantage de cette approche est qu'une seule implémentation `DoPropExchange` peut être utilisée pour l'initialisation, pour la persistance au format binaire et pour la persistance au soi-disant format "conteneur de propriétés" utilisé par certains conteneurs. Cette unique fonction fournit toutes les informations sur les propriétés et leurs valeurs par défaut dans un emplacement pratique.

Toutefois, cette généralité se produit au détriment de l'efficacité. Les fonctions de **PX_** bénéficient de leur flexibilité grâce à des implémentations à plusieurs couches qui sont fondamentalement moins efficaces que les approches plus directes, mais moins flexibles. En outre, si un contrôle passe une valeur par défaut à une fonction **PX_** , cette valeur par défaut doit être fournie à chaque fois, même dans les situations où la valeur par défaut ne peut pas nécessairement être utilisée. Si la génération de la valeur par défaut est une tâche non triviale (par exemple, si la valeur est obtenue à partir d’une propriété ambiante), le travail supplémentaire non nécessaire est effectué dans les cas où la valeur par défaut n’est pas utilisée.

Vous pouvez améliorer les performances de persistance binaire de votre contrôle en remplaçant sa fonction `Serialize`. L'implémentation par défaut de cette fonction membre passe un appel à votre fonction `DoPropExchange`. En la remplaçant, vous pouvez fournir une implémentation plus directe pour la persistance binaire. Par exemple, observez la fonction `DoPropExchange` suivante :

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Pour améliorer les performances de la persistance binaire de ce contrôle, vous pouvez remplacer la fonction `Serialize` comme suit :

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

La variable locale `dwVersion` peut être utilisée pour détecter la version de l'état persistant chargé ou enregistré du contrôle. Vous pouvez utiliser cette variable au lieu d’appeler [CPropExchange :: GetVersion](reference/cpropexchange-class.md#getversion).

Pour économiser un peu d’espace dans le format persistant pour une propriété **bool** (et pour qu’il soit compatible avec le format produit par `PX_Bool` ), vous pouvez stocker la propriété sous la forme d’un **octet**, comme suit :

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Notez que dans le cas de chargement, une variable temporaire est utilisée, puis sa valeur est assignée, au lieu d’effectuer un cast *m_boolProp* en référence d' **octet** . La technique de conversion entraînerait la modification d’un seul octet de *m_boolProp* , laissant les octets restants non initialisés.

Pour le même contrôle, vous pouvez optimiser l’initialisation du contrôle en remplaçant [COleControl :: OnResetState](reference/colecontrol-class.md#onresetstate) comme suit :

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Bien que les fonctions `Serialize` et `OnResetState` aient été substituées, la fonction `DoPropExchange` doit être conservée intacte, car elle est encore utilisée pour la persistance au format de conteneur de propriétés. Il est important de conserver ces trois fonctions pour garantir que le contrôle gère ses propriétés de manière cohérente, quel que soit le mécanisme de persistance utilisé par le conteneur.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : optimisation](mfc-activex-controls-optimization.md)
