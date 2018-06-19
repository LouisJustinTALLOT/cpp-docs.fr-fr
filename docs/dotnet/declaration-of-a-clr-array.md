---
title: Déclaration d’un tableau CLR | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8d8b2a5d348887d56a1221a5a9125449e5356b9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112132"
---
# <a name="declaration-of-a-clr-array"></a>Déclaration d'un tableau CLR
La syntaxe de déclaration, instancier et initialiser un tableau managé a changé entre les Extensions managées pour C++ vers Visual C++.  
  
 La déclaration d’un objet de tableau CLR dans les Extensions managées était une extension de la déclaration de tableau standard dans laquelle un `__gc` (mot clé) a été placé entre le nom de l’objet tableau et sa dimension éventuellement remplie de virgules, comme dans les deux suivants exemples :  
  
```  
void PrintValues( Object* myArr __gc[]);  
void PrintValues( int myArr __gc[,,]);  
```  
  
 Cela a été simplifié dans la nouvelle syntaxe, dans laquelle nous utilisons une déclaration de type modèle semblable à la bibliothèque Standard C++ `vector` déclaration. Le premier paramètre indique le type d’élément. Le deuxième paramètre spécifie la dimension du tableau (avec une valeur par défaut 1, par conséquent, seules les dimensions multiples nécessitent un deuxième argument). L’objet tableau lui-même est un handle de suivi et doit donc recevoir un chapeau. Si le type d’élément est également un type référence, elle requiert également un chapeau. Par exemple, l’exemple ci-dessus, lorsqu’ils sont exprimés dans la nouvelle syntaxe se présente comme suit :  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
 Comme un type référence est un handle de suivi plutôt qu’un objet, il est possible de spécifier un tableau CLR comme type de retour d’une fonction. (En revanche, il n’est pas possible de spécifier le tableau natif comme type de retour d’une fonction.) La syntaxe de cette opération dans les Extensions managées était quelque peu non intuitive. Par exemple :  
  
```  
Int32 f() [];  
int GetArray() __gc[];  
```  
  
 Dans Visual C++, la déclaration est beaucoup plus simple. Par exemple :  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
 L’initialisation de la forme abrégée d’un tableau managé local est pris en charge dans les deux versions du langage. Par exemple :  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = {   
      __box(26), __box(27), __box(28), __box(29), __box(30)  
   };  
   return a1;  
}  
```  
  
 est considérablement simplifié dans la nouvelle syntaxe (étant donné que la conversion boxing est implicite dans la nouvelle syntaxe, le `__box` opérateur a été éliminé - voir [Types valeur et leurs comportements (C + c++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) pour une présentation) :  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
   return a1;  
}  
```  
  
 Un tableau étant un type de référence CLR, la déclaration de chaque objet du tableau est un handle de suivi. Par conséquent, les objets de tableau doivent être alloués sur le tas CLR. (La notation abrégée masque l’allocation de tas managé.) Voici la forme explicite d’une initialisation d’objet tableau sous Extensions managées :  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 Dans la nouvelle syntaxe, le `new` expression est remplacée par `gcnew`. Les tailles de dimensions sont passés comme paramètres à la `gcnew` expression, comme suit :  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 Dans la nouvelle syntaxe, une liste d’initialisation explicite peut suivre le `gcnew` expression ; cela n’était pas prise en charge dans les Extensions managées. Par exemple :  
  
```  
// explicit initialization list following gcnew   
// was not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types managés (C + c++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Tableaux](../windows/arrays-cpp-component-extensions.md)