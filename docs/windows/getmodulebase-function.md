---
title: Getmodulebase, fonction | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25e4bb6db6114f7d64522dfe145d51ffaabd476a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874205"
---
# <a name="getmodulebase-function"></a>GetModuleBase, fonction
Récupère un [ModuleBase](../windows/modulebase-class.md) pointeur permettant d’incrémenter et décrémenter le décompte de références d’un [RuntimeClass](../windows/runtimeclass-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `ModuleBase` objet.  
  
## <a name="remarks"></a>Notes  
 Cette fonction est utilisée en interne pour incrémenter et décrémenter le nombre de référence d’objet.  
  
 Vous pouvez utiliser cette fonction pour contrôler les nombres de références en appelant [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) et [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)