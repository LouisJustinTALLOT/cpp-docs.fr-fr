---
description: 'En savoir plus sur : _purecall'
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: df52d7383685f3ce183562d8789b710fd7587acd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209449"
---
# <a name="_purecall"></a>_purecall

Gestionnaire d’erreurs d’appel de fonction virtuelle pure par défaut. Le compilateur génère du code pour appeler cette fonction quand une fonction membre virtuelle pure est appelée.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Notes

La fonction **_purecall** est un détail d’implémentation spécifique à Microsoft du compilateur Microsoft C++. Cette fonction n’est pas destinée à être appelée directement par votre code, et ne s’accompagne d’aucune déclaration d’en-tête publique. Elle est documentée ici, car il s’agit d’une exportation publique de la bibliothèque Runtime C.

Un appel à une fonction virtuelle pure est une erreur, car il n’a aucune implémentation. Le compilateur génère du code pour appeler la fonction de gestionnaire d’erreurs **_purecall** lorsqu’une fonction virtuelle pure est appelée. Par défaut, **_purecall** met fin au programme. Avant de se terminer, la fonction **_purecall** appelle une fonction **_purecall_handler** si une fonction a été définie pour le processus. Vous pouvez installer votre propre fonction de gestionnaire d’erreurs pour les appels de fonctions virtuelles pures, de façon à les intercepter à des fins de débogage ou de création de rapports. Pour utiliser votre propre gestionnaire d’erreurs, créez une fonction qui a la signature **_purecall_handler** , puis utilisez [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) pour en faire le gestionnaire actuel.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

La fonction **_purecall** n’a pas de déclaration d’en-tête. Le **_purecall_handler** typedef est défini dans \<stdlib.h> .

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
