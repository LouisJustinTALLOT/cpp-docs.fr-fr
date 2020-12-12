---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4684'
title: Avertissement du compilateur (niveau 1) C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: 036548912c55b2f21d9d62b00a06e49c0af252ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285212"
---
# <a name="compiler-warning-level-1-c4684"></a>Avertissement du compilateur (niveau 1) C4684

'Attribute' : WARNING !! l’attribut peut provoquer une génération de code non valide : utilisation avec précaution

Vous avez utilisé un attribut qui ne doit généralement pas être utilisé.

L’exemple suivant génère l’C4684 :

```cpp
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```
