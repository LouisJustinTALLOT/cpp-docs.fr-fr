---
description: 'En savoir plus sur : _local_unwind2'
title: _local_unwind2
ms.date: 1/14/2021
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: cb137547c44eb6d6516086a06109a9339247699c
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243058"
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

## <a name="remarks"></a>Remarques

Cette méthode est employé uniquement par l'environnement d'exécution. N'appelez pas la méthode dans votre code.

Quand cette méthode exécute des gestionnaires de terminaisons, elle part du niveau lexical actuel et parcourt les autres situés au-dessus jusqu'à atteindre celui indiqué par `stop`. Elle n'exécute pas les gestionnaires de terminaisons au niveau indiqué par `stop`.

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
