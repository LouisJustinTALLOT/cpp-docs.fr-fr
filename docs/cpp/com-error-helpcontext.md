---
title: _com_error::HelpContext | Microsoft Docs
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
ms.openlocfilehash: b1edf990697aa6becca0ad377f18e8f7045c96a4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401842"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Section spécifique à Microsoft**  
  
 Appels `IErrorInfo::GetHelpContext` (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DWORD HelpContext( ) const throw( );  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le résultat de `IErrorInfo::GetHelpContext` pour le `IErrorInfo` objet enregistré dans le `_com_error` objet. Si aucun `IErrorInfo` objet est enregistré, elle retourne un zéro.  
  
## <a name="remarks"></a>Notes  
 Tout échec lors de l’appel la `IErrorInfo::GetHelpContext` méthode est ignorée.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)