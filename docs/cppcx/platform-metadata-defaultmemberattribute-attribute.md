---
title: DefaultMemberAttribute (attribut) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::DefaultMemberAttribute
dev_langs:
- C++
helpviewer_keywords:
- Platform::Metadata::DefaultMemberAttribute Attribute
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62d531418e4729c34907cb65d446f89bfa60fb63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608912"
---
# <a name="platformmetadatadefaultmemberattribute-attribute"></a>Platform::Metadata::DefaultMemberAttribute (attribut)
Indique la fonction par défaut à appeler parmi plusieurs fonctions surchargées possibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
public ref class DefaultMember abstract : Attribute  
```  
  
## <a name="inheritance"></a>Héritage  
 [Platform::Object](../cppcx/platform-object-class.md)   
  
 [Platform::Metadata::Attribute](../cppcx/platform-metadata-attribute-attribute.md)  
  
### <a name="remarks"></a>Notes  
 Appliquez l'attribut DefaultMember à une méthode qui est consommée par une application JavaScript.  
  
### <a name="requirements"></a>Configuration requise  
 **Minimum de client pris en charge :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform::Metadata  
  
 **Métadonnées :** platform.winmd  
  
## <a name="see-also"></a>Voir aussi  
 [Platform::Metadata (espace de noms)](../cppcx/platform-metadata-namespace.md)