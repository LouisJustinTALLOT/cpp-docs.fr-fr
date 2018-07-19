---
title: _com_error::HRESULTToWCode | Microsoft Docs
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
ms.openlocfilehash: dbcbd73f1a4a6d80ed30a5d70ca43d5fe45677f9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941715"
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
 *ressources humaines*  
 Le HRESULT de 32 bits à 16 bits `wCode`.  
  
## <a name="return-value"></a>Valeur de retour  
 16 bits `wCode` mappé à partir de la valeur HRESULT 32 bits.  
  
## <a name="remarks"></a>Notes  
 Consultez [_com_error::WCode](../cpp/com-error-wcode.md) pour plus d’informations.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, classe](../cpp/com-error-class.md)