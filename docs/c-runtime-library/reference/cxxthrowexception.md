---
description: 'En savoir plus sur : _CxxThrowException'
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
ms.openlocfilehash: df4b1b30ba70ebf34bdb3cb4ae1c51a210f95a07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327032"
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

## <a name="requirements"></a>Spécifications

**Source :** Throw.cpp

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
