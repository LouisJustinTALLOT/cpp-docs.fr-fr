---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4124'
title: Avertissement du compilateur (niveau 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 97fe65f8513f656d85059714ae598ffad9f7a49c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267389"
---
# <a name="compiler-warning-level-1-c4124"></a>Avertissement du compilateur (niveau 1) C4124

__fastcall avec la vérification de la pile est inefficace

Le **`__fastcall`** mot clé a été utilisé avec la vérification de la pile activée.

La **`__fastcall`** Convention génère du code plus rapide, mais la vérification de la pile entraîne un code plus lent. Lors de l’utilisation de, désactivez **`__fastcall`** la vérification de la pile avec le pragma **check_stack** ou/GS.

Cet avertissement est émis uniquement pour la première fonction déclarée dans ces conditions.
