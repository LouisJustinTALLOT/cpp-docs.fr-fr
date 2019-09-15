---
title: _purecall
ms.date: 11/04/2016
api_name:
- _purecall
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
ms.openlocfilehash: 5d62ec30731ce26c4683afc88474d4bddb63a697
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950167"
---
# <a name="_purecall"></a>_purecall

Gestionnaire d’erreurs d’appel de fonction virtuelle pure par défaut. Le compilateur génère du code pour appeler cette fonction quand une fonction membre virtuelle pure est appelée.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Notes

La fonction **_purecall** est un détail d’implémentation spécifique à Microsoft du compilateur C++ Microsoft. Cette fonction n’est pas destinée à être appelée directement par votre code, et ne s’accompagne d’aucune déclaration d’en-tête publique. Elle est documentée ici, car il s’agit d’une exportation publique de la bibliothèque Runtime C.

Un appel à une fonction virtuelle pure est une erreur, car elle n’a pas d’implémentation. Le compilateur génère du code pour appeler la fonction de gestionnaire d’erreurs **_purecall** lorsqu’une fonction virtuelle pure est appelée. Par défaut, **_purecall** met fin au programme. Avant de se terminer, la fonction **_purecall** appelle une fonction **_purecall_handler** si une fonction a été définie pour le processus. Vous pouvez installer votre propre fonction de gestionnaire d’erreurs pour les appels de fonctions virtuelles pures, de façon à les intercepter à des fins de débogage ou de création de rapports. Pour utiliser votre propre gestionnaire d’erreurs, créez une fonction qui a la signature **_purecall_handler** , puis utilisez [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) pour en faire le gestionnaire actuel.

## <a name="requirements"></a>Configuration requise

La fonction **_purecall** n’a pas de déclaration d’en-tête. Le typedef **_purecall_handler** est défini dans \<stdlib. h >.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
