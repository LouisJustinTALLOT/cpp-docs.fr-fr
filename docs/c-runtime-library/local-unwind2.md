---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: cbcc0c6177ba4cc449daf6a385a7cce53b8c1230
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745326"
---
# <a name="_local_unwind2"></a>_local_unwind2

Fonction CRT interne. Exécute tous les gestionnaires de terminaisons répertoriés dans la table d'étendue.

## <a name="syntax"></a>Syntaxe

```cpp
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
