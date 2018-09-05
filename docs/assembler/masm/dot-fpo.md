---
title: . FPO | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be5e20716ff414eea3eddc8490e2a3f82adeb777
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687743"
---
# <a name="fpo"></a>.FPO

La barre d’outils. La directive FPO contrôle l’émission d’enregistrements de débogage à la section ou le segment de .debug$ F.

## <a name="syntax"></a>Syntaxe

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*,  *cbFrame*)

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