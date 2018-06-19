---
title: _amsg_exit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _amsg_exit
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
- _amsg_exit
dev_langs:
- C++
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbb7f46bb4f3c942fd1c9e1a1d45c1ccf48739f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392794"
---
# <a name="amsgexit"></a>_amsg_exit

Émet un message d’erreur d’exécution spécifié, puis quitte votre application avec le code d’erreur 255.

## <a name="syntax"></a>Syntaxe

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Paramètres

*rterrnum*<br/>
Numéro d’identification d’un message d’erreur d’exécution défini par le système.

## <a name="remarks"></a>Notes

Cette fonction émet le message d’erreur d’exécution vers **stderr** (pour les applications de console) ou affiche le message dans une boîte de message (pour les applications Windows). En mode débogage, vous pouvez choisir d’appeler le débogueur avant de quitter.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_amsg_exit|internal.h|