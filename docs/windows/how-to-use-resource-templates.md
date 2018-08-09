---
title: 'Comment : utiliser des modèles de ressources | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- language-specific template files
- resource templates
- resources [Visual Studio], creating
- rct files
- templates, resource templates
- resources [Visual Studio], templates
- .rct files
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0a123c336df3f47550f8bb825a621eff53a8cb5
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015545"
---
# <a name="how-to-use-resource-templates"></a>comment : utiliser des modèles de ressources
Un modèle de ressource est une ressource personnalisée que vous avez enregistrée en tant que fichier .rct. Un modèle de ressource peut servir ensuite de point de départ pour la création d'autres ressources. Les modèles de ressources permettent de gagner du temps pour le développement de ressources ou de groupes de ressources supplémentaires qui partagent des fonctionnalités, par exemple les contrôles standard et autres éléments récurrents. Par exemple, vous pouvez être amené à inclure un bouton Aide et l'icône d'un logo d'entreprise dans plusieurs boîtes de dialogue. Pour y parvenir rapidement, créez un modèle de boîte de dialogue, puis personnalisez-le avec le logo et le bouton Aide.  
  
 Une fois que vous avez personnalisé le modèle de ressource, vous devez enregistrer vos modifications dans le dossier de modèles (ou n’importe quel emplacement spécifié dans le chemin d’accès include) afin que le nouveau modèle de ressource s’affiche sous son type de ressource dans le [boîte de dialogue Ajouter une ressource](../windows/add-resource-dialog-box.md). Vous pouvez ensuite utiliser le nouveau modèle de ressource aussi souvent que nécessaire.  
  
> [!NOTE]
>  Vous pouvez placer des fichiers modèles spécifiques aux langues dans les sous-répertoires du répertoire de modèles principal. Par exemple, vous pouvez placer les fichiers de modèle uniquement en anglais dans \\< répertoire des modèles de ressource\>\1033.  
  
### <a name="to-create-a-template-for-resources"></a>Pour créer un modèle pour des ressources  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur votre projet.  
  
2.  Dans le menu contextuel, choisissez **ajouter**, puis cliquez sur **ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles :** volet, choisissez **le fichier de modèle de ressource (.rct)**.  
  
4.  Fournissez un nom et un emplacement pour votre nouveau fichier .rct, puis cliquez sur **Open**.  
  
5.  Le nouveau fichier .rct est ajouté à votre projet et apparaît dans **l’Explorateur de solutions** sous le **ressources** dossier.  
  
     Vous pouvez désormais double-cliquez sur le fichier .rct pour l’ouvrir dans une fenêtre de document, puis ajouter des ressources (cliquez sur le fichier dans la fenêtre de document et choisissez **ajouter une ressource** dans le menu contextuel). Vous pouvez ensuite personnaliser ces ressources et enregistrer le fichier .rct.  
  
    > [!NOTE]
    >  Lorsque vous créez un fichier RCT, Visual Studio le recherche dans \Program Files\Microsoft Visual Studio 9.0\VC\VCResourceTemplates, dans \Program Files\Microsoft Visual Studio 9.0\VC\VCResourceTemplates\\*LCID* () par exemple 1033 pour l’anglais), *ou* n’importe où sur le [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md). Si vous préférez stocker vos fichiers RCT dans un autre dossier de fichiers, par exemple \Mes documents, il vous suffit d’ajouter ce dossier dans le chemin d’accès Include, et Visual Studio le trouvera sans difficultés.  
  
### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>Pour convertir un fichier .rc existant en fichier .rct  
  
1.  [Ouvrez le fichier .rc en tant que fichier autonome](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
2.  Sur le **fichier** menu, cliquez sur **enregistrer \< *votre nom de fichier*> en tant que**.  
  
3.  Spécifiez un emplacement et cliquez sur **OK**.  
  
### <a name="to-create-a-new-resource-from-a-template"></a>Pour créer une ressource à partir d'un modèle  
  
1.  Dans le [affichage des ressources](../windows/resource-view-window.md) volet, cliquez avec le bouton droit sur le fichier .rc et choisissez **ajouter une ressource** dans le menu contextuel.  
  
2.  Dans le **ajouter une ressource** boîte de dialogue, cliquez sur le signe plus (**+**) en regard d’une ressource pour développer le nœud de ressource et afficher tous les modèles disponibles pour cette ressource.  
  
3.  Double-cliquez sur le modèle à utiliser.  
  
4.  En fonction des besoins, modifiez la ressource ajoutée dans son éditeur de ressources.  
  
     L'éditeur de ressources fournit automatiquement un ID de ressource unique. Vous pouvez réviser le [propriétés de ressource](../windows/changing-the-properties-of-a-resource.md) en fonction des besoins.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)