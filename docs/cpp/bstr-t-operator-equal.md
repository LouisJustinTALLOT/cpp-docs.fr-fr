---
description: 'En savoir plus sur : _bstr_t :: Operator ='
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 78447048a45567df603acf3af0bc51cefbdb187d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308781"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Spécifique à Microsoft**

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

*S2*<br/>
Chaîne multioctets à assigner à un objet `_bstr_t` existant.

*processeur*<br/>
Chaîne Unicode à assigner à un objet `_bstr_t` existant.

*var*<br/>
Objet `_variant_t` à assigner à un objet `_bstr_t` existant.

**FIN spécifique à Microsoft**

## <a name="example"></a>Exemple

Consultez [_bstr_t :: assign](../cpp/bstr-t-assign.md) pour obtenir un exemple d’utilisation de **Operator =**.

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
