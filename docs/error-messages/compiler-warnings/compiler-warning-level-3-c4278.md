---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4278'
title: Avertissement du compilateur (niveau 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: f7a53b54422e28f94096b91502651cb9355a244e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344144"
---
# <a name="compiler-warning-level-3-c4278"></a>Avertissement du compilateur (niveau 3) C4278

> '*identificateur*' : l’identificateur dans la bibliothèque de types'*TLB*'est déjà une macro ; utiliser le qualificateur’Rename'

Lors de l’utilisation de [#import](../../preprocessor/hash-import-directive-cpp.md), un identificateur dans la TypeLib que vous importez tente de déclarer un *identificateur* d’identificateur. Toutefois, il s’agit déjà d’un symbole valide.

Utilisez l' `#import` attribut **Rename** pour assigner un alias au symbole dans la bibliothèque de types.
