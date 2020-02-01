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
ms.openlocfilehash: 395f1443f4eef16d9eea44c23a6e3288daf03d14
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912839"
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

### <a name="requirements"></a>Configuration requise pour

Option du compilateur : `/ZW`

### <a name="examples"></a>Exemples

**Exemple**

Dans l’exemple suivant, une classe nommée **template** est créée dans C# et distribuée en tant que DLL. Dans le programme C++/CLI qui utilise la classe **template**, le mot clé **__identifier** dissimule le fait que **template** est un mot clé C++ standard.

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

### <a name="requirements"></a>Configuration requise pour

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Dans l’exemple suivant, une classe nommée **template** est créée dans C# et distribuée en tant que DLL. Dans le programme C++/CLI qui utilise la classe **template**, le mot clé **__identifier** dissimule le fait que **template** est un mot clé C++ standard.

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

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)