---
title: no_dual_interfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1e919e48b79c9fe98a7a33257ebd0f70061d788
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541184"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Spécifique à C++**  
  
Modifie la façon dont le compilateur génère des fonctions wrapper pour les méthodes d'interface double.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Notes  
 
Normalement, le wrapper appelle la méthode via la table de fonctions virtuelles pour l'interface. Avec **no_dual_interfaces**, le wrapper appelle à la place `IDispatch::Invoke` pour appeler la méthode.  
  
**FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 
[attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
[directive #import](../preprocessor/hash-import-directive-cpp.md)