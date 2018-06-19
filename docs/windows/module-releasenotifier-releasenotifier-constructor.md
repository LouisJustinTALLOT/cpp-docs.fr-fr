---
title: Constructeur de module::ReleaseNotifier::ReleaseNotifier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bbf21e1abc88c0fac0b9d20653fdb45c3706466d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882467"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier, constructeur
Initialise une nouvelle instance de la classe Module::ReleaseNotifier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `release`  
 `true` Pour supprimer cette instance lorsque la méthode Release est appelée ; `false` de ne pas supprimer cette instance.  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Module::ReleaseNotifier, classe](../windows/module-releasenotifier-class.md)