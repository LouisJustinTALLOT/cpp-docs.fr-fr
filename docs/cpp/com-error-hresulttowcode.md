---
title: _com_error::HRESULTToWCode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e3955fcda665e08e5415652a1e8f1f232d0fe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412262"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Section spécifique à Microsoft**  
  
 Mappe les 32 bits `HRESULT` à 16 bits `wCode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hr`  
 32 bits `HRESULT` soit mappé à 16 bits `wCode`.  
  
## <a name="return-value"></a>Valeur de retour  
 16 bits `wCode` mappé à partir de 32 bits `HRESULT`.  
  
## <a name="remarks"></a>Notes  
 Consultez [_com_error::WCode](../cpp/com-error-wcode.md) pour plus d’informations.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, classe](../cpp/com-error-class.md)