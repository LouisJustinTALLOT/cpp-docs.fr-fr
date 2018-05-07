---
title: Boîte de dialogue classe ajouter | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.addclass
dev_langs:
- C++
helpviewer_keywords:
- Add Class dialog box
ms.assetid: 916259b8-8e5f-4267-bd10-313483beba67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c4f108b30babcc30ffc5f2fc4c63fe764db2e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="add-class-dialog-box"></a>Ajouter une classe, boîte de dialogue
La boîte de dialogue **Ajouter une classe** contient des modèles qui vous permettent de :  
  
-   Ouvrir un Assistant de code correspondant, s’il est disponible. Pour plus d’informations, consultez [Ajout de fonctionnalités avec les Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
 \- ou -  
  
-   Créer automatiquement votre classe en ajoutant les fichiers appropriés et le code source à votre projet.  
  
 Vous pouvez accéder à la **ajouter une classe** boîte de dialogue à partir de la **projet** menu, **l’Explorateur de solutions**, ou [affichage de classes](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Quand vous essayez d’ajouter une classe qui ne convient pas à votre projet actuel, vous recevez un message d’erreur. Cliquez sur **OK** pour revenir à la boîte de dialogue **Ajouter une classe** .  
  
## <a name="add-class-templates"></a>Ajouter des modèles de classe  
 Il existe quatre catégories de modèles **Ajouter une classe** : .NET, ATL, MFC et Générique. Quand vous sélectionnez un modèle dans le volet **Modèles** , le texte décrivant votre sélection apparaît dans les volets **Catégories** et **Modèles** .  
  
### <a name="net"></a>.NET  
  
|Modèle|Assistant|  
|--------------|------------|  
|Service Web ASP.NET|Non disponible|  
|Classe Component (.NET)|Non disponible|  
|Classe Installer (.NET)|Non disponible|  
|Contrôle utilisateur (.NET)|Non disponible|  
|Windows Form (.NET)|Non disponible|  
  
### <a name="atl"></a>ATL  
  
|Modèle|Assistant|  
|--------------|------------|  
|Ajouter la prise en charge ATL à MFC|Non disponible|  
|Composant ASP ATL|[Assistant Composant ASP ATL](../atl/reference/atl-active-server-page-component-wizard.md)|  
|Contrôle ATL|[Assistant Contrôle ATL](../atl/reference/atl-control-wizard.md)|  
|Boîte de dialogue ATL|[Assistant Boîte de dialogue ATL](../atl/reference/atl-dialog-wizard.md)|  
|Composant COM+ 1.0 ATL|[Assistant Composant COM+ 1.0 ATL](../atl/reference/atl-com-plus-1-0-component-wizard.md)|  
|Consommateur OLEDB ATL|[Assistant Consommateur OLEDB ATL](../atl/reference/atl-ole-db-consumer-wizard.md)|  
|Fournisseur OLEDB ATL|[Assistant Fournisseur OLEDB ATL](../atl/reference/atl-ole-db-provider-wizard.md)|  
|Page de propriétés ATL|[Assistant Page de propriétés ATL](../atl/reference/atl-property-page-wizard.md)|  
|Objet simple ATL|[Assistant Objet simple ATL](../atl/reference/atl-simple-object-wizard.md)|  
|Fournisseur d’événements WMI|Assistant Fournisseur d’événements WMI|  
|Fournisseur d’instances WMI|Assistant Fournisseur d’instances WMI|  
  
### <a name="mfc"></a>MFC  
  
|Modèle|Assistant|  
|--------------|------------|  
|Classe MFC|[Ajouter une classe MFC, Assistant](../mfc/reference/mfc-add-class-wizard.md)|  
|Classe MFC à partir du contrôle ActiveX|[Assistant Ajout d’une classe à partir d’un contrôle ActiveX](../ide/add-class-from-activex-control-wizard.md)|  
|Classe MFC à partir d’une TypeLib|[Assistant Ajout de classes d’une Typelib](../mfc/reference/add-class-from-typelib-wizard.md)|  
|Consommateur ODBC MFC|[Consommateur ODBC MFC, Assistant](../mfc/reference/mfc-odbc-consumer-wizard.md)|  
  
### <a name="generic-classes"></a>Classes génériques  
  
|Modèle|Assistant|  
|--------------|------------|  
|Classe C++ générique|[Assistant Classe C++ générique](../ide/generic-cpp-class-wizard.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)   
 [Ajout d’une Variable membre](../ide/adding-a-member-variable-visual-cpp.md)   
 [Une fonction virtuelle de substitution](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigation dans la Structure de classe](../ide/navigating-the-class-structure-visual-cpp.md)