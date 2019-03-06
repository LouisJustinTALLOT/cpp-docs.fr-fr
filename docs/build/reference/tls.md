---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 1760e94046a950f67d3c3fd7ef13aa40ca7de47a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417786"
---
# <a name="tls"></a>/TLS

Affiche la structure IMAGE_TLS_DIRECTORY à partir d’un fichier exécutable.

## <a name="remarks"></a>Notes

/ TLS affiche les champs de la structure TLS ainsi que les adresses des fonctions de rappel TLS.

Si un programme n’utilise pas le stockage local des threads, son image ne contient pas une structure TLS.  Consultez [thread](../../cpp/thread.md) pour plus d’informations.

IMAGE_TLS_DIRECTORY est défini dans winnt.h.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)
