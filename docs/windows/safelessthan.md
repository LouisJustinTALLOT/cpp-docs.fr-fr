---
title: SafeLessThan | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeLessThan
dev_langs: C++
helpviewer_keywords: SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 3dbcec30858e5a56521d56c4f87b79f88b2c13d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="safelessthan"></a>SafeLessThan
Détermine si un nombre est inférieur à un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeLessThan (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `t`  
 Premier nombre. Cela doit être de type T.  
  
 [in] `u`  
 Le deuxième nombre. Cela doit être de type U.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si `t` est inférieure à `u`; sinon `false`.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode améliore l’opérateur de comparaison standard car `SafeLessThan` vous permet de comparer deux types de nombre.  
  
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
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)