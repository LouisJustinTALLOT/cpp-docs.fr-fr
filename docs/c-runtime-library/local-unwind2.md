---
title: _local_unwind2
ms.date: 11/04/2016
apiname:
- _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: c62763ecbdd2c05e8cd7b6733ec1df4254362527
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743997"
---
# <a name="localunwind2"></a>_local_unwind2

Fonction CRT interne. Exécute tous les gestionnaires de terminaisons répertoriés dans la table d'étendue.

## <a name="syntax"></a>Syntaxe

```
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Paramètres

*xr*<br/>
[in] Enregistrement d’inscription associé à une table d’étendue.

*stop*<br/>
[in] Niveau lexical qui indique là où `_local_unwind2` doit s’arrêter.

## <a name="remarks"></a>Remarques

Cette méthode est employé uniquement par l'environnement d'exécution. N'appelez pas la méthode dans votre code.

Quand cette méthode exécute des gestionnaires de terminaisons, elle part du niveau lexical actuel et parcourt les autres situés au-dessus jusqu'à atteindre celui indiqué par `stop`. Elle n'exécute pas les gestionnaires de terminaisons au niveau indiqué par `stop`.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
