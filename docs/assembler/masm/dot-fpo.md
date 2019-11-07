---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3938d9194c35d567ea670e0b92a731193ccd2254
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703789"
---
# <a name="fpo-32-bit-masm"></a>. FPO (32-bit MASM)

La. La directive FPO contrôle l’émission d’enregistrements de débogage dans le segment ou la section. Debug $ F. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Paramètres

*cdwLocals*<br/>
Nombre de variables locales, valeur de bit 32 non signée.

*cdwParams*<br/>
Taille des paramètres dans les valeurs DWORD, valeur 16 bits non signée.

*cbProlog*<br/>
Nombre d’octets dans le code de prologue de la fonction, valeur 8 bits non signée.

*cbRegs*<br/>
Registres de nombres enregistrés.

*fUseBP*<br/>
Indique si le registre EBP a été alloué. 0 ou 1.

*cbFrame*<br/>
Indique le type de trame.  Pour plus d’informations, consultez [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
