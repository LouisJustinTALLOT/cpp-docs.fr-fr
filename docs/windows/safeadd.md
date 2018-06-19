---
title: SafeAdd | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0450820afdde3eb330948a65f8d052fa54017dc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892714"
---
# <a name="safeadd"></a>SafeAdd
Additionne deux nombres d’une manière qui protège contre le dépassement de capacité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `t`  
 Le premier nombre à ajouter. Cela doit être de type T.  
  
 [in] `u`  
 Second nombre à ajouter. Cela doit être de type U.  
  
 [out] `result`  
 Le paramètre où `SafeAdd` stocke le résultat.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si aucune erreur ne se produit ; `false` si une erreur se produit.  
  
## <a name="remarks"></a>Notes  
 Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération d’ajout unique sans créer d’instance de la [SafeInt, classe](../windows/safeint-class.md).  
  
> [!NOTE]
>  Cette méthode doit uniquement être utilisée lorsqu’une opération mathématique unique doit être protégée. S’il existe plusieurs opérations, vous devez utiliser le `SafeInt` classe au lieu d’appeler les fonctions autonomes individuelles.  
  
 Pour plus d’informations sur les types de modèles T, U, consultez [SafeInt, fonctions](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** safeint.h  
  
 **Namespace :** Microsoft::Utilities  
  
## <a name="see-also"></a>Voir aussi  
 [SafeInt, fonctions](../windows/safeint-functions.md)   
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeInt (classe)](../windows/safeint-class.md)   
 [SafeSubtract](../windows/safesubtract.md)