---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154927"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Section spécifique à Microsoft**

Mappe les 16 bits *wCode* vers HRESULT de 32 bits.

## <a name="syntax"></a>Syntaxe

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Paramètres

*wCode*<br/>
16 bits *wCode* à mapper au HRESULT de 32 bits.

## <a name="return-value"></a>Valeur de retour

HRESULT de 32 bits mappé à partir de 16 bits *wCode*.

## <a name="remarks"></a>Notes

Consultez le [WCode](../cpp/com-error-wcode.md) fonction membre.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error, classe](../cpp/com-error-class.md)