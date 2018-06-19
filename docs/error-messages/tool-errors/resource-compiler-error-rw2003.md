---
title: Erreur RW2003 du compilateur de ressources | Documents Microsoft
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
ms.openlocfilehash: 10cbd42d976566b1bd8388b8a42429cd7e57639d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323509"
---
# <a name="resource-compiler-error-rw2003"></a>Erreur RW2003 du compilateur de ressources 
Erreur de génération  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  **Erreur : Le fichier de ressources du fichier Bitmap n’est pas au format 3.00**  
  
     Les images bitmap au format Windows version 2.x ne peuvent pas être utilisées dans les fichiers de ressources de version 3.x. L’image bitmap doit être redessiné ou convertir au format 3.x.  
  
2.  **Erreur : Ancien DIB dans le nom de la ressource. Passez-la à SDKPAINT**  
  
     Une Bitmap indépendante de périphérique (DIB) de la ressource spécifiée n’est pas compatible avec le format Windows 3.0. L’image bitmap doit être redessiné ou converti au format 3.x.  
  
3.  **Erreur : Le nom de ressource du fichier de ressources n’est pas au format 3.00**  
  
     Une icône ou un curseur de la ressource spécifiée utilise un format d’une version antérieure de Windows. L’icône ou le curseur doit être redessiné ou converti au format 3.x.  
  
4.  **format d’en-tête DIB inconnu**  
  
     L’en-tête de la bitmap n’est pas une structure BITMAPCOREHEADER ou BITMAPINFOHEADER.  
  
5.  **Impossible d’initialiser les informations de symboles**  
  
     Cette erreur se produit uniquement dans Visual C++. La cause probable est que vous avez trop de fichiers ouverts ou Impossible d’ouvrir ou d’écrire dans les fichiers de données requis par Visual C++ importer les symboles dans votre script. Visual C++ tente de créer ces fichiers dans le répertoire spécifié par le **TMP** variable d’environnement ou le répertoire actif si none est spécifié.  
  
6.  **Impossible d’enregistrer les informations de symboles**  
  
     Cette erreur se produit uniquement dans Visual C++. La cause probable est que vous avez trop de fichiers ouverts ou Impossible de fermer ou d’écrire dans les fichiers de données requis par Visual C++ importer les symboles dans votre script. Visual C++ tente d’utiliser ces fichiers dans le répertoire spécifié par le **TMP** variable d’environnement ou le répertoire actif si none est spécifié.  
  
7.  **Fichier de ressources du fichier bitmap n’est pas au format 2.03**  
  
     Un bitmap utilise un format antérieur à la version 2.03. Le bitmap doit être converti ou recréé en utilisant le format de la version 3.00 ou ultérieure.  
  
8.  **Ressource trop volumineuse**  
  
     Pour Windows 3.1 une ressource ne peut pas dépasser 65 000 octets environ. Si votre ressource est le cas, vous ne pourrez pas compiler avec Visual C++ ou le compilateur de ressources en ligne de commande. Cette limite de taille ne s’applique pas aux curseurs, aux icônes, aux bitmaps et autres ressources basées sur un fichier.  
  
9. **Fichier de ressources n’est pas au format 3.00**  
  
     Une icône ou curseur utilise un format antérieure à la version 3.00. La ressource doit être converti ou recréé en utilisant le format de la version 3.00 ou ultérieure.  
  
10. **Impossible d’ouvrir le fichier temporaire**  
  
     Le compilateur de ressources/Visual C++ n’a pas pu ouvrir un fichier temporaire. La cause probable est que vous n’avez pas d’accessible en écriture pour le répertoire ou que le répertoire n’existe pas. Le compilateur de ressources/Visual C++ essaie d’utiliser ces fichiers dans le répertoire spécifié par la variable d’environnement **TMP** ou le répertoire actuel si aucun n’est spécifié.