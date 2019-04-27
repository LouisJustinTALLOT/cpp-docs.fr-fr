---
title: Modification de la fabrique de classe par défaut et le modèle d’agrégation
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: 94f9ecd85e09cb3916b518d71b904961042142e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223148"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Modification de la fabrique de classe par défaut et le modèle d’agrégation

ATL utilise [CComCoClass](../atl/reference/ccomcoclass-class.md) pour définir le modèle par défaut classe factory et d’agrégation pour votre objet. `CComCoClass` Spécifie les deux macros suivantes :

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) déclare la fabrique de classe [CComClassFactory](../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) déclare que votre objet peut être agrégé.

Vous pouvez remplacer ces valeurs par défaut en spécifiant une autre macro dans votre définition de classe. Par exemple, pour utiliser [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) au lieu de `CComClassFactory`, spécifiez la [macro DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) macro :

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

Deux autres macros qui définissent une fabrique de classe sont [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) et [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

ATL utilise également le **typedef** mécanisme pour implémenter le comportement par défaut. Par exemple, la macro DECLARE_AGGREGATABLE utilise **typedef** pour définir un type appelé `_CreatorClass`, qui est ensuite référencé dans ATL. Notez que dans une classe dérivée, un **typedef** à l’aide du même nom que la classe de base **typedef** entraîne ATL à l’aide de votre définition et la substitution du comportement par défaut.

## <a name="see-also"></a>Voir aussi

[Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Agrégation et macros de fabrique de classe](../atl/reference/aggregation-and-class-factory-macros.md)
