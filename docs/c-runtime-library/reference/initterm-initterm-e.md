---
title: _initterm, _initterm_e
ms.date: 11/04/2016
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
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 65963e95507d4d6444ebcc9038b5b8cf797f9feb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331660"
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

Lorsque ces méthodes parcourent un tableau d’entrées de fonction, ils ignorent **NULL** entrées et continuer.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
