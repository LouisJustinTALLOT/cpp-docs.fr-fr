---
description: 'En savoir plus sur : modification de la fabrique de classe et du modèle d’agrégation par défaut'
title: Modification de la fabrique de classes et du modèle d’agrégation par défaut
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
ms.openlocfilehash: b25dc1c2cf3378532f02b1c0d5ba56cd43ee4ae4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148276"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Modification de la fabrique de classes et du modèle d’agrégation par défaut

ATL utilise [CComCoClass](../atl/reference/ccomcoclass-class.md) pour définir la fabrique de classe et le modèle d’agrégation par défaut pour votre objet. `CComCoClass` spécifie les deux macros suivantes :

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) Déclare que la fabrique de classe est [CComClassFactory](../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) Déclare que votre objet peut être agrégé.

Vous pouvez remplacer l’une de ces valeurs par défaut en spécifiant une autre macro dans votre définition de classe. Par exemple, pour utiliser [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) au lieu de `CComClassFactory` , spécifiez la macro [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) :

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

Deux autres macros qui définissent une fabrique de classes sont [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) et [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

ATL utilise également le **`typedef`** mécanisme pour implémenter le comportement par défaut. Par exemple, la macro DECLARE_AGGREGATABLE utilise **`typedef`** pour définir un type appelé `_CreatorClass` , qui est ensuite référencé dans tous les ATL. Notez que dans une classe dérivée, un qui **`typedef`** utilise le même nom que celui de la classe de base **`typedef`** génère ATL en utilisant votre définition et en substituant le comportement par défaut.

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Agrégation et macros de fabrique de classes](../atl/reference/aggregation-and-class-factory-macros.md)
