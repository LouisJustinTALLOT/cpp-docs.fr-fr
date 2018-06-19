---
title: _initterm, _initterm_e | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _initterm_e
- _initterm
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
dev_langs:
- C++
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 470ad6cbf13efb170f61aa12f7859f2baa248c2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395833"
---
# <a name="initterm-initterme"></a>_initterm, _initterm_e

Méthodes internes qui parcourent un tableau de pointeurs de fonction et les initialisent.

Le premier pointeur est l’emplacement de départ dans le tableau et le deuxième pointeur est l’emplacement de fin.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>Valeur de retour

Code d’erreur différent de zéro si l’initialisation échoue et génère une erreur ; 0 si aucune erreur ne se produit.

## <a name="remarks"></a>Notes

Ces méthodes sont appelées uniquement en interne pendant l’initialisation d’un programme C++. N’appelez pas ces méthodes dans un programme.

Lorsque ces méthodes parcourez un tableau d’entrées de la fonction, ils ignorent **NULL** entrées et continuer.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
