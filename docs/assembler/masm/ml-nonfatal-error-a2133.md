---
description: 'En savoir plus sur : ML d’erreur non irrécupérable A2133'
title: Erreur ML non fatale A2133
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 11a2d27a00ac4e1d8b669ec7a7d4fe523476b5c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128464"
---
# <a name="ml-nonfatal-error-a2133"></a>Erreur ML non fatale A2133

**inscrire la valeur remplacée par INVOKE**

Un registre a été passé comme argument à une procédure, mais le code généré par [Invoke](invoke.md) pour passer d’autres arguments a détruit le contenu du Registre.

Les registres AX, AL, AH, EAX, DX, DL, DH et EDX peuvent être utilisés par l’assembleur pour effectuer la conversion des données.

Utilisez un autre registre.

## <a name="see-also"></a>Voir aussi

[Messages d'erreur ML](ml-error-messages.md)
