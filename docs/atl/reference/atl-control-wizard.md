---
title: "Assistant contrôle ATL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9167153c2b827e1bc2597e830e9b3c82ee31b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="atl-control-wizard"></a>Assistant Contrôle ATL
Insère dans un projet ATL (ou un projet MFC avec prise en charge ATL) un contrôle ATL. Vous pouvez utiliser cet Assistant pour insérer l’un des trois types de contrôles :  
  
-   Contrôle standard  
  
-   Contrôles composites  
  
-   Contrôle DHTML  
  
 En outre, vous pouvez spécifier un contrôle minimal, suppression des interfaces à partir de la [Interfaces](../../atl/reference/interfaces-atl-control-wizard.md) liste, qui sont fournies en tant que valeurs par défaut pour les contrôles pour l’ouvrir dans la plupart des conteneurs. Vous pouvez définir les interfaces que vous souhaitez pris en charge pour le contrôle dans le **Interfaces** page de l’Assistant.  
  
## <a name="remarks"></a>Notes  
 Le script d’inscription produit par cet Assistant inscrira ses composants COM sous HKEY_CURRENT_USER au lieu de HKEY_LOCAL_MACHINE. Pour modifier ce comportement, définissez la **inscrire le composant pour tous les utilisateurs** option de l’Assistant ATL.  
  
## <a name="names"></a>Noms  
 Spécifiez les noms de l’objet, interface et les classes à ajouter à votre projet. À l’exception de **nom court**, toutes les autres cases sont modifiables indépendamment. Si vous modifiez le texte de **nom court**, la modification est répercutée dans les noms de tous les autres zones de cette page. Si vous modifiez le **coclasse** nom de la section COM, la modification est répercutée dans le **Type** zone, mais la **Interface** nom et **ProgID** faire ne modifiez pas. Ce comportement d’affectation de noms est conçu pour rendre tous les noms de facilement identifiables pour vous lorsque vous développez votre contrôle.  
  
> [!NOTE]
>  **Coclasse** est modifiable uniquement les contrôles sans attributs. Si votre projet est attribué, vous ne pouvez pas modifier **coclasse**.  
  
### <a name="c"></a>C++  
 Fournit des informations pour la classe C++ créée pour implémenter l’objet.  
  
 **Nom court**  
 Définit le nom abrégé de l’objet. Le nom que vous fournissez détermine la classe et **coclasse** des noms, le fichier (. CPP et. H) noms, le nom d’interface et le **Type** des noms, sauf si vous modifiez ces champs individuellement.  
  
 **Classe**  
 Définit le nom de la classe qui implémente l’objet. Ce nom est basé sur le nom que vous fournissez dans **nom court**, précédé de « C » (préfixe classique pour un nom de classe.  
  
 **fichier .h**  
 Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’Assistant l’enregistrera pas à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer**.  
  
 L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.  
  
 **fichier .cpp**  
 Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. Le fichier n’est pas enregistré à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.  
  
 L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.  
  
 **Attribué**  
 Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL avec attributs, cette option est sélectionnée et non disponible pour le modifier. Autrement dit, vous pouvez ajouter uniquement des objets attribués à un projet créé avec prise en charge de l’attribut.  
  
 Vous pouvez ajouter un objet attribué qu’à un projet ATL qui utilise des attributs. Si vous sélectionnez cette option pour un projet ATL qui n’a pas d’attribut prennent en charge, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge de l’attribut pour le projet.  
  
 Par défaut, les objets que vous ajoutez après avoir défini cette option sont désignés avec attributs (la case à cocher est sélectionnée). Vous pouvez désactiver cette case pour ajouter un objet qui n’utilise pas d’attributs.  
  
 Consultez [paramètres de l’Application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.  
  
### <a name="com"></a>COM  
 Fournit des informations sur les fonctionnalités COM pour l’objet.  
  
 **Coclasse**  
 Définit le nom de la classe de composant qui contient la liste des interfaces prises en charge par l’objet.  
  
> [!NOTE]
>  Si vous créez votre projet à l’aide des attributs, ou si vous indiquez sur cette page de l’Assistant que le contrôle utilise des attributs, vous ne pouvez pas modifier cette option, car ATL n’inclut pas le **coclasse** attribut.  
  
 **Interface**  
 Définit le nom de l’interface pour l’objet. Par défaut un nom d’interface est précédé de « I ».  
  
 **Type**  
 Définit la description de l’objet qui apparaîtra dans le Registre  
  
 **ProgID**  
 Définit le nom que les conteneurs peuvent utiliser à la place le CLSID de l’objet. Ce champ n’est pas rempli automatiquement. Si vous ne renseignez pas ce champ manuellement, il se peut que le contrôle ne peut pas être disponible à d’autres outils. Par exemple, les contrôles ActiveX générés sans un `ProgID` ne sont pas disponibles dans le **insérer un contrôle ActiveX** boîte de dialogue. Pour plus d’informations sur la boîte de dialogue, consultez [boîte de dialogue Insérer le contrôle ActiveX](../../windows/insert-activex-control-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle ATL](../../atl/reference/adding-an-atl-control.md)   
 [Ajout d’une fonctionnalité au contrôle Composite](../../atl/adding-functionality-to-the-composite-control.md)   
 [Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)

