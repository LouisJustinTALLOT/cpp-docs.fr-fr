---
title: Chaînes de modèles, de document MFC Assistant Ajout de classes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 247793199b1e865941659b970e4e59a688137a8e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712229"
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Chaînes du modèle de document, Assistant Ajouter une classe MFC
Cette page de l’Assistant est disponible uniquement pour les classes répondant aux critères suivants :  
  
-   Le projet MFC prend en charge l’architecture document/vue.  
  
-   La classe de base de la nouvelle classe est [CFormView](../../mfc/reference/cformview-class.md).  
  
-   La case à cocher **générer des ressources DocTemplate** est vérifiée sur le **noms** section de la [Assistant classe MFC](../../mfc/reference/mfc-add-class-wizard.md).  
  
 L’Assistant fournit des valeurs par défaut pour les valeurs suivantes faciliter la conception de la vue forms, gestion et la localisation. Étant donné que la plupart des chaînes de modèles de document sont visibles et employées par les utilisateurs du formulaire, elles sont traduites dans le **langue de ressource** indiqué dans le [Types d’applications](../../mfc/reference/application-type-mfc-application-wizard.md) page de l’Assistant Application MFC Lorsque le projet a été créé.  
  
> [!NOTE]
>  L’Assistant ne fournit pas de prise en charge l’impression automatique pour les classes dérivées à partir de `CFormView`.  
  
 Consultez [modèles de Document et le processus de création de Document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md) pour plus d’informations.  
  
## <a name="nonlocalized-strings"></a>Chaînes non localisées  
 S’applique aux applications qui créent des documents utilisateur. Les utilisateurs peuvent ouvrir et enregistrer des documents plus facilement si le type de document a une extension de fichier et un ID de type de fichier. Ces éléments ne sont pas localisés, car ils sont utilisés par le système plutôt que par l’utilisateur.  
  
- **Extension de fichier**

   Définit l’extension de fichier associée au type de document pour cette application de formulaires. Le fichier extension par défaut en fonction du nom de classe. Par exemple, si la nouvelle classe MFC est nommée `CWidget`, par défaut, l’extension de fichier est. WID. L’extension de fichier est utilisée dans les filtres de fichier et le **Open** et **enregistrer en tant que** boîtes de dialogue.  
  
   Si vous modifiez l’extension de fichier, la modification est répercutée dans le **nom de filtre** boîte.  
  
   > [!NOTE]
   > Si vous modifiez l’extension de fichier par défaut, n’incluez pas la période.  
  
- **ID de type de fichier**

   Définit l’étiquette pour votre type de document dans le Registre système.  
  
## <a name="localized-strings"></a>Chaînes localisées  
 Génère des chaînes associées avec les formulaires et les documents qui sont lus et utilisés par les utilisateurs de l’application, et donc les chaînes sont localisées.  
  
- **Nom de type de document**

   Identifie le type de document sous lequel un document de l’application peut être regroupé. Par défaut, il est basé sur le nom de la classe. Par exemple, si la nouvelle classe MFC est nommée **CWidget**, par défaut, le nom de type de document est Widget. Modification de la valeur par défaut ne modifie pas les options dans cette boîte de dialogue.  
  
- **Nom du filtre**

   Définit le nom que les utilisateurs peuvent indiquer pour rechercher les fichiers du type de fichier spécifié. Cette option est disponible à partir de la **types de fichiers** et **enregistrer en tant que type** options dans le Windows standard **Open** et **enregistrer en tant que** boîtes de dialogue. Par défaut, le nom est basé sur le nom du projet, ainsi que des fichiers, suivis de l’extension indiquée dans **Extension de fichier**. Par exemple, si votre projet est nommé Widget, et l’extension de fichier est .wid, le **nom de filtre** est Widget Files (*.wid) par défaut.  
  
- **Nom court de nouveau fichier**

   Définit le nom apparaissant dans le Windows standard **New** boîte de dialogue, si le projet comporte plusieurs modèles de document. Si votre application est un [serveur Automation](../../mfc/automation-servers.md), ce nom est utilisé en tant que le nom court de votre objet Automation. Par défaut, ce nom est basé sur le nom de classe.  
  
- **Nom de type de fichier long**

   Définit le nom de type de fichier dans le Registre système. Si votre application est un serveur Automation, ce nom est utilisé en tant que le nom long de votre objet Automation. Par défaut, ce nom est basé sur le nom de classe plus (+). Document. Par exemple, si le nom de classe est `CWidget`, le **type de fichier nom long** est Widget Document.  
  
- **Classe de document**

   Indique la classe de document du projet. Par défaut, cette classe est la classe de document de l’application principale, comme indiqué dans le [Classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant Application MFC. Vous pouvez sélectionner une autre classe de document dans la liste, si vous avez ajouté des autres classes de document dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [MFC Assistant Ajouter une classe](../../mfc/reference/mfc-add-class-wizard.md)   
 [Classe MFC](../../mfc/reference/adding-an-mfc-class.md)   
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)
