---
description: 'En savoir plus sur : classe _bstr_t'
title: _bstr_t, classe
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: 562b8eb871ddcd63e7df70c84e61e80a5bf934b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229403"
---
# <a name="_bstr_t-class"></a>_bstr_t, classe

**Spécifique à Microsoft**

Un `_bstr_t` objet encapsule le [type de données BSTR](/previous-versions/windows/desktop/automat/bstr). La classe gère l’allocation et la désallocation des ressources via des appels de fonction à `SysAllocString` et et à d' `SysFreeString` autres API, le `BSTR` cas échéant. La classe **_bstr_t** utilise le décompte de références pour éviter une surcharge excessive.

### <a name="construction"></a>Construction

| Constructeur | Description |
|--|--|
| [_bstr_t](../cpp/bstr-t-bstr-t.md) | Construit un objet `_bstr_t`. |

### <a name="operations"></a>Operations

| Fonction | Description |
|--|--|
| [Assign](../cpp/bstr-t-assign.md) | Copie un `BSTR` dans le `BSTR` encapsulé par un `_bstr_t`. |
| [Attacher](../cpp/bstr-t-attach.md) | Lie un wrapper `_bstr_t` à un `BSTR`. |
| [copy](../cpp/bstr-t-copy.md) | Construit une copie du `BSTR` encapsulé. |
| [Détacher](../cpp/bstr-t-detach.md) | Retourne le `BSTR` encapsulé par un `_bstr_t` et détache `BSTR` du `_bstr_t`. |
| [GetAddress](../cpp/bstr-t-getaddress.md) | Pointe vers le `BSTR` encapsulé par un `_bstr_t`. |
| [GetBSTR](../cpp/bstr-t-getbstr.md) | Pointe sur le début du `BSTR` encapsulé par l'objet `_bstr_t`. |
| [length](../cpp/bstr-t-length.md) | Retourne le nombre de caractères du `_bstr_t`. |

### <a name="operators"></a>Opérateurs

| Opérateur | Description |
|--|--|
| [opérateur =](../cpp/bstr-t-operator-equal.md) | Assigne une nouvelle valeur à un objet `_bstr_t` existant. |
| [opérateur + =](../cpp/bstr-t-operator-add-equal-plus.md) | Ajoute des caractères à la fin de l'objet `_bstr_t`. |
| [opérateur +](../cpp/bstr-t-operator-add-equal-plus.md) | Concatène deux chaînes. |
| [and!](../cpp/bstr-t-operator-logical-not.md) | Vérifie si le encapsulé `BSTR` est une chaîne NULL. |
| [opérateur = =, ! =, \<, > , \<=, >=](../cpp/bstr-t-relational-operators.md) | Compare deux objets `_bstr_t`. |
| [Operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md) | Extrayez les pointeurs dans l'objet `BSTR` Unicode ou multioctets encapsulé. |

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Spécifications

**En-tête :**\<comutil.h>

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)
