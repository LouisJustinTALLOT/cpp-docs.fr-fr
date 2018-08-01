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
ms.openlocfilehash: f0ddac28c4f39cdf11abbdf38c3af5d00c22413a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401904"
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