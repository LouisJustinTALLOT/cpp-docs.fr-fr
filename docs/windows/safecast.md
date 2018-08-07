---
title: SafeCast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a5b1c5fed776e5e9312843160a740fd3d801b196
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608545"
---
# <a name="safecast"></a>SafeCast
Convertit un type de nombre à un autre type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *à partir de*  
 Le nombre de la source à convertir. Cela doit être de type `T`.  
  
 [out] *à*  
 Une référence au nouveau type de nombre. Cela doit être de type `U`.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si aucune erreur ne se produit ; **false** si une erreur se produit.  
  
## <a name="remarks"></a>Notes  
 Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de cast unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).  
  
> [!NOTE]
>  Cette méthode doit uniquement être utilisée lorsqu’une seule opération doit être protégée. S’il existe plusieurs opérations, vous devez utiliser le `SafeInt` classe au lieu d’appeler des fonctions autonomes individuelles.  
  
 Pour plus d’informations sur les types de modèles T et U, consultez [SafeInt, fonctions](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** safeint.h  
  
 **Namespace :** Microsoft::Utilities  
  
## <a name="see-also"></a>Voir aussi  
 [SafeInt, fonctions](../windows/safeint-functions.md)   
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeInt, classe](../windows/safeint-class.md)