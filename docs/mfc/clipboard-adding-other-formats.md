---
title: 'Presse-papiers : Ajout d’autres Formats | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67004ac43193d47720626da241a8030ba396abdf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932016"
---
# <a name="clipboard-adding-other-formats"></a>Presse-papiers : ajout d'autres formats
Cette rubrique explique comment développer la liste des formats pris en charge, en particulier pour la prise en charge OLE. La rubrique [Presse-papiers : copies et collage de données](../mfc/clipboard-copying-and-pasting-data.md) décrit l’implémentation minimale nécessaire pour prendre en charge le copier- coller à partir du Presse-papiers. Si c’est vous vous, les seuls formats placés dans le Presse-papiers sont **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**et éventuellement **CF_LINKSOURCE**. La plupart des applications nécessitent d’autres formats dans le Presse-papiers à ces trois.  
  
##  <a name="_core_registering_custom_formats"></a> Enregistrement de Formats personnalisés  
 Pour créer vos propres formats personnalisés, suivez la même procédure que vous utiliserez lors de l’inscription de n’importe quel format de Presse-papiers : passez le nom du format à la **RegisterClipboardFormat** la fonction et utiliser sa valeur de retour comme ID de format.  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> Ajout de Formats du Presse-papiers  
 Pour ajouter d’autres formats à ceux placés dans le Presse-papiers, vous devez substituer la `OnGetClipboardData` fonction dans la classe dérivée à partir de le `COleClientItem` ou `COleServerItem` (selon que les données à copier sont natives). Dans cette fonction, vous devez utiliser la procédure suivante.  
  
#### <a name="to-place-formats-on-the-clipboard"></a>Pour placer des formats dans le Presse-papiers  
  
1.  Créez un objet `COleDataSource`.  
  
2.  Passez cette source de données à une fonction qui ajoute vos formats de données natifs à la liste des formats pris en charge en appelant `COleDataSource::CacheGlobalData`.  
  
3.  Ajoutez des formats standard en appelant `COleDataSource::CacheGlobalData` pour chaque format standard que vous souhaitez prendre en charge.  
  
 Cette technique est utilisée dans le programme d’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md) (examinez le `OnGetClipboardData` fonction membre de la **CServerItem** classe). La seule différence dans cet exemple est que l’étape trois n’est pas implémentée, car HIERSVR prend en charge aucun autre format standard.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Transfert de données uniforme et les sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Glisser-déplacer OLE](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Presse-papiers : utilisation du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

