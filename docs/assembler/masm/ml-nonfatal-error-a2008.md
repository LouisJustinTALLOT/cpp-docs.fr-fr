---
description: 'En savoir plus sur : ML d’erreur non irrécupérable A2008'
title: Erreur ML non fatale A2008
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 4482304de3238954a01a0242bd84712012d691f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129296"
---
# <a name="ml-nonfatal-error-a2008"></a>Erreur ML non fatale A2008

**erreur de syntaxe :**

Un jeton à l’emplacement actuel a provoqué une erreur de syntaxe.

L’une des conditions suivantes peut se produire :

- Un préfixe point a été ajouté ou omis dans une directive.

- Un mot réservé (tel que **C** ou **Size**) a été utilisé en tant qu’identificateur.

- Une instruction qui n’était pas disponible avec le processeur ou la sélection de coprocesseur en cours a été utilisée.

- Un opérateur d’exécution de comparaison (tel que `==` ) a été utilisé dans une instruction d’assembly conditionnel au lieu d’un opérateur relationnel (tel que [EQ](operator-eq.md)).

- Une instruction ou une directive a donné un nombre insuffisant d’opérandes.

- Une directive obsolète a été utilisée.

## <a name="see-also"></a>Voir aussi

[Messages d'erreur ML](ml-error-messages.md)
