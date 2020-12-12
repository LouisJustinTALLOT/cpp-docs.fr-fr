---
description: 'En savoir plus sur : BSCMAKE Error BK1503'
title: Erreur BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: 0e789aa54241df5245f4c3a02a9307a97d51730c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322997"
---
# <a name="bscmake-error-bk1503"></a>Erreur BSCMAKE BK1503

Impossible d’écrire dans le fichier’nom_fichier' [ : raison]

BSCMAKE combine les fichiers. SBR générés pendant la compilation dans une seule base de données de navigateur. Si la base de données du navigateur qui en résulte dépasse 64 Mo ou si le nombre de fichiers d’entrée (. SBR) dépasse 4092, cette erreur est émise.

Si le problème est causé par plus de 4092 fichiers. SBR, vous devez réduire le nombre de fichiers d’entrée. Dans Visual Studio, cela peut être accompli en parsuit l’intégralité de votre projet, [puis la vérification](../../build/reference/fr-fr-create-dot-sbr-file.md) d’un fichier par fichier.

Si le problème est causé par un fichier. bsc supérieur à 64 Mo, le fait de réduire le nombre de fichiers. SBR en entrée réduit la taille du fichier. bsc résultant. En outre, la quantité d’informations de navigation peut être réduite par le biais de l’utilisation des/EM (exclure les symboles développés de macros),/El (exclure les variables locales) et/es (exclure les fichiers système).

## <a name="see-also"></a>Voir aussi

[Options BSCMAKE](../../build/reference/bscmake-options.md)
