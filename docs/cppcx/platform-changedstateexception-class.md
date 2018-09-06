---
title: Platform::changedstateexception, classe | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
dev_langs:
- C++
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 029242a466b7fbac0d967596c114eb0ad45aa569
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760667"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException, classe
Exception levée lorsque l'état interne d'un objet a changé, ce qui entraîne l'invalidation des résultats de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Notes  
 Par exemple, cette exception est levée lorsque les méthodes d'un itérateur de collection ou d'une vue de collection sont appelées après la modification d'une collection parente, invalidant ainsi les résultats de la méthode.  
  
 Pour plus d'informations, consultez la classe [COMException](../cppcx/platform-comexception-class.md) .  
  
### <a name="requirements"></a>Configuration requise  
 **Minimum de client pris en charge :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd  
  
## <a name="see-also"></a>Voir aussi  
 [Platform::COMException, classe](../cppcx/platform-comexception-class.md)