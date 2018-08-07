---
title: Hstring::hstring, constructeur | Microsoft Docs
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
ms.openlocfilehash: 96b77ec87e3219206d353f56293fc201c46f5d7e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568769"
---
# <a name="hstringhstring-constructor"></a>HString::HString, constructeur
Initialise une nouvelle instance de la **HString** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *HSTR*  
 Un handle HSTRING.  
  
 *other*  
 Un existant **HString** objet.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un nouveau **HString** objet est vide.  
  
 Le deuxième constructeur initialise un nouveau **HString** objet à la valeur existants *autres* paramètre et détruit le *autres* paramètre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [HString, classe](../windows/hstring-class.md)