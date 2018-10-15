---
title: __identifier (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 09a8b69402dbe3812bdd49f8944c979300209bff
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328270"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

Permet l’utilisation de mots clés C++ comme identificateurs.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="syntax"></a>Syntaxe

```cpp
__identifier(C++_keyword)  
```

### <a name="remarks"></a>Notes

Utilisation de la **__identifier** mot clé pour les identificateurs qui ne sont pas des mots clés est autorisée, mais fortement déconseillée en tant qu’une question de style.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

### <a name="examples"></a>Exemples

**Exemple**

Dans l’exemple suivant, une classe nommée **modèle** est créé en c# et distribué en tant que DLL. En C / c++ / programme CLI qui utilise le **modèle** (classe), le **__identifier** mot clé dissimule le fait qui **modèle** est un mot clé C++ standard.

```cs
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

Le **__identifier** mot clé est valide avec le `/clr` option du compilateur.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Dans l’exemple suivant, une classe nommée **modèle** est créé en c# et distribué en tant que DLL. En C / c++ / programme CLI qui utilise le **modèle** (classe), le **__identifier** mot clé dissimule le fait qui **modèle** est un mot clé C++ standard.

```cs
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

[Extensions de composant pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Extensions de composant pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)