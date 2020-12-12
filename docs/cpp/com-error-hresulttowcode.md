---
description: 'En savoir plus sur : _com_error :: HRESULTToWCode'
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 1bbf62be42d4e34a2ef73493f0449c2ffbaf0646
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295831"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Spécifique à Microsoft**

Mappe le HRESULT 32 bits à 16 bits `wCode` .

## <a name="syntax"></a>Syntaxe

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Paramètres

*heure(s)*<br/>
HRESULT 32 bits à mapper à 16 bits `wCode` .

## <a name="return-value"></a>Valeur renvoyée

`wCode`mappé à 16 bits à partir de la valeur HRESULT 32 bits.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [_com_error :: WCode](../cpp/com-error-wcode.md) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[Classe _com_error](../cpp/com-error-class.md)
