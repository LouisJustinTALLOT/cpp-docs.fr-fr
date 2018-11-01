---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 13ddf57e0bdbdbcc0c5b487e879e14b000de3ad0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506836"
---
# <a name="bstrtcopy"></a>_bstr_t::copy

**Section spécifique à Microsoft**

Construit une copie du `BSTR` encapsulé.

## <a name="syntax"></a>Syntaxe

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Paramètres

*fCopy*<br/>
Si la valeur est TRUE, **copie** retourne une copie de la relation contenant-contenu `BSTR`, sinon **copie** retourne le BSTR réel.

## <a name="remarks"></a>Notes

Retourne une copie nouvellement allouée de l'objet `BSTR` encapsulé.

## <a name="example"></a>Exemple

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)