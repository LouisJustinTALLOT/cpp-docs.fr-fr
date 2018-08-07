---
title: 'Comment : créer un fichier de Script de ressources | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed35392180d0531133413a54ca2190ed65519546
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570572"
---
# <a name="how-to-create-a-resource-script-file"></a>Comment : créer un fichier de script de ressources
> [!NOTE]
>  L’Éditeur de ressources n’est pas disponible dans les éditions Express.  
>   
>  Ces informations s’appliquent aux applications de bureau Windows. Les projets dans les langages .NET n’utilisent pas de fichiers de script de ressources. Pour plus d’informations, consultez [Fichiers de ressources](../windows/resource-files-visual-studio.md).  
  
### <a name="to-create-a-new-resource-script-rc-file"></a>Pour créer un fichier de script de ressources (.rc)  
  
1.  Placez le focus sur le dossier de votre projet dans **l’Explorateur de solutions**, par exemple, « MonProjet ».  
  
    > [!NOTE]
    >  Ne confondez pas le dossier du projet avec le dossier de solution dans l’Explorateur de solutions. Si vous placez le focus sur le **Solution** dossier, les choix disponibles dans le **ajouter un nouvel élément** boîte de dialogue (à l’étape 3) seront différent.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur le dossier **Visual C++** , puis choisissez **Fichier de ressources (.rc)** dans le volet droit.  
  
4.  Donnez un nom à votre fichier de script de ressources dans la zone de texte **Nom** , puis cliquez sur **Ouvrir**.  
  
 Vous pouvez maintenant [créer](../windows/how-to-create-a-resource.md) et ajouter de nouvelles ressources à votre fichier .rc.  
  
> [!NOTE]
>  Vous pouvez ajouter un script de ressources (fichier .rc) uniquement à un projet existant qui est chargé dans l’IDE de Visual Studio. Vous ne pouvez pas créer de fichier .rc autonome (en dehors du projet). Vous pouvez créer des[modèles de ressources](../windows/how-to-use-resource-templates.md) (fichiers .rct) à tout moment.


## <a name="requirements"></a>Configuration requise  
  
Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)
