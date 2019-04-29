---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350869"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

**Section spécifique à Microsoft**

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

*s3*<br/>
Chaîne Unicode à assigner à un objet `_bstr_t` existant.

*var*<br/>
Objet `_variant_t` à assigner à un objet `_bstr_t` existant.

**FIN de la section spécifique à Microsoft**

## <a name="example"></a>Exemple

Consultez [_bstr_t::Assign](../cpp/bstr-t-assign.md) pour obtenir un exemple d’utilisation de **opérateur =**.

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)