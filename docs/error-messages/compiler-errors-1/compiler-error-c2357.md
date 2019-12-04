---
title: Erreur du compilateur C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: ce1926468bac7e44485be5c0a0944fdf12dce3d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759917"
---
# <a name="compiler-error-c2357"></a>Erreur du compilateur C2357

'identificateur' : doit être une fonction de type’type'

Votre code déclare une version de la fonction `atexit` qui ne correspond pas à la version déclarée en interne par le compilateur. Déclarez `atexit` comme suit :

```
int __cdecl atexit(void (__cdecl *)());
```

Pour plus d’informations, consultez [init_seg](../../preprocessor/init-seg.md).

L’exemple suivant génère l’C2357 :

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```
