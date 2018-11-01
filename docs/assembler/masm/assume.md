---
title: ASSUME
ms.date: 08/30/2018
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 97a57cc8a1acccf70572ff963e496aa79fa3ab43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500566"
---
# <a name="assume"></a>ASSUME

Permet la vérification des erreurs pour les valeurs de registres.

## <a name="syntax"></a>Syntaxe

> Prenons *segregister*:*nom* [[, *segregister*:*nom*]]...<br/>
> Prenons *dataregister*:*type* [[, *dataregister*:*type*]]...<br/>
> Prenons *inscrire*: erreur [[, *inscrire*: erreur]]...<br/>
> Supposer que [[*inscrire*:]] rien [[, *inscrire*: rien]]...

## <a name="remarks"></a>Notes

Après un `ASSUME` est mis en effet, l’assembleur surveille les modifications apportées aux valeurs des registres donnés. **ERREUR** génère une erreur si le Registre est utilisé. **NOTHING** supprime inscrire la vérification des erreurs. Vous pouvez combiner différents genres d’hypothèses dans une seule instruction.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>