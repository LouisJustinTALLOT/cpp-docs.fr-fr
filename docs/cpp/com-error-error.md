---
title: _com_error::Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7ddaefcf3bd46bf40b03c03d2d1fb00cf8fbbb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408425"
---
# <a name="comerrorerror"></a>_com_error::Error
**Section spécifique à Microsoft**  
  
 Récupère la valeur HRESULT passé au constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Error( ) const throw( );  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Élément HRESULT brut passé au constructeur.  
  
## <a name="remarks"></a>Notes  
 Récupère l’élément HRESULT encapsulé dans un `_com_error` objet.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)