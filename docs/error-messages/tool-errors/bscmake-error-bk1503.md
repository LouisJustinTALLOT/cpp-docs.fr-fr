---
title: Erreur BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: c81e955b912e03b322c0429097410fae74713b9d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031590"
---
# <a name="bscmake-error-bk1503"></a>Erreur BSCMAKE BK1503

ne peut pas écrire dans le fichier 'nom_fichier' [ : raison]

BSCMAKE combine les fichiers .sbr générés pendant la compilation dans une base de données de navigateur. Si la base de données de navigateur qui en résulte dépasse 64 Mo, ou si le nombre de fichiers d’entrée (.sbr) dépasse 4092, cette erreur est émise.

Si le problème est causé par des fichiers .sbr supérieur à 4092, vous devez réduire le nombre de fichiers d’entrée. À partir de Visual Studio, cela est possible en [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) votre projet entier, puis effectuez une revérification sur une base de fichier par fichier.

Si le problème est causé par un fichier .bsc supérieur à 64 Mo, ce qui réduit le nombre de fichiers .sbr en tant qu’entrée diminue la taille du fichier .bsc obtenu. En outre, la quantité d’informations de consultation peut être réduite en utilisant les /Em (exclure les symboles de développé de Macro), /El (exclure les Variables locales) et/es (exclure des fichiers système).

## <a name="see-also"></a>Voir aussi

[Options BSCMAKE](../../build/reference/bscmake-options.md)