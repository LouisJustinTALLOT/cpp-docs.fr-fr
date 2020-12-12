---
description: 'En savoir plus sur : erreur du compilateur C2732'
title: Erreur du compilateur C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 1ca97fbf46685af1df37b8caf82a03effc1ec6bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123212"
---
# <a name="compiler-error-c2732"></a>Erreur du compilateur C2732

les spécifications de la liaison contredisent les spécifications antérieures pour 'fonction'

La fonction est déjà déclarée avec un autre spécificateur de liaison.

Cette erreur peut être provoquée par des fichiers Include possédant des spécificateurs de liaison différents.

Pour corriger cette erreur, modifiez les **`extern`** instructions de manière à ce que les liaisons s’accordent. En particulier, n'imbriquez pas de directives `#include` dans des blocs `extern "C"`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2732 :

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
