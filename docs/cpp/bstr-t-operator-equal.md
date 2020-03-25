---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 5b7f499dd84a67020232aab84966647378daadad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181068"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Section spécifique de Microsoft**

Assigne une nouvelle valeur à un objet `_bstr_t` existant.

## <a name="syntax"></a>Syntaxe

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Paramètres

*s1*<br/>
Objet `_bstr_t` à assigner à un objet `_bstr_t` existant.

*s2*<br/>
Chaîne multioctets à assigner à un objet `_bstr_t` existant.

*processeur*<br/>
Chaîne Unicode à assigner à un objet `_bstr_t` existant.

*var*<br/>
Objet `_variant_t` à assigner à un objet `_bstr_t` existant.

**Fin de la section spécifique de Microsoft**

## <a name="example"></a>Exemple

Consultez [_bstr_t :: assign](../cpp/bstr-t-assign.md) pour obtenir un exemple d’utilisation de **Operator =** .

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
