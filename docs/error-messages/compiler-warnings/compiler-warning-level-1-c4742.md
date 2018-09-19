---
title: Compilateur avertissement (niveau 1) C4742 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4742
dev_langs:
- C++
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 622a1b1cd62024da58191ce1312c391dd39e0d28
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088590"
---
# <a name="compiler-warning-level-1-c4742"></a>Avertissement du compilateur (niveau 1) C4742

'var' a un alignement différent dans 'fichier1' et 'fichier2' : nombre et nombre

Une variable externe référencée ou définie dans deux fichiers a un alignement différent dans ces fichiers. Cet avertissement est émis lorsque le compilateur détecte que `__alignof` pour la variable dans *file1* diffère `__alignof` pour la variable dans *fichier2*. Cela peut être dû à l’aide des types incompatibles lors de la déclaration de variable dans un autre fichier ou à l’aide de non mise en correspondance de `#pragma pack` dans différents fichiers.

Pour résoudre cet avertissement, utilisez la même définition de type ou utiliser des noms différents pour les variables.

Pour plus d’informations, consultez [pack](../../preprocessor/pack.md) et [__alignof, opérateur](../../cpp/alignof-operator.md).

## <a name="example"></a>Exemple

Il s’agit du premier fichier qui définit le type.

```
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Exemple

L’exemple suivant génère C4742.

```
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```