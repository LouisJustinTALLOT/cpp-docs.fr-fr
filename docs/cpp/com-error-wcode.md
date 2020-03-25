---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190194"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Section spécifique de Microsoft**

Récupère le code d’erreur 16 bits mappé dans le HRESULT encapsulé.

## <a name="syntax"></a>Syntaxe

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Si la valeur HRESULT est comprise dans la plage 0x80040200 à 0x8004FFFF, la méthode `WCode` retourne le HRESULT moins 0x80040200 ; Sinon, elle retourne zéro.

## <a name="remarks"></a>Notes

La méthode `WCode` est utilisée pour annuler un mappage qui se produit dans le code de prise en charge COM. Le wrapper d’une méthode ou d’une propriété `dispinterface` appelle une routine de prise en charge qui empaquette les arguments et appelle `IDispatch::Invoke`. Lors du retour, si un HRESULT d’échec de `DISP_E_EXCEPTION` est retourné, les informations sur l’erreur sont récupérées à partir de la structure `EXCEPINFO` passée à `IDispatch::Invoke`. Le code d’erreur peut être une valeur 16 bits stockée dans le membre `wCode` de la structure `EXCEPINFO` ou une valeur 32 bits complète dans le membre `scode` de la structure `EXCEPINFO`. Si une `wCode` 16 bits est retournée, elle doit d’abord être mappée à un HRESULT d’échec 32 bits.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error, classe](../cpp/com-error-class.md)
