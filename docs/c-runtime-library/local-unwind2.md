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
ms.openlocfilehash: 8ae5c3937c9dedc54f0a936b91963419d59f79cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535406"
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

## <a name="remarks"></a>Notes

Cette méthode est employé uniquement par l'environnement d'exécution. N'appelez pas la méthode dans votre code.

Quand cette méthode exécute des gestionnaires de terminaisons, elle part du niveau lexical actuel et parcourt les autres situés au-dessus jusqu'à atteindre celui indiqué par `stop`. Elle n'exécute pas les gestionnaires de terminaisons au niveau indiqué par `stop`.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)