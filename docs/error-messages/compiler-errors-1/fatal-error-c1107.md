---
title: Erreur irrécupérable C1107
ms.date: 11/04/2016
f1_keywords:
- C1107
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
ms.openlocfilehash: 135e8da1b49eb1d86f6186e8683ced2f5152a3a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484810"
---
# <a name="fatal-error-c1107"></a>Erreur irrécupérable C1107

Impossible de trouver l’assembly 'fichier' : spécifiez le chemin de recherche des assemblys en utilisant /AI ou en définissant la variable d’environnement LIBPATH

Un fichier de métadonnées a été passé à un [#using](../../preprocessor/hash-using-directive-cpp.md) directive le compilateur n’a pas pu localiser.

LIBPATH, qui est décrite dans la rubrique pour `#using`et le [/AI](../../build/reference/ai-specify-metadata-directories.md) option du compilateur permettent de spécifier les répertoires dans lesquels le compilateur recherche les fichiers de métadonnées référencés.