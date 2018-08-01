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
ms.openlocfilehash: 3f777b1de83b19727bca5e1b498c5380604f6688
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404539"
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
 *WCode*  
 16 bits *wCode* à mapper au HRESULT de 32 bits.  
  
## <a name="return-value"></a>Valeur de retour  
 HRESULT de 32 bits mappé à partir de 16 bits *wCode*.  
  
## <a name="remarks"></a>Notes  
 Consultez le [WCode](../cpp/com-error-wcode.md) fonction membre.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error, classe](../cpp/com-error-class.md)