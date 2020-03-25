---
title: Avertissement du compilateur (niveau 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: af97c72f496177d2e94cf18f9685ac33c5e62404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185657"
---
# <a name="compiler-warning-level-1-c4742"></a>Avertissement du compilateur (niveau 1) C4742

'var’a un alignement différent dans’fichier1 'et’fichier2 ' : nombre et nombre

Une variable externe qui a été référencée ou définie dans deux fichiers a un alignement différent dans ces fichiers. Cet avertissement est émis lorsque le compilateur détecte que `__alignof` pour la variable dans *fichier1* diffère de `__alignof` pour la variable dans *fichier2*. Cela peut être dû à l’utilisation de types incompatibles lors de la déclaration de variables dans des fichiers différents, ou à l’aide de `#pragma pack` sans correspondance dans des fichiers différents.

Pour résoudre cet avertissement, utilisez la même définition de type ou utilisez des noms différents pour les variables.

Pour plus d’informations, consultez l' [opérateur](../../cpp/alignof-operator.md) [Pack](../../preprocessor/pack.md) et __alignof.

## <a name="example"></a>Exemple

Il s’agit du premier fichier qui définit le type.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4742.

```c
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
