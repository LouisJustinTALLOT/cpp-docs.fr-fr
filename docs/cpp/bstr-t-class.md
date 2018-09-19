---
title: _bstr_t, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04244357f7e372856aea28063ab0df9db6431e0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028686"
---
# <a name="bstrt-class"></a>_bstr_t, classe

**Section spécifique à Microsoft**

Un `_bstr_t` objet encapsule le [type de données BSTR](/previous-versions/windows/desktop/automat/bstr). La classe gère l’allocation des ressources et la désallocation via des appels de fonction à `SysAllocString` et `SysFreeString` et d’autres `BSTR` API lorsque cela est approprié. Le **_bstr_t** classe utilise le décompte de références pour éviter une charge excessive.

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
|[opérateur +=](../cpp/bstr-t-operator-add-equal-plus.md)|Ajoute des caractères à la fin de l'objet `_bstr_t`.|
|[+, opérateur](../cpp/bstr-t-operator-add-equal-plus.md)|Concatène deux chaînes.|
|[!, opérateur](../cpp/bstr-t-operator-logical-not.md)|Vérifie si encapsulé `BSTR` est une chaîne NULL.|
|[opérateur ==, ! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Compare deux objets `_bstr_t`.|
|[opérateur wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrayez les pointeurs dans l'objet `BSTR` Unicode ou multioctets encapsulé.|

**FIN de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

**En-tête :** \<comutil.h >

**Lib :** comsuppw.lib ou comsuppwd.lib (voir [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)