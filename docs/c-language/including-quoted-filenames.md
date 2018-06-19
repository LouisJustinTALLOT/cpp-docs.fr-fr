---
title: Inclusion des noms de fichier entre guillemets | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80f6afbc503b52d1ef620050bf5592eb84e75fa9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383219"
---
# <a name="including-quoted-filenames"></a>Intégration des noms de fichiers entre guillemets
**ANSI 3.8.2** Prise en charge des noms entre guillemets pour les fichiers à inclure  
  
 Si vous spécifiez un chemin d’accès complet et non équivoque pour le fichier Include entre guillemets doubles (" "), le préprocesseur recherche uniquement dans le répertoire défini par ce chemin d’accès et ignore les répertoires standard.  
  
 Pour les fichiers Include spécifiés comme « spécification de chemin d’accès » [#include](../preprocessor/hash-include-directive-c-cpp.md), la recherche dans les répertoires commence par les répertoires du fichier parent, puis se poursuit par les répertoires de tous les fichiers grand-parents. Ainsi, la recherche commence par rapport au répertoire contenant le fichier source actuellement traitée. S'il n'existe aucun fichier grand-parent et que le fichier n'a pas été trouvé, la recherche se poursuit comme si le nom de fichier était placé entre crochets pointus.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives de prétraitement](../c-language/preprocessing-directives.md)