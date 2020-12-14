---
description: En savoir plus sur:/TLS
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: a21ef03210a65bb50899ba3907911272ac52b0db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229949"
---
# <a name="tls"></a>/TLS

Affiche la structure IMAGE_TLS_DIRECTORY à partir d’un fichier exécutable.

## <a name="remarks"></a>Notes

/TLS affiche les champs de la structure TLS, ainsi que les adresses des fonctions de rappel TLS.

Si un programme n’utilise pas le stockage local des threads, son image ne contient pas de structure TLS.  Pour plus d’informations, consultez [thread](../../cpp/thread.md) .

IMAGE_TLS_DIRECTORY est défini dans Winnt. h.

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
