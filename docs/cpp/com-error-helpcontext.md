---
title: _com_error::HelpContext | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7123fcf5859ce3fc373b29b4cb3e7b32109b464e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410822"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Section spécifique à Microsoft**  
  
 Appels **IErrorInfo::GetHelpContext** (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le résultat de **IErrorInfo::GetHelpContext** pour le **IErrorInfo** enregistré dans le `_com_error` objet. Si aucun **IErrorInfo** objet est enregistré, elle retourne une valeur zéro.  
  
## <a name="remarks"></a>Notes  
 Tout échec lors de l’appel du **IErrorInfo::GetHelpContext** méthode est ignorée.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)