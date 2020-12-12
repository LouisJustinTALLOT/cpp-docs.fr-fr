---
description: 'En savoir plus sur : erreur du compilateur de ressources RW2003'
title: 'Erreur RW2003 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: 545168aae1c483c358c55dfc90ce320aafac3ca2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259680"
---
# <a name="resource-compiler-error-rw2003"></a>Erreur RW2003 du compilateur de ressources 

Erreur de génération

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. **Erreur : le fichier de ressources du fichier bitmap n’est pas au format 3,00**

   Les images bitmap au format Windows version 2.x ne peuvent pas être utilisées dans les fichiers de ressources de version 3.x. La bitmap doit être redessinée ou convertie au format 3. x.

1. **Erreur : ancien DIB dans le nom de ressource. Passer par SDKPAINT**

   Une image bitmap indépendante du périphérique (DIB) de la ressource spécifiée n’est pas compatible avec le format Windows 3,0. La bitmap doit être redessinée ou convertie au format 3. x.

1. **Erreur : le nom de ressource du fichier de ressources n’est pas au format 3,00**

   Une icône ou un curseur dans la ressource spécifiée a utilisé un format d’une version précédente de Windows. L’icône ou le curseur doit être redessiné ou converti au format 3. x.

1. **Format d’en-tête DIB inconnu**

   L’en-tête de la bitmap n’est pas une structure BITMAPCOREHEADER ou BITMAPINFOHEADER.

1. **Impossible d’initialiser les informations de symboles**

   Cette erreur se produit uniquement dans Visual C++. La cause probable est que vous avez trop de fichiers ouverts ou que vous ne pouvez pas ouvrir ou écrire dans les fichiers de données nécessaires à Visual C++ importer les symboles dans votre script. Visual C++ tente de créer ces fichiers dans le répertoire spécifié par la variable d’environnement **tmp** ou le répertoire actuel si aucun n’est spécifié.

1. **Impossible d’enregistrer les informations de symbole**

   Cette erreur se produit uniquement dans Visual C++. La cause probable est que vous avez trop de fichiers ouverts ou que vous ne pouvez pas fermer ou écrire dans les fichiers de données nécessaires à Visual C++ importer les symboles dans votre script. Visual C++ tente d’utiliser ces fichiers dans le répertoire spécifié par la variable d’environnement **tmp** ou le répertoire actuel si aucun n’est spécifié.

1. **Le fichier de ressources du fichier bitmap n’est pas au format 2,03**

   Un bitmap utilise un format antérieur à la version 2.03. Le bitmap doit être converti ou recréé en utilisant le format de la version 3.00 ou ultérieure.

1. **Ressource trop volumineuse**

   Pour Windows 3,1, une ressource ne peut pas dépasser 65000 octets environ. Si votre ressource le fait, vous ne pourrez pas la compiler avec Visual C++ ou le compilateur de ressources en ligne de commande. Cette limite de taille ne s’applique pas aux curseurs, aux icônes, aux bitmaps et autres ressources basées sur un fichier.

1. **Le fichier de ressources n’est pas au format 3,00**

   Un curseur ou une icône a utilisé un format antérieur à la version 3,00. La ressource doit être convertie ou redessinée à l’aide du format pour la version 3,00 ou ultérieure.

1. **Impossible d’ouvrir le fichier temporaire**

   Le compilateur de ressources/Visual C++ n’a pas pu ouvrir un fichier temporaire. La cause probable est que vous n’avez pas d’autorisations d’écriture pour le répertoire ou que le répertoire n’existe pas. Le compilateur de ressources/Visual C++ essaie d’utiliser ces fichiers dans le répertoire spécifié par la variable d’environnement **TMP** ou le répertoire actuel si aucun n’est spécifié.
