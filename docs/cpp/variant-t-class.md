---
title: _variant_t (classe)
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: 69976cab9caed653a8278f80821569b613f690eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502737"
---
# <a name="variantt-class"></a>_variant_t (classe)

**Section spécifique à Microsoft**

Un **_variant_t** objet encapsule le `VARIANT` type de données. La classe gère l’allocation des ressources et la désallocation et effectue des appels de fonction à `VariantInit` et `VariantClear` selon le cas.

### <a name="construction"></a>Construction

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Construit un **_variant_t** objet.|

### <a name="operations"></a>Opérations

|||
|-|-|
|[Attacher](../cpp/variant-t-attach.md)|Attache un `VARIANT` de l’objet dans le **_variant_t** objet.|
|[Effacer](../cpp/variant-t-clear.md)|Efface le texte encapsulé `VARIANT` objet.|
|[ChangeType](../cpp/variant-t-changetype.md)|Change le type de la **_variant_t** objet au `VARTYPE`.|
|[Détacher](../cpp/variant-t-detach.md)|Détache encapsulé `VARIANT` objet à partir de ce **_variant_t** objet.|
|[SetString](../cpp/variant-t-setstring.md)|Assigne une chaîne à cet **_variant_t** objet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](../cpp/variant-t-operator-equal.md)|Assigne une nouvelle valeur à un existant **_variant_t** objet.|
|[opérateur ==, ! =](../cpp/variant-t-relational-operators.md)|Comparer deux **_variant_t** objets pour l’égalité ou d’inégalité.|
|[Extracteurs](../cpp/variant-t-extractors.md)|Extraire des données d’encapsulé `VARIANT` objet.|

**FIN de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

**En-tête :** \<comutil.h >

**Lib :** comsuppw.lib ou comsuppwd.lib (voir [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)