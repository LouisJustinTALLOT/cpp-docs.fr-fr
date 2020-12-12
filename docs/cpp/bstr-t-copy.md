---
description: 'En savoir plus sur : _bstr_t :: Copy'
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 29ca965730dbcc22b4b725661ece68442d39aeba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229338"
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
