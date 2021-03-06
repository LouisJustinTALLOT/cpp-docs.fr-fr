---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4691'
title: Avertissement du compilateur (niveau 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 3235b32a071e6b6a2a0afab122978f9fcb7e112a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238269"
---
# <a name="compiler-warning-level-1-c4691"></a>Avertissement du compilateur (niveau 1) C4691

'type' : le type référencé était attendu dans l’assembly non référencé’fichier', le type défini dans l’unité de traduction actuelle est utilisé à la place

Le fichier de métadonnées contenant la définition de type d’origine n’est pas référencé et le compilateur utilise une définition de type local.

Dans le cas où vous reconstruisez le *fichier*, C4691 peut être ignoré ou désactivé avec l' [Avertissement](../../preprocessor/warning.md)pragma.  Autrement dit, si le fichier que vous générez est le même que le fichier dans lequel le compilateur s’attend à trouver la définition de type, vous pouvez ignorer C4691.

Toutefois, un comportement inattendu peut se produire si le compilateur utilise une définition qui n’est pas du même assembly que celui référencé dans les métadonnées. Les types CLR sont tapés non seulement par le nom du type, mais également par l’assembly.  Autrement dit, un type Z de l’assembly z.dll est différent d’un type Z de l’assembly y.dll.

## <a name="examples"></a>Exemples

Cet exemple contient la définition de type d’origine.

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

Cet exemple référence C4691_a.dll et déclare un champ de type Original_Type.

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

L’exemple suivant génère l’C4691.  Notez que cet exemple contient une définition pour Original_Type et ne fait pas référence à C4691a.dll.

Pour résoudre le, référencez le fichier de métadonnées qui contient la définition de type d’origine et supprimez la déclaration et la définition locales.

```cpp
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```
