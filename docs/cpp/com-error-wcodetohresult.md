---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2194e0e54a93d3227b84d893f9d3f208d972d09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180509"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Section spécifique de Microsoft**

Mappe les *wCode* 16 bits à HRESULT 32 bits.

## <a name="syntax"></a>Syntaxe

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Paramètres

*wCode*<br/>
*WCode* 16 bits à mapper à HRESULT 32 bits.

## <a name="return-value"></a>Valeur de retour

HRESULT 32 bits mappé à partir de *wCode*16 bits.

## <a name="remarks"></a>Notes

Consultez la fonction membre [WCode](../cpp/com-error-wcode.md) .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error, classe](../cpp/com-error-class.md)
