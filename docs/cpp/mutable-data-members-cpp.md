---
title: Données membres mutables (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adc8f9c456d28089d57bc1f13b61ad8efa10b6b6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402918"
---
# <a name="mutable-data-members-c"></a>Membres de données mutables (C++)
Ce mot clé peut être appliqué uniquement aux données membres non statiques et non constantes d'une classe. Si un membre de données est déclaré **mutable**, puis il est permis d’assigner une valeur à ce membre de données à partir d’un **const** fonction membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Notes  
 Par exemple, le code suivant sera compilé sans erreur, car `m_accessCount` a été déclarée comme étant **mutable**et peut donc être modifié par `GetFlag` même si `GetFlag` est une fonction membre const.  
  
```cpp 
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)