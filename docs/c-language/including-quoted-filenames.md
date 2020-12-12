---
description: 'En savoir plus sur : inclusion des noms de fichiers entre guillemets'
title: Intégration des noms de fichiers entre guillemets
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: b07d8dc04106a330644c30bffd1e8f36fc81fb6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137629"
---
# <a name="including-quoted-filenames"></a>Intégration des noms de fichiers entre guillemets

**ANSI 3.8.2** Prise en charge des noms entre guillemets pour les fichiers à inclure

Si vous spécifiez un chemin d’accès complet et non équivoque pour le fichier Include entre guillemets doubles (" "), le préprocesseur recherche uniquement dans le répertoire défini par ce chemin d’accès et ignore les répertoires standard.

Pour les fichiers Include spécifiés comme « spécification de chemin d’accès » [#include](../preprocessor/hash-include-directive-c-cpp.md), la recherche dans les répertoires commence par les répertoires du fichier parent, puis se poursuit par les répertoires de tous les fichiers grand-parents. Ainsi, la recherche commence par rapport au répertoire contenant le fichier source actuellement traitée. S'il n'existe aucun fichier grand-parent et que le fichier n'a pas été trouvé, la recherche se poursuit comme si le nom de fichier était placé entre crochets pointus.

## <a name="see-also"></a>Voir aussi

[Directives de prétraitement](../c-language/preprocessing-directives.md)
