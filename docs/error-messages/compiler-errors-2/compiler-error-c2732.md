---
title: Erreur du compilateur C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 61bac8c1b5c9e029cc5833f458669b490fed8c91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755796"
---
# <a name="compiler-error-c2732"></a>Erreur du compilateur C2732

les spécifications de la liaison contredisent les spécifications antérieures pour 'fonction'

La fonction est déjà déclarée avec un autre spécificateur de liaison.

Cette erreur peut être provoquée par des fichiers Include possédant des spécificateurs de liaison différents.

Pour corriger cette erreur, modifiez les instructions `extern` afin que les liaisons correspondent. En particulier, n'imbriquez pas de directives `#include` dans des blocs `extern "C"`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2732 :

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
