---
title: Avertissement du compilateur (niveau 4) C4510
description: Description et solution de l’avertissement du compilateur C4510.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 05a6d0fe42d8247d3328506d8772b2fa77b5703c
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230380"
---
# <a name="compiler-warning-level-4-c4510"></a>Avertissement du compilateur (niveau 4) C4510

> '*classe*' : le constructeur par défaut n’a pas pu être généré

Le compilateur ne peut pas générer un constructeur par défaut pour la classe spécifiée, qui n’a pas de constructeurs définis par l’utilisateur. Impossible de créer les objets de ce type.

Il existe plusieurs situations qui empêchent le compilateur de générer un constructeur par défaut, y compris :

- Membre de données **const** .

- Membre de données qui est une référence.

Pour résoudre ce problème, créez un constructeur par défaut défini par l’utilisateur pour la classe qui initialise ces membres.
