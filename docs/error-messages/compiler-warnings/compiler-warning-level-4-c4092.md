---
title: Avertissement du compilateur (niveau 4) C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 6786d692785dbca575d4b241b7b3e3d40575b686
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198547"
---
# <a name="compiler-warning-level-4-c4092"></a>Avertissement du compilateur (niveau 4) C4092

sizeof retourne’unsigned long'

L’opérande de l’opérateur `sizeof` était très volumineux, `sizeof` a donc retourné un entier **long**non signé. Cet avertissement se produit sous les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). Sous compatibilité ANSI (/za), le résultat est tronqué à la place.
