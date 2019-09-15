---
title: _CxxThrowException
ms.date: 11/04/2016
api_name:
- _CxxThrowException
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: a5b614d25502ddd5a58aedcf2ec843b2b1ab9d47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942037"
---
# <a name="_cxxthrowexception"></a>_CxxThrowException

Crée l’enregistrement d’exception et appelle l’environnement d’exécution pour commencer le traitement de l’exception.

## <a name="syntax"></a>Syntaxe

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>Paramètres

*pExceptionObject*<br/>
Objet qui a généré l’exception.

*pThrowInfo*<br/>
Informations requises pour traiter l’exception.

## <a name="remarks"></a>Notes

Cette méthode est incluse dans un fichier de compilateur uniquement que le compilateur utilise pour traiter les exceptions. N’appelez pas la méthode directement à partir de votre code.

## <a name="requirements"></a>Configuration requise

**Code** Throw. cpp

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
