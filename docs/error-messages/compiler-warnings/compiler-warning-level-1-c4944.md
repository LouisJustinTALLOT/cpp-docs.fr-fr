---
title: Compilateur avertissement (niveau 1) C4944 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4944
dev_langs:
- C++
helpviewer_keywords:
- C4944
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdf155ce5fb53bb4b1b5914d7738c8c12f458888
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105498"
---
# <a name="compiler-warning-level-1-c4944"></a>Avertissement du compilateur (niveau 1) C4944

'symbole' : impossible d’importer le symbole de 'assembly1', car 'symbole' existe déjà dans la portée actuelle

Un symbole a été défini dans un fichier de code source, puis une instruction #using a référencé un assembly définissant également le symbole. Le symbole contenu dans l’assembly est ignoré.

## <a name="example"></a>Exemple

Dans l’exemple suivant, un composant est créé avec un type appelé ClassA.

```
// C4944.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

## <a name="example"></a>Exemple

Les exemples suivants génèrent l’erreur C4944.

```
// C4944b.cpp
// compile with: /clr /W1
class ClassA {
public:
   int u;
};

#using "C4944.dll"   // C4944 ClassA also defined C4944.dll

int main() {
   ClassA * x = new ClassA();
   x->u = 9;
   System::Console::WriteLine(x->u);
}
```