---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4234'
title: Avertissement du compilateur (niveau 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 98a3f5bc2c13dec3822342a669f7c9de3dc452fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334904"
---
# <a name="compiler-warning-level-4-c4234"></a>Avertissement du compilateur (niveau 4) C4234

extension non standard utilisée : mot clé’keyword’réservé pour un usage ultérieur

Le compilateur n’implémente pas encore le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4234 dans un numéro d’avertissement de niveau 4,

```cpp
#pragma warning(2:4234)
```

dans votre fichier de code source.
