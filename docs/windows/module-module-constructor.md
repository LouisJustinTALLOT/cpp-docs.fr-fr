---
title: Module::module, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d63b90bb3622129589fca41c029f548a07ec21b8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017654"
---
# <a name="modulemodule-constructor"></a>Module::Module, constructeur
Initialise une nouvelle instance de la **Module** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Module();  
```  
  
## <a name="remarks"></a>Notes  
 Ce constructeur est protégé et ne peut pas être appelé avec le **nouveau** mot clé. Au lieu de cela, appelez [module::GetModule, méthode](../windows/module-getmodule-method.md) ou [module::Create, méthode](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL
 
 ## <a name="see-also"></a>Voir aussi
 [Module, classe](../windows/module-class.md)