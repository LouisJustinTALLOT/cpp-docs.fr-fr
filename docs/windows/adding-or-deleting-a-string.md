---
title: Ajout ou suppression d’une chaîne | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e15e29c99dba89ef29ba5b909c62f819bedf63f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858755"
---
# <a name="adding-or-deleting-a-string"></a>Ajout ou suppression d'une chaîne
Vous pouvez insérer rapidement de nouvelles entrées dans la table de chaînes à l’aide de l’éditeur de chaînes. Nouvelles chaînes sont placées à la fin de la table et sont fournies à l’identificateur disponible suivant. Vous pouvez modifier ensuite les propriétés ID, Value ou Caption dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) en fonction des besoins.  
  
 L’éditeur de chaînes permet de s’assurer que vous n’utilisez pas un ID qui est déjà en cours d’utilisation. Si vous sélectionnez un ID déjà en cours d’utilisation, l’éditeur de chaînes est vous notifier, puis attribuez un ID unique générique, par exemple IDS_STRING58113.  
  
### <a name="to-add-a-string-table-entry"></a>Pour ajouter une entrée de table de chaînes  
  
1.  Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Avec le bouton droit dans la table de chaînes et choisissez **nouvelle chaîne** dans le menu contextuel.  
  
3.  Dans le **chaîne** éditeur, sélectionnez une **ID** à partir de la liste déroulante de ID ou ID directement sur place.  
  
4.  Modifier la **valeur**, si nécessaire.  
  
5.  Tapez une entrée pour le **légende**.  
  
    > [!NOTE]
    >  Chaînes null ne sont pas autorisés dans les tables de chaînes Windows. Si vous créez une entrée dans la table de chaînes qui est une chaîne null, vous recevrez un message vous demandant de « Veuillez entrer une chaîne pour cette entrée de table. »  
  
### <a name="to-delete-a-string-table-entry"></a>Pour supprimer une entrée de table de chaînes  
  
1.  Sélectionnez l'entrée à supprimer.  
  
2.  Sur le **modifier** menu, cliquez sur **supprimer**.  
  
 \- ou -  
  
-   Avec le bouton droit de la chaîne que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.  
  
 \- ou -  
  
-   Appuyez sur la **supprimer** clé.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, et ceci manuellement, consultez [Procédure pas à pas : localisation des applications Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) et [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de chaînes](../windows/string-editor.md)   

