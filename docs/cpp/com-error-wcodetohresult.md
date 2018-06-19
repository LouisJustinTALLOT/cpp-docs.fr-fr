---
title: _com_error::WCodeToHRESULT | Documents Microsoft
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
ms.openlocfilehash: 31b9df8305d0eea772979904f63847f6d6c2325a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413373"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Section spécifique à Microsoft**  
  
 Mappe `wCode` 16 bits vers `HRESULT` 32 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wCode`  
 `wCode` 16 bits à mapper vers `HRESULT` 32 bits.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` 32 bits mappé à partir de `wCode` 16 bits.  
  
## <a name="remarks"></a>Notes  
 Consultez le [WCode](../cpp/com-error-wcode.md) fonction membre.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error, classe](../cpp/com-error-class.md)