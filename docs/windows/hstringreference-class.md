---
title: Hstringreference, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14ad6e511baa4c7b61a2205311bfb9ea4322a5b1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605098"
---
# <a name="hstringreference-class"></a>HStringReference, classe
Représente un HSTRING créé à partir d’une chaîne existante.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>Notes  
 La durée de vie de la mémoire tampon de stockage dans le nouveau HSTRING n’est pas gérée par le Runtime de Windows. L’appelant alloue une chaîne source sur le frame de pile pour éviter une allocation de tas et d’éliminer le risque d’une fuite de mémoire. En outre, l’appelant doit s’assurer que la chaîne source reste inchangée pendant la durée de vie du HSTRING attaché. Pour plus d’informations, consultez [WindowsCreateStringReference fonction](http://msdn.microsoft.com/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[HStringReference::HStringReference, constructeur](../windows/hstringreference-hstringreference-constructor.md)|Initialise une nouvelle instance de la **HStringReference** classe.|  
  
### <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|[HStringReference::CopyTo, méthode](../windows/hstringreference-copyto-method.md)|Copie en cours **HStringReference** objet dans un objet HSTRING.|  
|[HStringReference::Get, méthode](../windows/hstringreference-get-method.md)|Récupère la valeur du handle HSTRING sous-jacent.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[HStringReference::Operator=, opérateur](../windows/hstringreference-operator-assign-operator.md)|Déplace la valeur d’un autre **HStringReference** objet actuel **HStringReference** objet.|  
|[HStringReference::Operator==, opérateur](../windows/hstringreference-operator-equality-operator.md)|Indique si les deux paramètres sont égaux.|  
|[HStringReference::Operator!=, opérateur](../windows/hstringreference-operator-inequality-operator.md)|Indique si les deux paramètres ne sont pas égales.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `HStringReference`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)