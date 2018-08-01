---
title: protégé (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68cf69cd0c14d56c75a2c67d4369264e7a2ee440
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406170"
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Notes  
 Le **protégé** mot clé spécifie l’accès aux membres de classe dans le *-liste des membres* jusqu’au spécificateur d’accès suivant (**public** ou **privé**) ou à la fin de la définition de classe. Membres de classe déclarés comme **protégé** peut être utilisé uniquement par ce qui suit :  
  
-   Les fonctions membres de la classe qui a initialement déclaré ces membres.  
  
-   Les friends de la classe qui a initialement déclaré ces membres.  
  
-   Les classes dérivées ayant un accès public ou protégé à partir de la classe qui a initialement déclaré ces membres.  
  
-   Les classes directes dérivées de manière privée qui ont également un accès privé aux membres protégés.  
  
 Lorsqu’il précède le nom de classe de base, le **protégé** mot clé spécifie que les membres publics et protégés de la classe de base sont des membres protégés de ses classes dérivées.  
  
 Membres protégés ne sont pas aussi privés que **privé** membres, qui sont uniquement accessibles aux membres de la classe dans laquelle ils sont déclarés, mais ils ne sont pas aussi publics que **public** membres, qui sont accessibles dans n’importe quelle fonction.  
  
 Membres protégés qui sont également déclarés comme **statique** sont accessibles à n’importe quelle fonction ami ou un membre d’une classe dérivée. Membres protégés qui ne sont pas déclarés en tant que **statique** sont accessibles à leurs amis et des fonctions membres dans une classe dérivée uniquement par le biais d’un pointeur vers la référence à, ou un objet de la classe dérivée.  
  
 Pour plus d’informations, consultez [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [privé](../cpp/private-cpp.md)et accès aux membres de la [contrôle de l’accès aux membres de classe](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Spécifique /clr  
 Dans les types CLR, mots clés de spécificateur d’accès le C++ (**public**, **privé**, et **protégé**) peuvent affecter la visibilité des types et méthodes quant aux assemblys. Pour plus d’informations, consultez [contrôle d’accès de membre](member-access-control-cpp.md).  
  
> [!NOTE]
>  Fichiers compilés avec [/LN](../build/reference/ln-create-msil-module.md) ne sont pas affectés par ce comportement. Dans ce cas, toutes les classes managées (public ou privées) seront visibles.  
  
## <a name="end-clr-specific"></a>Spécifique END /clr  
  
## <a name="example"></a>Exemple  
  
```cpp 
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler l’accès aux membres de classe](member-access-control-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)