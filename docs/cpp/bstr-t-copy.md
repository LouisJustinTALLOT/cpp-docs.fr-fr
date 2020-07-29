---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: b6029e98e83b171d9ab9f8f3f0282fa3f46ca167
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227593"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Spécifique à Microsoft**

Construit une copie du `BSTR` encapsulé.

## <a name="syntax"></a>Syntaxe

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Paramètres

*fCopy*<br/>
Si **`true`** la valeur est, **Copy** retourne une copie du contenu `BSTR` . sinon, **Copy** retourne le BSTR réel.

## <a name="remarks"></a>Notes

Retourne une copie nouvellement allouée de l'objet `BSTR` encapsulé.

## <a name="example"></a>Exemple

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
