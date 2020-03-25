---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180561"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Section spécifique de Microsoft**

Mappe le HRESULT 32 bits à `wCode`16 bits.

## <a name="syntax"></a>Syntaxe

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Paramètres

*h*<br/>
HRESULT 32 bits à mapper à `wCode`16 bits.

## <a name="return-value"></a>Valeur de retour

`wCode` 16 bits mappé à partir de la valeur HRESULT 32 bits.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [_com_error :: WCode](../cpp/com-error-wcode.md) .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error, classe](../cpp/com-error-class.md)
