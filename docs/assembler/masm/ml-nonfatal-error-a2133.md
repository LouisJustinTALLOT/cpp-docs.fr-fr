---
title: Erreur ML non fatale A2133
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 9e13dd48c77b9574229023e3cfc4cc2f2221d153
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201208"
---
# <a name="ml-nonfatal-error-a2133"></a>Erreur ML non fatale A2133

**remplacé par INVOKE de valeur de Registre**

Un Registre a été passé en tant qu’argument à une procédure, mais le code généré par [INVOKE](../../assembler/masm/invoke.md) pour passer des autres arguments détruit le contenu du Registre.

Les registres AX, AL, AH, EAX, DX, DL, Diffie-Hellman et EDX peuvent être utilisés par l’assembleur pour effectuer la conversion de données.

Utiliser un autre registre.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>