---
title: Avertissement des outils Éditeur de liens LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194003"
---
# <a name="linker-tools-warning-lnk4070"></a>Avertissement des outils Éditeur de liens LNK4070

Directive/OUT : filename dans. EXP diffère du nom de fichier de sortie’nom_fichier'; directive ignorée

La `filename` spécifiée dans l’instruction [Name](../../build/reference/name-c-cpp.md) ou [Library](../../build/reference/library.md) lors de la création du fichier. exp est différente de la `filename` de sortie supposée par défaut ou spécifiée avec l’option [/out](../../build/reference/out-output-file-name.md) .

Cet avertissement s’affiche si vous modifiez le nom d’un fichier de sortie dans l’environnement de développement et si le fichier. def du projet n’a pas été mis à jour. Mettez à jour manuellement le fichier. def pour résoudre cet avertissement.

Un programme client qui utilise la DLL résultante peut rencontrer des problèmes.
