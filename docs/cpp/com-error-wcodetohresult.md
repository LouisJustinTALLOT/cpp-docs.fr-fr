---
title: _com_error::WCodeToHRESULT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b6712734cd7283558ad5776444586f8c0b3fa6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077566"
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

*WCode*<br/>
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