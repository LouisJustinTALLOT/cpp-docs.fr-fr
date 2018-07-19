---
title: _com_error::ErrorInfo | Microsoft Docs
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
ms.openlocfilehash: 52935c81849ded072cb20d6c835b3a71b66c2871
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941312"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Section spécifique à Microsoft**  
  
 Récupère le `IErrorInfo` objet passé au constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 L'élément `IErrorInfo` brut est transmis dans le constructeur.  
  
## <a name="remarks"></a>Notes  
 Récupère le texte encapsulé `IErrorInfo` d’éléments dans un `_com_error` de l’objet, ou NULL si aucun `IErrorInfo` élément est enregistré. L’appelant doit appeler `Release` sur l’objet retourné lors de la fin de l’utiliser.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)