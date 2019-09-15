---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 2d577bfcf0584ef982ab43ff98674d0cfadd14ba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939696"
---
# <a name="_amsg_exit"></a>_amsg_exit

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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|_amsg_exit|internal.h|