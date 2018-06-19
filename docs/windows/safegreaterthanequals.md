---
title: SafeGreaterThanEquals | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThanEquals function
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c8b08e9262c1fc251de9ce2e23ba37783e97ab9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888758"
---
# <a name="safegreaterthanequals"></a>SafeGreaterThanEquals
Compare deux nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T, typename U>  
inline bool SafeGreaterThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `t`  
 Le premier nombre à comparer. Cela doit être de type T.  
  
 [in] `u`  
 Second nombre à comparer. Cela doit être de type U.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si `t` est supérieur ou égal à `u`; sinon `false`.  
  
## <a name="remarks"></a>Notes  
 `SafeGreaterThanEquals` améliore l’opérateur de comparaison standard, car il vous permet de comparer deux types de nombres.  
  
 Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de comparaison unique sans créer d’instance de la [SafeInt, classe](../windows/safeint-class.md).  
  
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
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeLessThan](../windows/safelessthan.md)