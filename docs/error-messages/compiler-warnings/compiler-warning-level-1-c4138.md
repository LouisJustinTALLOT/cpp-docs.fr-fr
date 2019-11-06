---
title: Avertissement du compilateur (niveau 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e6e368f27371b744efa4006630938f68f51a2ca0
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627097"
---
# <a name="compiler-warning-level-1-c4138"></a>Avertissement du compilateur (niveau 1) C4138

'*/' trouvé à l'extérieur du commentaire

Le délimiteur de commentaire de clôture n’est pas précédé d’un délimiteur de commentaire d’ouverture. Le compilateur suppose l’existence d’un espace entre l’astérisque (<strong>\*</strong>) et la barre oblique (/).

## <a name="example"></a>Exemple

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

Cet avertissement peut être provoqué par une tentative d’imbrication de commentaires.

Cet avertissement peut être résolu en plaçant en commentaire des sections de code contenant elles-mêmes des commentaires, en incluant le code dans un bloc **#if/#endif** et en définissant une valeur zéro pour l’expression de contrôle :

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```