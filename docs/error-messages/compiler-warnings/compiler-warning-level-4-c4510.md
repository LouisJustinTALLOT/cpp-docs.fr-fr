---
title: Avertissement du compilateur (niveau 4) C4510
description: Description et solution de l’avertissement du compilateur C4510.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: e4bb688266d9fe638978d2d3fa2666b83b3e6cc9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225252"
---
# <a name="compiler-warning-level-4-c4510"></a>Avertissement du compilateur (niveau 4) C4510

> '*classe*' : le constructeur par défaut n’a pas pu être généré

Le compilateur ne peut pas générer un constructeur par défaut pour la classe spécifiée, qui n’a pas de constructeurs définis par l’utilisateur. Impossible de créer les objets de ce type.

Il existe plusieurs situations qui empêchent le compilateur de générer un constructeur par défaut, y compris :

- **`const`** Membre de données.

- Membre de données qui est une référence.

Pour résoudre ce problème, créez un constructeur par défaut défini par l’utilisateur pour la classe qui initialise ces membres.
