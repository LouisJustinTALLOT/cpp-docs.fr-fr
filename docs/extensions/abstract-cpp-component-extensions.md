---
description: 'En savoir plus sur : abstract (C++/CLI et C++/CX)'
title: résumé (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: e40d0d0c03bbf97b684d9e011f4bf614f6a44332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177118"
---
# <a name="abstract--ccli-and-ccx"></a>résumé (C++/CLI et C++/CX)

Le mot clé **abstract** peut déclarer :

- Un type peut être utilisé comme type de base, mais le type lui-même ne peut pas être instancié.

- Une fonction membre de type peut être définie uniquement dans un type dérivé.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="syntax"></a>Syntaxe

*class-declaration* *class-identifier* **abstract {}**

**`virtual`***type de retour* *membre-Function-identifier* **() abstract ;**

### <a name="remarks"></a>Notes

Le premier exemple de syntaxe déclare une classe comme étant abstraite. Le composant *de déclaration de classe* peut être une déclaration c++ native (**`class` * * * * ou **`struct`** ) ou une déclaration d’extension c++ (** ref class * * ou **ref struct**) si l' `/ZW` `/clr` option du compilateur ou est spécifiée.

Le deuxième exemple de syntaxe déclare une fonction membre virtuelle comme étant abstraite. La déclaration d'une fonction comme étant abstraite revient à déclarer qu'il s'agit d'une fonction virtuelle pure. La déclaration d'une fonction membre comme étant abstraite entraîne également la déclaration de la classe englobante comme étant abstraite.

Le mot clé **abstract** est pris en charge dans le code natif et spécifique à la plateforme ; autrement dit, il peut être compilé avec ou sans l’option du compilateur `/ZW` ou `/clr`.

Vous pouvez détecter, au moment de la compilation, si un type est abstrait avec le trait de type `__is_abstract(type)`. Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](compiler-support-for-type-traits-cpp-component-extensions.md).

Le mot clé **abstract** est un spécificateur de substitution contextuel. Pour plus d’informations sur les mots clés contextuels, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md). Pour plus d’informations sur les spécificateurs de substitution, consultez [Comment : déclarer des spécificateurs de substitution dans les compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>Windows Runtime

Pour plus d’informations, consultez [Classes et structures de référence](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant génère une erreur car la classe `X` est marquée comme **abstract**.

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

L’exemple de code suivant génère une erreur car il instancie une classe native marquée comme **abstract**. Cette erreur se produit avec ou sans l'option du compilateur `/clr`.

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

L’exemple de code suivant génère une erreur car la fonction `f` inclut une définition, mais elle est marquée comme **abstract**. La dernière instruction de l'exemple montre que la déclaration d'une fonction virtuelle abstraite équivaut à la déclaration d'une fonction virtuelle pure.

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

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
