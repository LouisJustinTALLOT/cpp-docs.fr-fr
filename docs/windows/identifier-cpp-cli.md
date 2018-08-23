---
title: __identifier (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: d578c820660d99e6fa217a14181330d258ab081b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613320"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

Permet d’utiliser des mots clés Visual C++ en tant qu’identificateurs.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="syntax"></a>Syntaxe

```cpp
__identifier(
Visual_C++_keyword
)  
```

### <a name="remarks"></a>Notes

Utilisation de la **__identifier** mot clé pour les identificateurs qui ne sont pas des mots clés est autorisée, mais fortement déconseillée en tant qu’une question de style.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

### <a name="examples"></a>Exemples

**Exemple**

Dans l’exemple suivant, une classe nommée **modèle** est créé en c# et distribué en tant que DLL. Dans le programme Visual C++ qui utilise le **modèle** (classe), le **__identifier** mot clé dissimule le fait que **modèle** est un mot clé C++ standard.

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

Dans l’exemple suivant, une classe nommée **modèle** est créé en c# et distribué en tant que DLL. Dans le programme Visual C++ qui utilise le **modèle** (classe), le **__identifier** mot clé dissimule le fait que **modèle** est un mot clé C++ standard.

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

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)  
[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)