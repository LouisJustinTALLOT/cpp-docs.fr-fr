---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: d89503e822d92bf6a1fcb2b6bb658d532af32c5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581231"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Section spécifique à Microsoft**

Mappe le HRESULT de 32 bits à 16 bits `wCode`.

## <a name="syntax"></a>Syntaxe

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Paramètres

*ressources humaines*<br/>
Le HRESULT de 32 bits à 16 bits `wCode`.

## <a name="return-value"></a>Valeur de retour

16 bits `wCode` mappé à partir de la valeur HRESULT 32 bits.

## <a name="remarks"></a>Notes

Consultez [_com_error::WCode](../cpp/com-error-wcode.md) pour plus d’informations.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error, classe](../cpp/com-error-class.md)