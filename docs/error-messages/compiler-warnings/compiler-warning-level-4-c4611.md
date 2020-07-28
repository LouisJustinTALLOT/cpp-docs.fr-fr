---
title: Avertissement du compilateur (niveau 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 2ce261b36344126d541a9b453c88f7f8289ecba0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214332"
---
# <a name="compiler-warning-level-4-c4611"></a>Avertissement du compilateur (niveau 4) C4611

l’interaction entre’Function’et la destruction d’objet C++ n’est pas portable

Sur certaines plateformes, les fonctions qui incluent **`catch`** peuvent ne pas prendre en charge la sémantique d’objet C++ en dehors de l’étendue.

Pour éviter un comportement inattendu, évitez **`catch`** d’utiliser dans les fonctions qui ont des constructeurs et des destructeurs.

Cet avertissement n’est émis qu’une seule fois ; consultez [pragma warning](../../preprocessor/warning.md).
