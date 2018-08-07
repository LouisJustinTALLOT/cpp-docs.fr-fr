---
title: HStringReference::Operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc8f919dcec994be5d4f0300e9c96dde95895e16
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608519"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator=, opérateur
Déplace la valeur d’un autre **HStringReference** objet actuel **HStringReference** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
### <a name="parameters"></a>Paramètres  
 *other*  
 Un existant **HStringReference** objet.  
  
## <a name="remarks"></a>Notes  
 La valeur existants *autres* objet est copié dans le cours **HStringReference** objet, puis le *autres* détruit.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HStringReference, classe](../windows/hstringreference-class.md)