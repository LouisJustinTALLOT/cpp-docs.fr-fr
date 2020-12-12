---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4138'
title: Avertissement du compilateur (niveau 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: 68789c7300944c7435431688ff147f40cd4cadb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278023"
---
# <a name="compiler-warning-level-1-c4138"></a>Avertissement du compilateur (niveau 1) C4138

'*/' trouvé à l'extérieur du commentaire

Le délimiteur de commentaire de clôture n’est pas précédé d’un délimiteur de commentaire d’ouverture. Le compilateur suppose un espace entre l’astérisque ( <strong>\*</strong> ) et la barre oblique (/).

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
