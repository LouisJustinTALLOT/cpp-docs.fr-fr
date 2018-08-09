---
title: Verifyinheritancehelper::Verify, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04bf01b5fad5a9fec579e347497a28b5e8abb861
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018814"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
static void Verify();  
```  
  
## <a name="remarks"></a>Notes  
 Teste les deux interfaces spécifiées par les paramètres de modèle actuelle et détermine si une interface est dérivée de l’autre.  
  
 Une erreur est générée si une interface n’est pas dérivée de l’autre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [VerifyInheritanceHelper (Structure)](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)