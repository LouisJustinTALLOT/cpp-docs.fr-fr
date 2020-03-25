---
title: Avertissement du compilateur (niveau 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174230"
---
# <a name="compiler-warning-level-3-c4278"></a>Avertissement du compilateur (niveau 3) C4278

> '*identificateur*' : l’identificateur dans la bibliothèque de types'*TLB*'est déjà une macro ; utiliser le qualificateur’Rename'

Lors de l’utilisation de [#import](../../preprocessor/hash-import-directive-cpp.md), un identificateur dans la TypeLib que vous importez tente de déclarer un *identificateur*d’identificateur. Toutefois, il s’agit déjà d’un symbole valide.

Utilisez l’attribut **Renommer** `#import` pour assigner un alias au symbole dans la bibliothèque de types.
