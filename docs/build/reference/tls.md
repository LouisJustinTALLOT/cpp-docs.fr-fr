---
title: -TLS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f485a783dbe8b5fe9a49ed3100754115bf50b8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714652"
---
# <a name="tls"></a>/TLS

Affiche la structure IMAGE_TLS_DIRECTORY à partir d’un fichier exécutable.

## <a name="remarks"></a>Notes

/ TLS affiche les champs de la structure TLS ainsi que les adresses des fonctions de rappel TLS.

Si un programme n’utilise pas le stockage local des threads, son image ne contient pas une structure TLS.  Consultez [thread](../../cpp/thread.md) pour plus d’informations.

IMAGE_TLS_DIRECTORY est défini dans winnt.h.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)