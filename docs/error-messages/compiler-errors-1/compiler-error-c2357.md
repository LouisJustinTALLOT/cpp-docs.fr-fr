---
title: Erreur du compilateur C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: 1872672e776ad13bf16be5ae69729f4f68d8f3b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302031"
---
# <a name="compiler-error-c2357"></a>Erreur du compilateur C2357

'identificateur' : doit être une fonction de type 'type'

Votre code déclare une version de la `atexit` fonction qui ne correspond pas à la version déclarée en interne par le compilateur. Déclarer `atexit` comme suit :

```
int __cdecl atexit(void (__cdecl *)());
```

Pour plus d’informations, consultez [init_seg](../../preprocessor/init-seg.md).

L’exemple suivant génère l’erreur C2357 :

```
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```