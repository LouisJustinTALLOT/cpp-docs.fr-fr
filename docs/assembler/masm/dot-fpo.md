---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 83d6e81ea7dd35038f27f2721f3cc41fe49ef1bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204056"
---
# <a name="fpo"></a>.FPO

La barre d’outils. La directive FPO contrôle l’émission d’enregistrements de débogage à la section ou le segment de .debug$ F.

## <a name="syntax"></a>Syntaxe

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Paramètres

*cdwLocals*<br/>
Nombre de variables locales, une valeur 32 bits non signé.

*cdwParams*<br/>
Taille des paramètres dans DWORDS, une valeur 16 bits non signé.

*cbProlog*<br/>
Nombre d’octets dans le code de prologue de fonction, une valeur non signé 8 bits.

*cbRegs*<br/>
Numéro de registres enregistrés.

*fUseBP*<br/>
Indique si le registre EBP a été alloué. 0 ou 1.

*cbFrame*<br/>
Indique le type de trame.  Consultez [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>