---
title: Chaininterfaces::Verify, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c83479434a936f32fb0f7367d8cd02c6676c74e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860692"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify, méthode
Vérifie que chaque interface définie par les paramètres de modèle `I0` via `I9` hérite de IUnknown et/ou IInspectable et qui `I0` hérite `I1` via `I9`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Notes  
 Si l’opération de vérification échoue, un `static_assert` émet un message d’erreur qui décrit l’échec.  
  
## <a name="remarks"></a>Notes  
 Paramètres de modèle `I0` et `I1` sont requis et les paramètres `I2` via `I9` sont facultatifs.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ChainInterfaces, structure](../windows/chaininterfaces-structure.md)