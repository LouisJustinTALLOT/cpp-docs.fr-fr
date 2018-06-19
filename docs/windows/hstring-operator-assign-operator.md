---
title: HString::Operator =, opérateur | Documents Microsoft
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
ms.openlocfilehash: 6fd1082beb6d84c5dded008e20683f7292cbc1e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873870"
---
# <a name="hstringoperator-operator"></a>HString::Operator=, opérateur
Déplace la valeur d’un autre objet HString à l’objet HString actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
#### <a name="parameters"></a>Paramètres  
 `other`  
 Objet HString existant.  
  
## <a name="remarks"></a>Notes  
 La valeur existants `other` objet est copié vers l’objet HString en cours, puis le `other` objet est détruit.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)