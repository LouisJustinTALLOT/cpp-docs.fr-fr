---
title: Erreur du compilateur C2955 | Documents Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2955
dev_langs:
- C++
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 686fb51d1e72f0835a673d00c05ade21a7580515
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245947"
---
# <a name="compiler-error-c2955"></a>Erreur du compilateur C2955
’identificateur’ : l’utilisation d’un modèle de classe ou d’un générique d’alias requiert une liste d’arguments modèles ou génériques  
  
 Vous ne pouvez pas utiliser un modèle de classe ni un générique de classe comme identificateur sans une liste d’arguments modèles ou génériques.  
  
 Pour plus d’informations, consultez [les modèles de classe](../../cpp/class-templates.md).  
  
 L'exemple suivant génère l'erreur C2955 et montre comment la corriger :  
  
```  
// C2955.cpp  
// compile with: /c  
template<class T>   
class X {};  
  
X x1;   // C2955  
X<int> x2;   // OK - this is how to fix it.  
```  
  
 L'erreur C2955 peut également se produire lors de la tentative d'une définition hors ligne d'une fonction déclarée dans un modèle de classe :  
  
```  
// C2955_b.cpp  
// compile with: /c  
template <class T>  
class CT {  
public:  
   void CTFunc();  
   void CTFunc2();  
};  
  
void CT::CTFunc() {}   // C2955  
  
// OK - this is how to fix it  
template <class T>  
void CT<T>::CTFunc2() {}  
  
```  
  
 L'erreur C2955 peut également se produire lors de l'utilisation de génériques :  
  
```  
// C2955_c.cpp  
// compile with: /clr  
generic <class T>   
ref struct GC {   
   T t;  
};  
  
int main() {  
   GC^ g;   // C2955  
   GC <int>^ g;  
}  
```

## <a name="example"></a>Exemple
**Visual Studio 2017 et versions ultérieur :** le compilateur diagnostique correctement les listes d’arguments de modèle manquant lorsque le modèle apparaît dans une liste de paramètres de modèle (par exemple dans le cadre d’un paramètre de modèle sans type ou d’un argument de modèle par défaut). Le code suivant se compile dans Visual Studio 2015, mais génère une erreur dans Visual Studio 2017 :

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
