---
title: SafeLessThan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 923c1f46d8d4212eb61cd9834af1c47d521bf369
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020038"
---
# <a name="safelessthan"></a>SafeLessThan
Détermine si un nombre est inférieur à un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T, typename U>  
inline bool SafeLessThan (  
   const T t,  
   const U u  
) throw ();  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *t*  
 Premier nombre. Cela doit être de type `T`.  
  
 [in] *u*  
 Le deuxième nombre. Cela doit être de type `U`.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si *t* est inférieure à *u*; sinon **false**.  
  
## <a name="remarks"></a>Notes  
 Cette méthode améliore l’opérateur de comparaison standard, car **SafeLessThan** vous permet de comparer deux types de nombre.  
  
 Cette méthode fait partie de [Bibliothèque SafeInt](../windows/safeint-library.md) et est conçu pour une opération de comparaison unique sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md).  
  
> [!NOTE]
>  Cette méthode doit uniquement être utilisée lorsqu’une opération mathématique unique doit être protégée. S’il existe plusieurs opérations, vous devez utiliser le `SafeInt` classe, plutôt que d’appeler des fonctions autonomes individuelles.  
  
 Pour plus d’informations sur les types de modèle `T` et `U`, consultez [SafeInt, fonctions](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** safeint.h  
  
 **Namespace :** Microsoft::Utilities  
  
## <a name="see-also"></a>Voir aussi  
 [SafeInt, fonctions](../windows/safeint-functions.md)   
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeInt, classe](../windows/safeint-class.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)