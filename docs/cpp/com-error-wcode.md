---
description: 'En savoir plus sur : _com_error :: WCode'
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: e3a19e5ae6c98cb38445e5eaa822474b2a852135
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295729"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Spécifique à Microsoft**

Récupère le code d’erreur 16 bits mappé dans le HRESULT encapsulé.

## <a name="syntax"></a>Syntaxe

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Si la valeur HRESULT est comprise dans la plage 0x80040200 à 0x8004FFFF, la `WCode` méthode retourne le HRESULT moins 0x80040200 ; sinon, elle retourne zéro.

## <a name="remarks"></a>Notes

La `WCode` méthode est utilisée pour annuler un mappage qui se produit dans le code de prise en charge com. Le wrapper d’une `dispinterface` propriété ou d’une méthode appelle une routine de prise en charge qui empaquette les arguments et les appels `IDispatch::Invoke` . Lors du retour, si un HRESULT d’échec de `DISP_E_EXCEPTION` est retourné, les informations sur l’erreur sont récupérées à partir de la `EXCEPINFO` structure passée à `IDispatch::Invoke` . Le code d’erreur peut être une valeur 16 bits stockée dans le `wCode` membre de la `EXCEPINFO` structure ou une valeur 32 bits complète dans le `scode` membre de la `EXCEPINFO` structure. Si une valeur 16 bits `wCode` est retournée, elle doit d’abord être mappée à un HRESULT d’échec 32 bits.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[Classe _com_error](../cpp/com-error-class.md)
