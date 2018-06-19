---
title: Assistant Page de propriétés ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c5d863ef14aeddcd66f813449b514360f657a4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359780"
---
# <a name="atl-property-page-wizard"></a>Assistant Page de propriétés ATL
Cet Assistant [ajoute une page de propriétés dans un projet ATL](../../atl/reference/adding-an-atl-property-page.md) ou à un projet MFC avec prise en charge ATL. Une page de propriétés ATL fournit une interface utilisateur pour définir les propriétés (ou en appelant les méthodes) d’un ou plusieurs objets COM.  
  
## <a name="remarks"></a>Notes  
 À compter de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrira ses composants COM sous **HKEY_CURRENT_USER** au lieu de **HKEY_LOCAL_MACHINE**. Pour modifier ce comportement, définissez la **inscrire le composant pour tous les utilisateurs** option de l’Assistant ATL.  
  
## <a name="names"></a>Noms  
 Spécifiez les noms de l’objet, interface et les classes à ajouter à votre projet. À l’exception de **nom court**, toutes les autres cases peuvent être modifiés de manière indépendante. Si vous modifiez le texte de **nom court**, la modification est répercutée dans les noms de tous les autres zones de cette page. Si vous modifiez le **coclasse** nom de la section COM, la modification est répercutée dans le **Type** et **ProgID** cases. Ce comportement d’affectation de noms est conçu pour rendre tous les noms de facilement identifiables pour vous lorsque vous développez votre page de propriétés.  
  
> [!NOTE]
>  **Coclasse** ne peut être modifiée que pour les projets. Si votre projet est attribué, vous ne pouvez pas modifier **coclasse**.  
  
### <a name="c"></a>C++  
 Fournit des informations pour la classe C++ créée pour implémenter l’objet.  
  
|||  
|-|-|  
|Terme|Définition|  
|**Nom court**|Définit le nom abrégé de l’objet. Le nom que vous fournissez détermine la classe et **coclasse** des noms, le fichier (**.cpp** et **.h**), noms de la **Type** nom et la  **ProgID**, sauf si vous modifiez ces champs individuellement.|  
|**fichier .h**|Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’Assistant l’enregistrera pas à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.<br /><br /> L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.|  
|**Classe**|Définit le nom de la classe qui implémente l’objet. Ce nom est basé sur le nom que vous fournissez dans **nom court**, précédé de « C » (préfixe classique pour un nom de classe.|  
|**fichier .cpp**|Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. Le fichier n’est pas enregistré à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.<br /><br /> L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.|  
|**Attribué**|Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL avec attributs, cette option est sélectionnée, et non disponible pour modifier, autrement dit, vous pouvez ajouter attribué uniquement des objets à un projet créé avec prise en charge de l’attribut.<br /><br /> Vous pouvez ajouter un objet attribué qu’à un projet ATL qui utilise des attributs. Si vous sélectionnez cette option pour un projet ATL qui n’a pas d’attribut prennent en charge, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge de l’attribut pour le projet.<br /><br /> Par défaut, les objets que vous ajoutez après avoir défini cette option sont désignés avec attributs (la case à cocher est sélectionnée). Vous pouvez désactiver cette case pour ajouter un objet qui n’utilise pas d’attributs.<br /><br /> Consultez [paramètres de l’Application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.|  
  
### <a name="com"></a>COM  
 Fournit des informations sur les fonctionnalités COM pour l’objet.  
  
 **coclasse**  
 Définit le nom de la classe de composant qui contient la liste des interfaces prises en charge par l’objet.  
  
> [!NOTE]
>  Si vous créez votre projet à l’aide des attributs, ou si vous indiquez sur cette page de l’Assistant que la page de propriétés utilise des attributs, vous ne pouvez pas modifier cette option, car ATL n’inclut pas le `coclass` attribut.  
  
 **Type**  
 Définit la description de l’objet qui apparaîtra dans le Registre  
  
 **ProgID**  
 Définit le nom que les conteneurs peuvent utiliser à la place le CLSID de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Options, Assistant Page de propriétés ATL](../../atl/reference/options-atl-property-page-wizard.md)   
 [Chaînes, Assistant Page de propriétés ATL](../../atl/reference/strings-atl-property-page-wizard.md)   
 [Exemple : implémentation d’une page de propriétés](../../atl/example-implementing-a-property-page.md)

