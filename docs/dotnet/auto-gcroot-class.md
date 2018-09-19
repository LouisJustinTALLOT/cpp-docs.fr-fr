---
title: auto_gcroot, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da63d58136d61bbea75daa90ac01cee5b44ac86d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039099"
---
# <a name="autogcroot-class"></a>auto_gcroot, classe
Gestion des ressources automatique (comme [auto_ptr, classe](../standard-library/auto-ptr-class.md)) qui peut être utilisé pour incorporer un handle virtuel dans un type natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>Paramètres  
*_element_type*<br/>
Le type managé à incorporer.  
  
## <a name="requirements"></a>Configuration requise  
 **Fichier d’en-tête** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [auto_gcroot](../dotnet/auto-gcroot.md)   
 [auto_gcroot, membres](../dotnet/auto-gcroot-members.md)   
 [Comment : déclarer des Handles dans les Types natifs](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle, classe](../dotnet/auto-handle-class.md)