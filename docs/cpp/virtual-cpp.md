---
title: Virtual (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84035f2007f3c45c33c1dfa342caf5c788580205
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460917"
---
# <a name="virtual-c"></a>virtual (C++)
Le **virtuel** mot clé déclare une fonction virtuelle ou une classe de base virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>Paramètres  
 *spécificateurs de type*  
 Spécifie le type de retour de la fonction membre virtuelle.  
  
 *déclarateur de fonction membre*  
 Déclare une fonction membre.  
  
 *spécificateur d’accès*  
 Définit le niveau d’accès à la classe de base, **public**, **protégé** ou **privé**. Peut apparaître avant ou après le **virtuel** mot clé.  
  
 *nom de classe de base*  
 Identifie un type de classe déclaré précédemment.  
  
## <a name="remarks"></a>Notes  
 Consultez [fonctions virtuelles](../cpp/virtual-functions.md) pour plus d’informations.  
  
 Consultez également les mots clés suivants : [classe](../cpp/class-cpp.md), [privé](../cpp/private-cpp.md), [public](../cpp/public-cpp.md), et [protégé](../cpp/protected-cpp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)