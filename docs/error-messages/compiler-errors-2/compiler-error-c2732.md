---
title: Erreur du compilateur C2732 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 040fd73bcb69ef032d5c6150bb157337f34a2088
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079659"
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