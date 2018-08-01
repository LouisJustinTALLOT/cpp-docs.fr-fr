---
title: __if_exists, instruction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac866487c25ee4ce75abbebe9b9f9c2a5e97828
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405942"
---
# <a name="ifexists-statement"></a>__if_exists, instruction
Le **__if_exists** instruction teste si l’identificateur spécifié existe. Si l'identificateur existe, le bloc d'instructions spécifié est exécuté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*identifier*|Identificateur dont vous voulez tester l'existence.|  
|*Instructions*|Une ou plusieurs instructions à exécuter si *identificateur* existe.|  
  
## <a name="remarks"></a>Notes  
  
> [!CAUTION]
>  Pour obtenir des résultats plus fiables, utilisez le **__if_exists** instruction sous les contraintes suivantes.  
  
-   Appliquer le **__if_exists** instruction uniquement aux types simples, et non des modèles.  
  
-   Appliquer le **__if_exists** instruction aux identificateurs à la fois à l’intérieur ou en dehors d’une classe. N’appliquez pas le **__if_exists** instruction aux variables locales.  
  
-   Utilisez le **__if_exists** instruction uniquement dans le corps d’une fonction. En dehors du corps d’une fonction, le **__if_exists** instruction peut tester uniquement les types entièrement définis.  
  
-   Lorsque vous vérifiez la présence de fonctions surchargées, vous ne pouvez pas effectuer le test sur une forme spécifique de la surcharge.  
  
 Le complément de la **__if_exists** instruction est la [__if_not_exists](../cpp/if-not-exists-statement.md) instruction.  
  
## <a name="example"></a>Exemple  
 Notez que cet exemple utilise des modèles, ce qui n'est pas recommandé.  
  
```cpp 
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## <a name="output"></a>Sortie  
  
```Output  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de sélection](../cpp/selection-statements-cpp.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [__if_not_exists, instruction](../cpp/if-not-exists-statement.md)