---
title: Argtraits::args, constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b6f0059d167b04c9a4b177d1851ad88133ef5cd3
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466554"
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args, constante
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>Notes  
 Conserve le nombre de paramètres sur le `Invoke` méthode d’une interface de délégué.  
  
## <a name="remarks"></a>Notes  
 Lorsque `args` est égal à -1 indique qu’il ne peut y avoir aucune correspondance pour le `Invoke` signature de méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [ArgTraits (Structure)](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)