---
title: Erreur du compilateur C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 820a620b7e4414123c56433f84536393834f6fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208400"
---
# <a name="compiler-error-c2732"></a>Erreur du compilateur C2732

les spécifications de la liaison contredisent les spécifications antérieures pour 'fonction'

La fonction est déjà déclarée avec un autre spécificateur de liaison.

Cette erreur peut être provoquée par des fichiers Include possédant des spécificateurs de liaison différents.

Pour corriger cette erreur, modifiez les instructions `extern` afin que les liaisons correspondent. En particulier, n'imbriquez pas de directives `#include` dans des blocs `extern "C"`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2732 :

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```