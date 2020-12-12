---
description: 'En savoir plus sur : _com_error :: WCodeToHRESULT'
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: 9925c34f14f0685cb563e37a8cae0970911f009c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295716"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur renvoyée

HRESULT 32 bits mappé à partir de *wCode* 16 bits.

## <a name="remarks"></a>Notes

Consultez la fonction membre [WCode](../cpp/com-error-wcode.md) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[Classe _com_error](../cpp/com-error-class.md)
