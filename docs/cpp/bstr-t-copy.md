---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190324"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Section spécifique de Microsoft**

Construit une copie du `BSTR` encapsulé.

## <a name="syntax"></a>Syntaxe

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Paramètres

*fCopy*<br/>
Si la valeur est TRUE, **Copy** retourne une copie du `BSTR`contenu ; sinon, **Copy** retourne le BSTR réel.

## <a name="remarks"></a>Notes

Retourne une copie nouvellement allouée de l'objet `BSTR` encapsulé.

## <a name="example"></a>Exemple

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
