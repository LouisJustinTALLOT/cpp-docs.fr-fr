---
description: 'En savoir plus sur : _initterm, _initterm_e'
title: _initterm, _initterm_e
ms.date: 11/04/2016
api_name:
- _initterm_e
- _initterm
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c9686504ae39f5aad1678430f4e4ad0054aabc36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296392"
---
# <a name="_initterm-_initterm_e"></a>_initterm, _initterm_e

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

Lorsque ces méthodes parcourent une table d’entrées de fonction, elles ignorent les entrées **null** et continuent.

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
