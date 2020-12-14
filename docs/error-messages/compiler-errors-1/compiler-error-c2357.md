---
description: 'En savoir plus sur : erreur du compilateur C2357'
title: Erreur du compilateur C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: a58317fc4706d6385d3753a434c8e4fd80dc79b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276736"
---
# <a name="compiler-error-c2357"></a>Erreur du compilateur C2357

'identificateur' : doit être une fonction de type’type'

Votre code déclare une version de la `atexit` fonction qui ne correspond pas à la version déclarée en interne par le compilateur. Déclarez `atexit` comme suit :

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
