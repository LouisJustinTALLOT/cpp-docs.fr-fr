---
title: Mots clés contextuels (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: ca289a7ebd4578d5c67bb5d3e403d2a9a2756520
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516124"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>Mots clés contextuels (C++/CLI et C++/CX)

Les *mots clés contextuels* sont des éléments de langage reconnus uniquement dans des contextes spécifiques. En dehors du contexte spécifique, un mot clé contextuel peut être un symbole défini par l'utilisateur.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Remarques

Voici une liste de mots clés contextuels :

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [literal](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [propriété](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where` (partie de [Génériques](generics-cpp-component-extensions.md))

Pour des raisons de lisibilité, vous pouvez limiter votre utilisation des mots clés contextuels comme symboles définis par l’utilisateur.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Remarques

(Il n’existe aucune note spécifique à la plateforme pour cette fonctionnalité.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Remarques

(Il n’existe aucune note spécifique à la plateforme pour cette fonctionnalité.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre que dans le contexte approprié, le mot clé contextuel **property** peut être utilisé pour définir une propriété et une variable.

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)