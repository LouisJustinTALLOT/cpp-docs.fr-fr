---
description: 'En savoir plus sur : erreur irrécupérable C1107'
title: Erreur irrécupérable C1107
ms.date: 11/04/2016
f1_keywords:
- C1107
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
ms.openlocfilehash: c746bcf5f8bcb0247d8603b1734a3b1bdbc174f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144902"
---
# <a name="fatal-error-c1107"></a>Erreur irrécupérable C1107

Impossible de trouver l’assembly’fichier' : spécifiez le chemin de recherche de l’assembly en utilisant/AI ou en définissant la variable d’environnement LIBPATH

Un fichier de métadonnées a été passé à une directive de [#using](../../preprocessor/hash-using-directive-cpp.md) que le compilateur n’a pas pu localiser.

LIBPATH, qui est décrit dans la rubrique pour `#using` , et l’option du compilateur [/ai](../../build/reference/ai-specify-metadata-directories.md) vous permettent de spécifier les répertoires dans lesquels le compilateur recherchera les fichiers de métadonnées référencés.
