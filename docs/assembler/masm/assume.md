---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 4bf8f0c41e9ce3e296cf201efd4fd9be2033cbdb
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73702468"
---
# <a name="assume-32-bit-masm"></a>SUPPOSER (32-bit MASM)

Active la vérification des erreurs pour les valeurs de registre. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> SUPPOSons que *segregister*:*Name* [[, *segregister*:*Name*]]...<br/>
> SUPPOSons que *dataregister*:*type* [[, *dataregister*:*type*]]...<br/>
> SUPPOSER que *Register*: erreur [[, *Register*: Error]]...<br/>
> SUPPOSER que [[*Register*:]] Nothing [[, *Register*: Nothing]]...

## <a name="remarks"></a>Notes

Une fois qu’un `ASSUME` est mis en vigueur, l’assembleur surveille les modifications apportées aux valeurs des registres donnés. **Error** génère une erreur si le Registre est utilisé. **Rien ne** supprime la vérification des erreurs du Registre. Vous pouvez combiner différents genres d’hypothèses dans une instruction.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>