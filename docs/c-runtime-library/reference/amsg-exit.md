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
ms.openlocfilehash: 31979a3181dc57644f1e6877277884e55cebf733
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170932"
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

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_amsg_exit|internal.h|
