---
title: Compilateur avertissement (niveau 1) C4138 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2e637c73482b1a59034d6a269ea2240445bdef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046905"
---
# <a name="compiler-warning-level-1-c4138"></a>Avertissement du compilateur (niveau 1) C4138

'*/' trouvé à l'extérieur du commentaire

Le délimiteur de commentaire de clôture n’est pas précédé d’un délimiteur de commentaire d’ouverture. Le compilateur suppose un espace entre l’astérisque (<strong>\*</strong>) et la barre oblique (/).

## <a name="example"></a>Exemple

```
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

Cet avertissement peut être provoqué par une tentative d’imbrication de commentaires.

Cet avertissement peut être résolu en plaçant en commentaire des sections de code contenant elles-mêmes des commentaires, en incluant le code dans un bloc **#if/#endif** et en définissant une valeur zéro pour l’expression de contrôle :

```
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```