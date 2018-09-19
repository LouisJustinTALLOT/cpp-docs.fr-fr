---
title: Erreur RW2003 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7b4341c4567e7a58135cc99a793f287f810043
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096780"
---
# <a name="resource-compiler-error-rw2003"></a>Erreur RW2003 du compilateur de ressources 

Erreur de génération

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. **Erreur : Le fichier de ressources du fichier Bitmap n’est pas au format 3.00**

     Les images bitmap au format Windows version 2.x ne peuvent pas être utilisées dans les fichiers de ressources de version 3.x. Devez les recréer ou les convertir au format 3.x.

1. **Erreur : Ancien DIB dans le nom de la ressource. Passez-la à SDKPAINT**

     Une Bitmap indépendante de périphérique (DIB) dans la ressource spécifiée n’est pas compatible avec le format Windows 3.0. L’image bitmap doit être redessiné ou converti au format 3.x.

1. **Erreur : Le nom de ressource du fichier de ressources n’est pas au format 3.00**

     Une icône ou un curseur dans la ressource spécifiée utilisait un format d’une version précédente de Windows. L’icône ou le curseur doit être redessiné ou converti au format 3.x.

1. **format d’en-tête DIB inconnu**

     L’en-tête de la bitmap n’est pas une structure BITMAPCOREHEADER ou BITMAPINFOHEADER.

1. **Impossible d’initialiser les informations de symboles**

     Cette erreur se produit uniquement dans Visual C++. La cause probable est que vous avez trop de fichiers ouverts ou vous ne pouvez pas ouvrir ou écrire dans les fichiers de données requis par Visual C++ importer les symboles dans votre script. Visual C++ tente de créer ces fichiers dans le répertoire spécifié par le **TMP** variable d’environnement ou le répertoire actuel si aucun n’est spécifié.

1. **Impossible d’enregistrer les informations de symboles**

     Cette erreur se produit uniquement dans Visual C++. La cause probable est que vous avez trop de fichiers ouverts ou vous ne pouvez pas fermer ou écrire dans les fichiers de données requis par Visual C++ importer les symboles dans votre script. Visual C++ tente d’utiliser ces fichiers dans le répertoire spécifié par le **TMP** variable d’environnement ou le répertoire actuel si aucun n’est spécifié.

1. **Fichier de ressources du fichier bitmap n’est pas au format 2.03**

     Un bitmap utilise un format antérieur à la version 2.03. Le bitmap doit être converti ou recréé en utilisant le format de la version 3.00 ou ultérieure.

1. **Ressource trop volumineuse**

     Pour Windows 3.1, une ressource ne peut pas dépasser 65 000 octets environ. Si votre ressource est le cas, vous ne pourrez pas compiler avec Visual C++ ou le compilateur de ressources en ligne de commande. Cette limite de taille ne s’applique pas aux curseurs, aux icônes, aux bitmaps et autres ressources basées sur un fichier.

9. **Fichier de ressources n’est pas au format 3.00**

     Une icône ou curseur utilisait un format antérieures à la version 3.00. La ressource doit être converti ou recréé en utilisant le format de la version 3.00 ou ultérieure.

10. **Impossible d’ouvrir le fichier temporaire**

     Le compilateur de ressources/Visual C++ n’a pas pu ouvrir un fichier temporaire. La cause probable est que vous n’avez pas d’autorisations en écriture pour le répertoire ou que le répertoire n’existe pas. Le compilateur de ressources/Visual C++ essaie d’utiliser ces fichiers dans le répertoire spécifié par la variable d’environnement **TMP** ou le répertoire actuel si aucun n’est spécifié.