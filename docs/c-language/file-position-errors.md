---
title: Erreurs de position de fichier
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: 3d581d86d6f08eee564feb6373a623512085ccca
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147800"
---
# <a name="file-position-errors"></a>Erreurs de position de fichier

**ANSI 4.9.9.1, 4.9.9.4** Valeur à laquelle la macro `errno` est définie par la fonction `fgetpos` ou `ftell` en cas d'échec

Lorsque `fgetpos` ou `ftell` échoue, `errno` prend comme valeur la constante de manifeste `EINVAL` si la position n’est pas valide ou `EBADF` si le numéro de fichier est incorrect. Les constantes sont définies dans ERRNO.H.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)
