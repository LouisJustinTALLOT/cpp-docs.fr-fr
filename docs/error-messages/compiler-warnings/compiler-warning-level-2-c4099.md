---
title: Avertissement du compilateur (niveau 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349813"
---
# <a name="compiler-warning-level-2-c4099"></a>Avertissement du compilateur (niveau 2) C4099

'identificateur' : nom de type à l’aide de « objecttype1 » est maintenant affichée à l’aide de 'objecttype2'

Un objet déclaré comme structure est défini comme une classe ou un objet déclaré en tant que classe est défini en tant que structure. Le compilateur utilise le type donné dans la définition.

## <a name="example"></a>Exemple

L’exemple suivant génère C4099.

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```