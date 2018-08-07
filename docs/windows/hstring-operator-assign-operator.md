---
title: HString::Operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9cc496f4f1c23508b2ebba2788910ff9c9ca2066
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608597"
---
# <a name="hstringoperator-operator"></a>HString::Operator=, opérateur
Déplace la valeur d’un autre **HString** objet actuel **HString** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
### <a name="parameters"></a>Paramètres  
 *other*  
 Un existant **HString** objet.  
  
## <a name="remarks"></a>Notes  
 La valeur existants *autres* objet est copié dans le cours **HString** objet, puis le *autres* détruit.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)