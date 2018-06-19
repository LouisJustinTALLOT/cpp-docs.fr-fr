---
title: _com_error::ErrorInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fbc735dfae1b30209eccfd14f1170826fb07680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410991"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Section spécifique à Microsoft**  
  
 Récupère le **IErrorInfo** objet passé au constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Brutes **IErrorInfo** élément passé au constructeur.  
  
## <a name="remarks"></a>Notes  
 Récupère l’encapsulé **IErrorInfo** d’élément dans un `_com_error` objet, ou **NULL** si aucun **IErrorInfo** article est enregistré. L’appelant doit appeler **version** sur l’objet retourné lors de la fin de l’utiliser.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)