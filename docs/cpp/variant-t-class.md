---
description: 'En savoir plus sur : classe _variant_t'
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
ms.openlocfilehash: e720d78e6f7fd22fc369d4b39804260892e235c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116611"
---
# <a name="_variant_t-class"></a>_variant_t (classe)

**Spécifique à Microsoft**

Un objet **_variant_t** encapsule le `VARIANT` type de données. La classe gère l’allocation et la désallocation des ressources et effectue des appels de fonction vers `VariantInit` et `VariantClear` selon les besoins.

### <a name="construction"></a>Construction

| Nom | Description |
|--|--|
| [_variant_t](../cpp/variant-t-variant-t.md) | Construit un objet **_variant_t** . |

### <a name="operations"></a>Operations

| Nom | Description |
|--|--|
| [Attacher](../cpp/variant-t-attach.md) | Attache un `VARIANT` objet dans l’objet **_variant_t** . |
| [Clear](../cpp/variant-t-clear.md) | Efface l’objet encapsulé `VARIANT` . |
| [ChangeType](../cpp/variant-t-changetype.md) | Remplace le type de l’objet **_variant_t** par le spécifié `VARTYPE` . |
| [Détacher](../cpp/variant-t-detach.md) | Détache l' `VARIANT` objet encapsulé de cet objet **_variant_t** . |
| [SetString](../cpp/variant-t-setstring.md) | Assigne une chaîne à cet objet **_variant_t** . |

### <a name="operators"></a>Opérateurs

| Nom | Description |
|--|--|
| [Opérateur =](../cpp/variant-t-operator-equal.md) | Assigne une nouvelle valeur à un objet **_variant_t** existant. |
| [opérateur = =, ! =](../cpp/variant-t-relational-operators.md) | Compare deux objets **_variant_t** pour vérifier leur égalité ou leur inégalité. |
| [Extracteurs](../cpp/variant-t-extractors.md) | Extrayez les données de l' `VARIANT` objet encapsulé. |

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :**\<comutil.h>

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)
