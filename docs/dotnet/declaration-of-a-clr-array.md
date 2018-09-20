---
title: Déclaration d’un tableau CLR | Microsoft Docs
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
ms.openlocfilehash: c3de17bb293e10c4e1a2287ef12b934633b1fe21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426456"
---
# <a name="declaration-of-a-clr-array"></a>Déclaration d'un tableau CLR

La syntaxe pour déclarer, instancier et initialiser un tableau managé a changé d’Extensions managées pour C++ vers Visual C++.

La déclaration d’un objet de tableau CLR dans les Extensions managées était une extension de la déclaration de tableau standard dans laquelle un `__gc` mot clé a été placé entre le nom de l’objet de tableau et sa dimension éventuellement remplie de virgules, comme dans les deux suivants exemples :

```
void PrintValues( Object* myArr __gc[]);
void PrintValues( int myArr __gc[,,]);
```

Ceci a été simplifié dans la nouvelle syntaxe, dans lequel nous utilisons une déclaration de type modèle pour la bibliothèque C++ Standard `vector` déclaration. Le premier paramètre indique le type d’élément. Le deuxième paramètre spécifie la dimension du tableau (valeur par défaut est 1, par conséquent, seules les dimensions plusieurs nécessitent un deuxième argument). L’objet tableau lui-même est un handle de suivi et doit donc recevoir un chapeau. Si le type d’élément est également un type référence, elle requiert également un chapeau. Par exemple, l’exemple ci-dessus, exprimées dans la nouvelle syntaxe se présente comme suit :

```
void PrintValues( array<Object^>^ myArr );
void PrintValues( array<int,3>^ myArr );
```

Comme un type référence est un handle de suivi plutôt qu’un objet, il est possible de spécifier un tableau CLR comme type de retour d’une fonction. (En revanche, il n’est pas possible de spécifier le tableau natif comme type de retour d’une fonction.) La syntaxe permettant de le faire dans les Extensions managées était pas assez intuitive. Exemple :

```
Int32 f() [];
int GetArray() __gc[];
```

Dans Visual C++, la déclaration est beaucoup plus simple. Par exemple :

```
array<Int32>^ f();
array<int>^ GetArray();
```

L’initialisation de raccourci d’un tableau managé local est pris en charge dans les deux versions du langage. Exemple :

```
int GetArray() __gc[] {
   int a1 __gc[] = { 1, 2, 3, 4, 5 };
   Object* myObjArray __gc[] = {
      __box(26), __box(27), __box(28), __box(29), __box(30)
   };
   return a1;
}
```

est considérablement simplifié dans la nouvelle syntaxe (Notez que, comme le boxing est implicite dans la nouvelle syntaxe, le `__box` opérateur a été éliminé - voir [Types valeur et leurs comportements (C++ / c++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) pour une discussion) :

```
array<int>^ GetArray() {
   array<int>^ a1 = {1,2,3,4,5};
   array<Object^>^ myObjArray = {26,27,28,29,30};
   return a1;
}
```

Un tableau étant un type de référence CLR, la déclaration de chaque objet de tableau est un handle de suivi. Par conséquent, les objets de tableau doivent être alloués sur le tas CLR. (La notation abrégée masque l’allocation de tas managé.) Voici la forme explicite d’une initialisation d’objet tableau sous Extensions managées :

```
Object* myArray[] = new Object*[2];
String* myMat[,] = new String*[4,4];
```

Dans la nouvelle syntaxe, le `new` expression est remplacée par `gcnew`. Les tailles de dimensions sont passés comme paramètres à la `gcnew` expression, comme suit :

```
array<Object^>^ myArray = gcnew array<Object^>(2);
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);
```

Dans la nouvelle syntaxe, une liste d’initialisation explicite peut suivre le `gcnew` expression ; cela n’était pas prise en charge dans les Extensions managées. Exemple :

```
// explicit initialization list following gcnew
// was not supported in Managed Extensions
array<Object^>^ myArray =
   gcnew array<Object^>(4){ 1, 1, 2, 3 };
```

## <a name="see-also"></a>Voir aussi

[Types managés (C++ / c++ / CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Tableaux](../windows/arrays-cpp-component-extensions.md)