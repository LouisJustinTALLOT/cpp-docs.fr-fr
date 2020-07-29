---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 5f95e9fc55acd33705b855c7c4f0ef268d4776a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219688"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Permet d’utiliser des mots clés C++ en tant qu’identificateurs.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="syntax"></a>Syntaxe

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Notes

L’utilisation du mot clé **__identifier** pour les identificateurs qui ne sont pas des mots clés est autorisée, mais fortement déconseillée d’un point de vue stylistique.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

### <a name="examples"></a>Exemples

**Exemple**

Dans l’exemple suivant, une classe nommée `template` est créée en C# et distribuée sous la forme d’une dll. Dans le programme C++/CLI qui utilise la `template` classe, le **`__identifier`** mot clé masque le fait qu’il `template` s’agit d’un mot clé C++ standard.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Le mot clé **__identifier** est valide avec l’option du compilateur `/clr`.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Dans l’exemple suivant, une classe nommée `template` est créée en C# et distribuée sous la forme d’une dll. Dans le programme C++/CLI qui utilise la `template` classe, le **`__identifier`** mot clé masque le fait qu’il `template` s’agit d’un mot clé C++ standard.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
