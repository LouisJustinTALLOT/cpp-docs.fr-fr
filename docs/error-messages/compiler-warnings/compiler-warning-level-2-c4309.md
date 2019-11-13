---
title: Avertissement du compilateur (niveau 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: 78d7d8130282a67c07046004ee61e802cfd97780
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052043"
---
# <a name="compiler-warning-level-2-c4309"></a>Avertissement du compilateur (niveau 2) C4309

'conversion' : troncation d’une valeur constante

La conversion de type entraîne une constante dépassant l’espace qui lui est alloué. Vous devrez peut-être utiliser un plus grand type pour la constante.

L’exemple suivant génère l’C4309 :

```cpp
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```