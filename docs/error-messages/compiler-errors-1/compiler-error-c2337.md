---
description: 'En savoir plus sur : erreur du compilateur C2337'
title: Erreur du compilateur C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: 44def6fe9c220699e3687ce9b843f977528b5e15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234850"
---
# <a name="compiler-error-c2337"></a>Erreur du compilateur C2337

> '*attribute-name*' : attribut introuvable

Votre code utilise un attribut qui n’est pas pris en charge dans ce contexte. Ou bien, l’attribut n’est pas disponible dans cette version du compilateur. Pour résoudre ce problème, supprimez l’attribut non pris en charge.

L’exemple suivant génère l’erreur C2337 :

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
