---
title: _com_error::GUID | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee1952e50251cfac7563357c7626ab8603589e4d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409680"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Section spécifique à Microsoft**  
  
 Appels **IErrorInfo::GetGUID** (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le résultat de **IErrorInfo::GetGUID** pour le **IErrorInfo** enregistré dans le `_com_error` objet. Si aucun **IErrorInfo** objet est enregistré, il retourne `GUID_NULL`.  
  
## <a name="remarks"></a>Notes  
 Tout échec lors de l’appel du **IErrorInfo::GetGUID** méthode est ignorée.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)