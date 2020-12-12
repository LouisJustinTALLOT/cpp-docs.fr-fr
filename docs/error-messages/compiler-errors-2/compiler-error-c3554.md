---
description: 'En savoir plus sur : erreur du compilateur C3554'
title: Erreur du compilateur C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: 39bc1a673af37d6b73941bb300d86df5f41a4704
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223176"
---
# <a name="compiler-error-c3554"></a>Erreur du compilateur C3554

impossible d'associer 'decltype' à un autre spécificateur de type

Vous ne pouvez pas qualifier le mot clé `decltype()` avec n’importe quel spécificateur de type. Par exemple, le fragment de code suivant génère l’erreur C3554.

```
int x;
unsigned decltype(x); // C3554
```
