---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 751c212398f3d309b1d31d204291fe3a0503cf06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317261"
---
# <a name="tls"></a>/TLS

Affiche la structure IMAGE_TLS_DIRECTORY à partir d’un fichier exécutable.

## <a name="remarks"></a>Notes

/ TLS affiche les champs de la structure TLS ainsi que les adresses des fonctions de rappel TLS.

Si un programme n’utilise pas le stockage local des threads, son image ne contient pas une structure TLS.  Consultez [thread](../../cpp/thread.md) pour plus d’informations.

IMAGE_TLS_DIRECTORY est défini dans winnt.h.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
