---
title: _bstr_t, classe
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: 3ef89c6f6742d528c427c49fd2a62d8820625e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190376"
---
# <a name="_bstr_t-class"></a>_bstr_t, classe

**Section spécifique de Microsoft**

Un objet `_bstr_t` encapsule le [type de données BSTR](/previous-versions/windows/desktop/automat/bstr). La classe gère l’allocation et la désallocation des ressources via des appels de fonction à `SysAllocString` et `SysFreeString` et d’autres API `BSTR`, le cas échéant. La classe **_bstr_t** utilise le décompte de références pour éviter une surcharge excessive.

### <a name="construction"></a>Construction

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Construit un objet `_bstr_t`.|

### <a name="operations"></a>Opérations

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|Copie un `BSTR` dans le `BSTR` encapsulé par un `_bstr_t`.|
|[Attacher](../cpp/bstr-t-attach.md)|Lie un wrapper `_bstr_t` à un `BSTR`.|
|[copy](../cpp/bstr-t-copy.md)|Construit une copie du `BSTR` encapsulé.|
|[Détacher](../cpp/bstr-t-detach.md)|Retourne le `BSTR` encapsulé par un `_bstr_t` et détache `BSTR` du `_bstr_t`.|
|[GetAddress](../cpp/bstr-t-getaddress.md)|Pointe vers le `BSTR` encapsulé par un `_bstr_t`.|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Pointe sur le début du `BSTR` encapsulé par l'objet `_bstr_t`.|
|[length](../cpp/bstr-t-length.md)|Retourne le nombre de caractères du `_bstr_t`.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](../cpp/bstr-t-operator-equal.md)|Assigne une nouvelle valeur à un objet `_bstr_t` existant.|
|[opérateur + =](../cpp/bstr-t-operator-add-equal-plus.md)|Ajoute des caractères à la fin de l'objet `_bstr_t`.|
|[+, opérateur](../cpp/bstr-t-operator-add-equal-plus.md)|Concatène deux chaînes.|
|[!, opérateur](../cpp/bstr-t-operator-logical-not.md)|Vérifie si le `BSTR` encapsulé est une chaîne NULL.|
|[opérateur = =, ! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Compare deux objets `_bstr_t`.|
|[wchar_t d’opérateur &#124; * char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrayez les pointeurs dans l'objet `BSTR` Unicode ou multioctets encapsulé.|

**Fin de la section spécifique de Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :** \<comutil. h >

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)
