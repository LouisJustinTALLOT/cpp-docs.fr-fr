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
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187750"
---
# <a name="_variant_t-class"></a>_variant_t (classe)

**Section spécifique de Microsoft**

Un objet **_variant_t** encapsule le type de données `VARIANT`. La classe gère l’allocation et la désallocation des ressources et effectue des appels de fonction à `VariantInit` et `VariantClear` selon le cas.

### <a name="construction"></a>Construction

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|Construit un objet **_variant_t** .|

### <a name="operations"></a>Opérations

|||
|-|-|
|[Attacher](../cpp/variant-t-attach.md)|Attache un objet `VARIANT` dans l’objet **_variant_t** .|
|[Clear](../cpp/variant-t-clear.md)|Efface l’objet `VARIANT` encapsulé.|
|[ChangeType](../cpp/variant-t-changetype.md)|Remplace le type de l’objet **_variant_t** par le `VARTYPE`indiqué.|
|[Détacher](../cpp/variant-t-detach.md)|Détache l’objet `VARIANT` encapsulé de cet objet **_variant_t** .|
|[SetString](../cpp/variant-t-setstring.md)|Assigne une chaîne à cet objet **_variant_t** .|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[Opérateur =](../cpp/variant-t-operator-equal.md)|Assigne une nouvelle valeur à un objet **_variant_t** existant.|
|[opérateur = =, ! =](../cpp/variant-t-relational-operators.md)|Compare deux objets **_variant_t** pour vérifier leur égalité ou leur inégalité.|
|[Extracteurs](../cpp/variant-t-extractors.md)|Extrayez les données de l’objet `VARIANT` encapsulé.|

**Fin de la section spécifique de Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :** \<comutil. h >

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)
