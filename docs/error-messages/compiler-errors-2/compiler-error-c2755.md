---
title: Erreur du compilateur C2755
ms.date: 11/04/2016
f1_keywords:
- C2755
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
ms.openlocfilehash: c2238058dc4b7df6bbe33e98d6ccde996f36b782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227970"
---
# <a name="compiler-error-c2755"></a>Erreur du compilateur C2755

'param' : paramètre sans type d’une spécialisation partielle doit être un identificateur simple

Le paramètre sans type doit être un identificateur simple, quelque chose que le compilateur peut être convertie au moment de la compilation à un identificateur unique ou une valeur constante.

L’exemple suivant génère l’erreur C2755 :

```
// C2755.cpp
template<int I, int J>
struct A {};

template<int I>
struct A<I,I*5> {};   // C2755
// try the following line instead
// struct A<I,5> {};
```