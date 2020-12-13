---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1181'
title: Erreur des outils Éditeur de liens LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: bda05d15597d6ed82b12145d380bbe40483d7623
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341683"
---
# <a name="linker-tools-error-lnk1181"></a>Erreur des outils Éditeur de liens LNK1181

Impossible d’ouvrir le fichier d’entrée’nom_fichier'

L’éditeur de liens n’a pas pu trouver `filename` , car il n’existe pas ou le chemin d’accès est introuvable.

Voici quelques causes courantes de l’erreur LNK1181 :

- `filename` est référencé comme dépendance supplémentaire sur la ligne de l’éditeur de liens, mais ce fichier n’existe pas.

- Une instruction **/LIBPATH** spécifiant que le répertoire contenant `filename` est manquant.

Pour résoudre les problèmes ci-dessus, assurez-vous que tous les fichiers référencés sur la ligne de l’éditeur de liens sont présents sur le système.  Vérifiez également qu’il existe une instruction **/LIBPATH** pour chaque répertoire contenant un fichier dépendant de l’éditeur de liens.

Pour plus d’informations, consultez [fichiers. lib en tant qu’entrée dans l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).

Une autre cause possible de LNK1181 est qu’un nom de fichier long avec des espaces incorporés n’a pas été placé entre guillemets.  Dans ce cas, l’éditeur de liens ne reconnaît qu’un nom de fichier jusqu’au premier espace, puis suppose une extension de fichier. obj.  La solution à cette situation consiste à placer le nom de fichier long (chemin plus nom de fichier) entre guillemets.

La compilation avec l’option [/p (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) peut entraîner la LNK1181, car cette option supprime la création de fichiers. obj.

## <a name="see-also"></a>Voir aussi

[/LIBPATH (autre chemin d’accès)](../../build/reference/libpath-additional-libpath.md)
