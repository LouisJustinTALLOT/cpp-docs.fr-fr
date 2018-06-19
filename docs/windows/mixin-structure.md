---
title: MixIn (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20dac5f189a51a1610da45e43e03e51ff1c3610
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876161"
---
# <a name="mixin-structure"></a>MixIn (structure)
Garantit qu'une classe d'exécution dérive des interfaces du Windows Runtime, le cas échéant, puis des interfaces du COM classique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Derived`  
 Un type dérivé de la [implémente](../windows/implements-structure.md) structure.  
  
 `MixInType`  
 Type de base.  
  
 `hasImplements`  
 `true` Si `MixInType` est dérivé de l’implémentation actuelle du type de base ; `false` dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
 Si une classe est dérivée de Windows Runtime et les interfaces de classe COM, la liste de déclaration de classe doit répertorier tout d’abord toutes les interfaces Windows Runtime et puis des interfaces tout COM classique. MixIn garantit que les interfaces sont spécifiées dans l’ordre correct.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `MixIn`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)