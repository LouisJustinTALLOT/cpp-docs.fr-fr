---
title: Avertissement du compilateur (niveau 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 812f36884d24ac988353dbcb18609d4c506e3110
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164259"
---
# <a name="compiler-warning-level-1-c4036"></a>Avertissement du compilateur (niveau 1) C4036

'type' sans nom comme paramètre réel

Une structure, union, énumération ou classe utilisée comme paramètre réel n’a pas reçu de nom de type. Si vous utilisez [/Zg](../../build/reference/zg-generate-function-prototypes.md) pour générer des prototypes de fonction, le compilateur émet cet avertissement et met en commentaire le paramètre formel dans le prototype généré.

Spécifiez un nom de type pour remédier à cet avertissement.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4036.

```c
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```
