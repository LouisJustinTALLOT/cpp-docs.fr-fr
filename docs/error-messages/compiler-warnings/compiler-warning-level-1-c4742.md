---
title: Avertissement du compilateur (niveau 1) C4742
ms.date: 07/22/2020
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: e6ecd082a9f6d690414761d11d3a0adf101f87c2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233234"
---
# <a name="compiler-warning-level-1-c4742"></a>Avertissement du compilateur (niveau 1) C4742

> '*variable*'a un alignement différent dans'*fichier1*'et'*fichier2*' : *nombre1* et *nombre2*

Une variable externe qui a été référencée ou définie dans deux fichiers a un alignement différent dans ces fichiers.

## <a name="remarks"></a>Notes

Cet avertissement est émis lorsque le compilateur détecte que **`alignof`** pour la variable dans *fichier1* est différent de **`alignof`** pour la variable dans *fichier2*. Cela peut être dû à l’utilisation de types incompatibles lors de la déclaration de variables dans des fichiers différents, ou à l’aide d’une non-correspondance `#pragma pack` dans des fichiers différents.

Pour résoudre cet avertissement, utilisez la même définition de type ou utilisez des noms différents pour les variables.

Pour plus d’informations, [`pack`](../../preprocessor/pack.md) consultez [ `alignof` opérateur](../../cpp/alignof-operator.md)and.

## <a name="example"></a>Exemple

Il s’agit du premier fichier qui définit le type.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

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
