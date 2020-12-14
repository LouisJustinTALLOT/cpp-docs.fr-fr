---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4092'
title: Avertissement du compilateur (niveau 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 70b2d94304863610ede64a30bcb1bb6d407f2e12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262008"
---
# <a name="compiler-warning-level-4-c4092"></a>Avertissement du compilateur (niveau 4) C4092

> sizeof retourne’unsigned long'

L’opérande de l' **`sizeof`** opérateur était très volumineux, ce qui a **`sizeof`** retourné un **`unsigned long`** . Cet avertissement se produit sous les extensions Microsoft ( [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) ). Sous compatibilité ANSI ( **`/Za`** ), le résultat est tronqué à la place.
