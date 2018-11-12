---
title: Registres enregistrés des appelants-appelés
ms.date: 11/04/2016
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
ms.openlocfilehash: f34fbfff8e6c61b5d568c073f6b7da2a12e34535
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654699"
---
# <a name="callercallee-saved-registers"></a>Registres enregistrés des appelants/appelés

Les registres RAX, RCX, RDX, R8, R9, R10, R11 sont considérés comme volatile et doit être considéré comme détruit lors des appels de fonction (sauf si sinon sécurité-démontrables par analyse telles que de l’optimisation de l’ensemble du programme).

Les registres RBX, RBP, RDI, RSI, RSP, R12, R13, R14 et R15 sont considérés comme non volatile et doivent être enregistrés et restauré par une fonction qui les utilise.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)