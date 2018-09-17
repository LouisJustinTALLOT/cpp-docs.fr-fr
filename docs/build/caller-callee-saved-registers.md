---
title: Registres enregistrés des appelants-| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8e877387dbb5b0be865e11017a3ac71a0c38faa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707653"
---
# <a name="callercallee-saved-registers"></a>Registres enregistrés des appelants/appelés

Les registres RAX, RCX, RDX, R8, R9, R10, R11 sont considérés comme volatile et doit être considéré comme détruit lors des appels de fonction (sauf si sinon sécurité-démontrables par analyse telles que de l’optimisation de l’ensemble du programme).

Les registres RBX, RBP, RDI, RSI, RSP, R12, R13, R14 et R15 sont considérés comme non volatile et doivent être enregistrés et restauré par une fonction qui les utilise.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)