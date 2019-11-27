---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 650c69be17c9271c343360edbb90f093841a1047
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398258"
---
# <a name="fpo-32-bit-masm"></a>. FPO (32-bit MASM)

**.** La directive FPO contrôle l’émission d’enregistrements de débogage dans le segment ou la section. Debug $ F. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. FPO** (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Paramètres

*cdwLocals*\
Nombre de variables locales, valeur de bit 32 non signée.

*cdwParams*\
Taille des paramètres dans les valeurs DWORD, valeur 16 bits non signée.

*cbProlog*\
Nombre d’octets dans le code de prologue de la fonction, valeur 8 bits non signée.

*cbRegs*\
Registres de nombres enregistrés.

*fUseBP*\
Indique si le registre EBP a été alloué. 0 ou 1.

*cbFrame*\
Indique le type de trame.  Pour plus d’informations, consultez [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
