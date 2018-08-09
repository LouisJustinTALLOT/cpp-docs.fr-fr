---
title: 'Comment : importer et exporter des ressources | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e912e2aaae53fa0c7f9e506ce70128238bf15a78
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018414"
---
# <a name="how-to-import-and-export-resources"></a>Comment : importer et exporter des ressources
Vous pouvez importer des ressources graphiques (images bitmap, icônes, curseurs et barres d'outils), des fichiers HTML et des ressources personnalisées pour les utiliser dans Visual C++. Vous pouvez exporter les mêmes types de fichier depuis un projet Visual C++ vers des fichiers distincts utilisables en dehors de l'environnement de développement.  
  
> [!NOTE]
>  Les types de ressource tels que les accélérateurs, les boîtes de dialogue et les tables de chaînes ne peuvent pas être importés ou exportés, car il ne s'agit pas de types de fichier autonomes.  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Pour importer une ressource individuelle dans votre fichier de ressources actuel  
  
1.  Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur le nœud pour le script de ressources (* .rc) auquel vous souhaitez ajouter une ressource de fichier.  
  
2.  Cliquez sur **importation** dans le menu contextuel.  
  
3.  Recherchez et sélectionnez le nom de fichier de l'image bitmap (.bmp), de l'icône (.ico), du curseur (.cur), du fichier HTML (.htm), ou de tout autre fichier que vous souhaitez importer.  
  
4.  Cliquez sur **OK** pour ajouter la ressource au fichier sélectionné dans **ressource** vue.  
  
    > [!NOTE]
    >  Le processus d'importation fonctionne de la même façon, quel que soit le type de ressource que vous avez sélectionné. La ressource importée est automatiquement ajoutée au nœud approprié pour ce type de ressource.  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Pour exporter une image bitmap, une icône ou un curseur en tant que fichier distinct (pour une utilisation en dehors de Visual C++)  
  
1.  Dans **ressource** , cliquez sur la ressource que vous voulez exporter.  
  
2.  Cliquez sur **exporter** dans le menu contextuel.  
  
3.  Dans le **exporter la ressource** boîte de dialogue zone, acceptez le nom de fichier actuel ou tapez-en un nouveau.  
  
4.  Accédez au dossier où vous souhaitez enregistrer le fichier et cliquez sur **exporter**.  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)