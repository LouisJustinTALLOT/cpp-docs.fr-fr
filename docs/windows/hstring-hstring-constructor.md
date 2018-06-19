---
title: Hstring::hstring, constructeur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3188e137d3a39fb26ca4151f72073306038e46f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876876"
---
# <a name="hstringhstring-constructor"></a>HString::HString, constructeur
Initialise une nouvelle instance de la classe HString.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hstr`  
 Un handle HSTRING.  
  
 `other`  
 Objet HString existant.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un nouvel objet HString qui est vide.  
  
 Le deuxième constructeur initialise un nouvel objet HString à la valeur existants `other` paramètre et puis détruit la `other` paramètre.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)