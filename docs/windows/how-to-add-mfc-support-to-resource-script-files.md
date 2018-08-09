---
title: 'Comment : ajouter la prise en charge MFC aux fichiers de Script de ressources | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 659c974fccec0e54dc42d6d1a5bdb019747f81ff
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647022"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Comment : ajouter de la prise en charge MFC aux fichiers de script de ressources
Normalement, lorsque vous générez une application MFC pour Windows à l’aide de la [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’Assistant génère un ensemble de base de fichiers (y compris un fichier de script (.rc) de ressources) qui contiennent les principales fonctionnalités de Microsoft Foundation classes (MFC). Toutefois, si vous modifiez un fichier .rc d’une application Windows qui n’est pas basée sur MFC, les fonctionnalités suivantes propres à l’infrastructure MFC ne sont pas disponibles :  
  
-   Assistants code MFC (précédemment appelé «[MFC ClassWizard](http://msdn.microsoft.com/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)»)  
  
-   Chaînes d'invite de menu  
  
-   Contenu des listes pour les contrôles zone de liste déroulante  
  
-   Hébergement de contrôles ActiveX  
  
 Toutefois, vous pouvez ajouter une prise en charge de MFC aux fichiers .rc existants qui en sont dépourvus.  
  
### <a name="to-add-mfc-support-to-rc-files"></a>Pour ajouter la prise en charge de MFC à des fichiers .rc  
  
1.  Ouvrez le fichier de script de ressources.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans [affichage des ressources](../windows/resource-view-window.md), mettez en surbrillance le dossier de ressources (par exemple, MFC.rc).  
  
3.  Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), définissez le **MFC Mode** propriété **True**.  
  
    > [!NOTE]
    >  Outre la définition de cet indicateur, le fichier .rc doit faire partie d'un projet MFC. Par exemple, définissant simplement **MFC Mode** à **True** sur un fichier .rc dans Win32 projet ne vous donne aucune des fonctionnalités MFC.  
  
## <a name="requirements"></a>Configuration requise  
 MFC  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)