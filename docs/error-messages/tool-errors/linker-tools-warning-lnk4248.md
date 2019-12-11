---
title: Avertissement des outils Éditeur de liens LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 4ba05ef067c539dc9c0aca6dc2a395748fd217a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988100"
---
# <a name="linker-tools-warning-lnk4248"></a>Avertissement des outils Éditeur de liens LNK4248

jeton TypeRef non résolu (jeton) pour’type'; l’image risque de ne pas s’exécuter

Un type n’a pas de définition dans les métadonnées MSIL.

LNK4248 peut se produire lorsqu’il n’existe qu’une déclaration anticipée pour un type dans un module MSIL (compilé avec **/CLR**), où le type est référencé dans le module MSIL, et où le module MSIL est lié à un module natif qui a une définition pour le type.

Dans ce cas, l’éditeur de liens fournira la définition de type natif dans les métadonnées MSIL, ce qui peut fournir le comportement correct.

Toutefois, si une déclaration de type Forward est un type CLR, la définition de type natif de l’éditeur de liens peut ne pas être correcte

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Indiquez la définition du type dans le module MSIL.

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK4248. Définissez le struct A à résoudre.

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>Exemple

L’exemple suivant présente une définition anticipée d’un type.

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK4248.

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
