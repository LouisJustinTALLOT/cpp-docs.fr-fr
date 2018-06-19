---
title: _com_error::WCode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1354d490446795e55b41fa0c548e8dd8aa38c71b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411534"
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Section spécifique à Microsoft**  
  
 Récupère le code d'erreur 16 bits mappé dans le `HRESULT` encapsulé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si le `HRESULT` se trouve dans la plage 0 x 80040200 à 0x8004FFFF, la **WCode** méthode retourne la `HRESULT` moins 0 x 80040200 ; sinon, elle retourne zéro.  
  
## <a name="remarks"></a>Notes  
 Le **WCode** méthode est utilisée pour annuler un mappage qui se produit dans le code de prise en charge COM. Le wrapper pour un **dispinterface** propriété ou une méthode appelle une routine d’assistance qui empaquette les arguments et appelle **IDispatch::Invoke**. Au retour, si une défaillance `HRESULT` de `DISP_E_EXCEPTION` est retourné, les informations d’erreur sont récupérées à partir de la **EXCEPINFO** structure passée au **IDispatch::Invoke**. Le code d’erreur peut être une valeur 16 bits stockée dans le `wCode` membre de la **EXCEPINFO** structure ou une valeur de 32 bits dans le **scode** membre de la **EXCEPINFO**structure. Si un `wCode` 16 bits est retourné, il doit d'abord être mappé à un `HRESULT` d'échec 32 bits.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, classe](../cpp/com-error-class.md)