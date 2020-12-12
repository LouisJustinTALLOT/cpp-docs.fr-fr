---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4070'
title: Avertissement des outils Éditeur de liens LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 188c8d88fa4fec332dad80fd5afee346f6099fca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210177"
---
# <a name="linker-tools-warning-lnk4070"></a>Avertissement des outils Éditeur de liens LNK4070

Directive/OUT : filename dans. EXP diffère du nom de fichier de sortie’nom_fichier'; directive ignorée

Le `filename` spécifié dans l’instruction [Name](../../build/reference/name-c-cpp.md) ou [Library](../../build/reference/library.md) lors de la création du fichier. exp est différent de la sortie `filename` supposée par défaut ou spécifiée avec l’option [/out](../../build/reference/out-output-file-name.md) .

Cet avertissement s’affiche si vous modifiez le nom d’un fichier de sortie dans l’environnement de développement et si le fichier. def du projet n’a pas été mis à jour. Mettez à jour manuellement le fichier. def pour résoudre cet avertissement.

Un programme client qui utilise la DLL résultante peut rencontrer des problèmes.
