---
title: _purecall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3095f6fee4458af5a12662886fdc6b9d81fe07f5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403064"
---
# <a name="purecall"></a>_purecall

Gestionnaire d’erreurs d’appel de fonction virtuelle pure par défaut. Le compilateur génère du code pour appeler cette fonction quand une fonction membre virtuelle pure est appelée.

## <a name="syntax"></a>Syntaxe

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Notes

Le **_purecall** fonction est un détail d’implémentation du compilateur Microsoft Visual C++ spécifiques à Microsoft. Cette fonction n’est pas destinée à être appelée directement par votre code, et ne s’accompagne d’aucune déclaration d’en-tête publique. Elle est documentée ici, car il s’agit d’une exportation publique de la bibliothèque Runtime C.

Un appel à une fonction virtuelle pure est une erreur, car elle n’a pas d’implémentation. Le compilateur génère du code pour appeler le **_purecall** fonction de gestionnaire d’erreur lorsqu’une fonction virtuelle pure est appelée. Par défaut, **_purecall** termine le programme. Avant de mettre fin, le **_purecall** fonction appelle un **_purecall_handler** fonctionner s’il a été défini pour le processus. Vous pouvez installer votre propre fonction de gestionnaire d’erreurs pour les appels de fonctions virtuelles pures, de façon à les intercepter à des fins de débogage ou de création de rapports. Pour utiliser votre propre gestionnaire d’erreurs, créez une fonction qui possède le **_purecall_handler** signature, puis utilisez [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) afin de faciliter le gestionnaire en cours.

## <a name="requirements"></a>Spécifications

Le **_purecall** fonction n’a pas une déclaration d’en-tête. Le **_purecall_handler** typedef est défini dans \<stdlib.h >.

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
