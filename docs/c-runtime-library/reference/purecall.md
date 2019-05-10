---
title: _purecall
ms.date: 11/04/2016
apiname:
- _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: df6dde91ccb952e66eb77c841b2b1ace12756b8c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446627"
---
# <a name="purecall"></a>_purecall

Gestionnaire d’erreurs d’appel de fonction virtuelle pure par défaut. Le compilateur génère du code pour appeler cette fonction quand une fonction membre virtuelle pure est appelée.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Notes

Le **_purecall** fonction est un détail d’implémentation spécifique à Microsoft de Microsoft C++ compilateur. Cette fonction n’est pas destinée à être appelée directement par votre code, et ne s’accompagne d’aucune déclaration d’en-tête publique. Elle est documentée ici, car il s’agit d’une exportation publique de la bibliothèque Runtime C.

Un appel à une fonction virtuelle pure est une erreur, car elle n’a pas d’implémentation. Le compilateur génère du code pour appeler le **_purecall** fonction de gestionnaire d’erreurs quand une fonction virtuelle pure est appelée. Par défaut, **_purecall** met fin au programme. Avant de terminer, le **_purecall** fonction appelle un **_purecall_handler** fonctionner s’il a été défini pour le processus. Vous pouvez installer votre propre fonction de gestionnaire d’erreurs pour les appels de fonctions virtuelles pures, de façon à les intercepter à des fins de débogage ou de création de rapports. Pour utiliser votre propre gestionnaire d’erreurs, créez une fonction qui a le **_purecall_handler** signature, puis utilisez [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) à faire le gestionnaire en cours.

## <a name="requirements"></a>Configuration requise

Le **_purecall** fonction n’a pas de déclaration d’en-tête. Le **_purecall_handler** typedef est défini dans \<stdlib.h >.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
