---
title: once_flag, structure | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: a39919d3c1608d53edc6a75ecc3dd2e0ff504b1c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/19/2017

---
# <a name="onceflag-structure"></a>once_flag, structure
Représente un `struct` utilisé avec la fonction de modèle [call_once](../standard-library/mutex-functions.md#call_once) pour garantir que le code d’initialisation est appelé une seule fois, même en présence de plusieurs threads d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };  
  
## <a name="remarks"></a>Notes  
 `once_flag``struct` a seulement un constructeur par défaut.  
  
 Les objets de type `once_flag` peuvent être créés, mais ils ne peuvent pas être copiés.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<mutex >  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




