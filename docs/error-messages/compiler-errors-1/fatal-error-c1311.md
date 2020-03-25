---
title: Erreur irrécupérable 1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203266"
---
# <a name="fatal-error-c1311"></a>Erreur irrécupérable 1311

Le format COFF ne peut pas initialiser de manière statique’var’avec le nombre d’octets d’une adresse

Une adresse dont la valeur n’est pas connue au moment de la compilation ne peut pas être assignée de manière statique à une variable dont le type a un stockage de moins de 4 octets.

Cette erreur peut se produire sur du code qui est C++autrement valide.

L’exemple suivant montre une condition qui peut provoquer C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
