---
title: abstract (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6474b659070793ddfa4e21d15e65be30f16a49bb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641806"
---
# <a name="abstract--c-component-extensions"></a>abstract  (extensions du composant C++)
Le **abstraite** mot clé déclare :  
  
-   Un type peut être utilisé comme type de base, mais le type lui-même ne peut pas être instancié.  
  
-   Une fonction membre de type peut être définie uniquement dans un type dérivé.  
  
## <a name="all-platforms"></a>Toutes les plateformes  
### <a name="syntax"></a>Syntaxe 
  
```cpp  
      class-declaration  
      class-identifier  
      abstract {}  
virtualreturn-typemember-function-identifier() abstract ;  
```  
  
### <a name="remarks"></a>Notes
  
 Le premier exemple de syntaxe déclare une classe comme étant abstraite. Le *déclaration de classe* composant peut être une déclaration C++ native (**classe** ou **struct**), ou une déclaration d’extension C++ (**classe ref** ou **ref struct**) si le `/ZW` ou `/clr` option du compilateur est spécifiée.  
  
 Le deuxième exemple de syntaxe déclare une fonction membre virtuelle comme étant abstraite. La déclaration d'une fonction comme étant abstraite revient à déclarer qu'il s'agit d'une fonction virtuelle pure. La déclaration d'une fonction membre comme étant abstraite entraîne également la déclaration de la classe englobante comme étant abstraite.  
  
 Le **abstraite** mot clé est prise en charge dans le code natif et spécifique à la plateforme ; autrement dit, il peut être compilé avec ou sans le `/ZW` ou `/clr` option du compilateur.  
  
 Vous pouvez détecter au moment de la compilation si un type est abstrait avec le `__is_abstract(type)` trait de type. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Le **abstraite** mot clé est un spécificateur de substitution contextuel. Pour plus d’informations sur les mots clés contextuels, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md). Pour plus d’informations sur les spécificateurs de substitution, consultez [Comment : déclarer des spécificateurs de substitution dans les Compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Pour plus d’informations, consultez [classes et structs Ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/clr`  
  
### <a name="examples"></a>Exemples  
  
 L’exemple de code suivant génère une erreur car classe `X` est marquée **abstraite**.  
  
```cpp  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 L’exemple de code suivant génère une erreur, car il instancie une classe native marquée **abstraite**. Cette erreur se produit avec ou sans l'option du compilateur `/clr`.  
  
```cpp  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
```  
  
 L’exemple de code suivant génère une erreur car fonction `f` inclut une définition, mais est marqué comme **abstraite**. La dernière instruction de l'exemple montre que la déclaration d'une fonction virtuelle abstraite équivaut à la déclaration d'une fonction virtuelle pure.  
  
```cpp  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)