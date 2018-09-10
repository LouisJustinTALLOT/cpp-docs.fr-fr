---
title: _CxxThrowException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CxxThrowException
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
apitype: DLLExport
f1_keywords:
- CxxThrowException
- _CxxThrowException
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7adf4c285646e6a3f4706a9a56995f4440cc1e8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103813"
---
# <a name="cxxthrowexception"></a>_CxxThrowException

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

**Source :** Throw.cpp

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
