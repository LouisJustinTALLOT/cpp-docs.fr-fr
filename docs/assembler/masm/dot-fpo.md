---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3bdb6af98aa71fef3d4af24091dc7463d917ce15
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915963"
---
# <a name="fpo"></a>.FPO

La. La directive FPO contrôle l’émission d’enregistrements de débogage dans le segment ou la section. Debug $ F.

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
Indique le type de trame.  Pour plus d’informations, consultez [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
