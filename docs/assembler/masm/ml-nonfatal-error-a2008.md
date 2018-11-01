---
title: Erreur ML non fatale A2008
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 7f85a3aabb7b1955cede912168dfc04618b8f2b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630371"
---
# <a name="ml-nonfatal-error-a2008"></a>Erreur ML non fatale A2008

**Erreur de syntaxe :**

Un jeton à l’emplacement actuel a provoqué une erreur de syntaxe.

Parmi les options suivantes peut-être se sont produites :

- Un préfixe de point a été ajouté à ou omis à partir d’une directive.

- Un mot réservé (tel que **C** ou **taille**) a été utilisé en tant qu’identificateur.

- Une instruction a été utilisée qui n’était pas disponible avec la sélection actuelle du processeur ou de coprocesseur.

- Un opérateur d’exécution de comparaison (tels que `==`) a été utilisé dans une instruction conditionnelle assembly au lieu d’un opérateur relationnel (tel que [EQ](../../assembler/masm/operator-eq.md)).

- Une instruction ou la directive a été donnée trop peu d’opérandes.

- Une directive obsolète a été utilisée.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>