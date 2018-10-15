---
title: Mots clés contextuels (C++ / c++ / CLI et c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal_CPP
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d02939e61da4a247b46da5637c38d01e7990c49
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327932"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>Mots clés contextuels (C++ / c++ / CLI et c++ / CX)

*Mots clés contextuels* sont des éléments de langage reconnus uniquement dans des contextes spécifiques. En dehors du contexte spécifique, un mot clé contextuel peut être un symbole défini par l'utilisateur.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Notes

Voici une liste de mots clés contextuels :

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [delegate](../windows/delegate-cpp-component-extensions.md)

- [event](../windows/event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [literal](../windows/literal-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [propriété](../windows/property-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- `where` (dans le cadre de [génériques](../windows/generics-cpp-component-extensions.md))

Pour des raisons de lisibilité, vous souhaiterez limiter votre utilisation des mots clés contextuels comme symboles définis par l’utilisateur.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

(Il n’existe aucune note spécifique à la plateforme pour cette fonctionnalité.)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

(Il n’existe aucune note spécifique à la plateforme pour cette fonctionnalité.)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre que, dans le contexte approprié, le **propriété** mot clé contextuel peut être utilisé pour définir une propriété et une variable.

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

[Extensions de composant pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)