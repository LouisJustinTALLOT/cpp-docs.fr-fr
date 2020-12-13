---
description: 'En savoir plus sur : erreur du compilateur C2236'
title: Erreur du compilateur C2236
ms.date: 11/04/2016
f1_keywords:
- C2236
helpviewer_keywords:
- C2236
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
ms.openlocfilehash: 91b04cad6be02a3a50a21af9ef3397fb17d9c43b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338737"
---
# <a name="compiler-error-c2236"></a>Erreur du compilateur C2236

jeton 'identificateur' inattendu. N'auriez-vous pas oublié un ';' ?

L'identificateur est déjà défini comme un type et ne peut pas être remplacé par un type défini par l'utilisateur.

L'exemple suivant génère l'erreur C2236 :

```cpp
// C2236.cpp
// compile with: /c
int class A {};  // C2236 "int class" is unexpected
int i;
class B {};
```
