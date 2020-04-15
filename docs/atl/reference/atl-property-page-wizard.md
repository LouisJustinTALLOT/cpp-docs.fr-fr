---
title: Assistant Page de propriétés ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: eaf070d5a98a05dbe3102afac8317ffd59298ad2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321679"
---
# <a name="atl-property-page-wizard"></a>Assistant Page de propriétés ATL

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=vs-2017"

Cet Assistant [ajoute une page de propriétés dans un projet ATL](../../atl/reference/adding-an-atl-property-page.md) ou dans un projet MFC avec prise en charge d’ATL. Une page de propriétés ATL fournit une interface utilisateur pour définir les propriétés (ou pour appeler les méthodes) d’un ou plusieurs objets COM.

## <a name="remarks"></a>Notes

À partir de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrit ses composants COM sous **HKEY_CURRENT_USER** et non plus **HKEY_LOCAL_MACHINE**. Pour modifier ce comportement, définissez l’option **Inscrire le composant pour tous les utilisateurs** de l’Assistant ATL.

## <a name="names"></a>noms

Spécifiez les noms de l’objet, de l’interface et des classes à ajouter à votre projet. À l’exception du champ **Nom court**, tous les autres peuvent être modifiés de manière indépendante. Si vous modifiez le contenu du champ **Nom court**, la modification se reflète dans les noms de tous les autres champs de cette page. Si vous modifiez le nom **Coclasse** dans la section COM, la modification se reflète dans les champs **Type** et **ProgID**. Ce comportement de nommage est conçu pour rendre tous les noms faciles à identifier lors du développement de votre page de propriétés.

> [!NOTE]
> **Coclasse** est modifiable uniquement pour les projets non attribués. Si votre projet est attribué, vous ne pouvez pas modifier **Coclasse**.

### <a name="c"></a>C++

Fournit des informations pour la classe C++ créée pour implémenter l’objet.

|||
|-|-|
|Terme|Définition|
|**Nom court**|Définit le nom abrégé de l’objet. Le nom que vous renseignez détermine les noms de la classe et de la **Coclasse**, les noms de fichier (**.cpp** and **.h**), le nom du **Type** et le **ProgID**, sauf si vous modifiez ces champs individuellement.|
|**Fichier .h**|Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.<br /><br /> L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.|
|**Classe**|Définit le nom de la classe qui implémente l’objet. Ce nom est basé sur le nom que vous renseignez dans **Nom court**, précédé de « C », préfixe typique d’un nom de classe.|
|**Fichier .cpp**|Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.<br /><br /> L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.|
|**Avec attributs**|Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL attribué, cette option est sélectionnée et il est impossible de la modifier. Vous ne pouvez ajouter que des objets attribués à un projet créé avec une prise en charge d’attribut.<br /><br /> Vous pouvez ajouter un objet attribué uniquement à un projet ATL qui utilise des attributs. Si vous sélectionnez cette option pour un projet ATL qui ne prend pas en charge les attributs, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge d’attributs au projet.<br /><br /> Par défaut, tous les objets que vous ajoutez après avoir défini cette option sont désignés comme attribués (la case est cochée). Vous pouvez effacer ce champ pour y ajouter un objet qui n’utilise pas d’attributs.<br /><br /> Consultez [Paramètre d’application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [Mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.|

### <a name="com"></a>COM

Fournit des informations sur la fonctionnalité COM de l’objet.

- **CoClasse**

   Définit le nom de la classe du composant qui contient une liste d’interfaces prises en charge par l’objet.

   > [!NOTE]
   > Si vous créez votre projet à l’aide d’attributs, ou si vous indiquez sur cette page de l’Assistant que la page de propriétés utilise des attributs, vous ne pouvez pas modifier cette option car ATL n’inclut pas l’attribut `coclass`.

- **Type**

   Définit la description de l’objet qui s’affiche dans le registre

- **Progid**

   Définit le nom que les conteneurs peuvent utiliser au lieu du CLSID de l’objet.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Options, Assistant Page de propriétés ATL](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Chaînes, Assistant Page de propriétés ATL](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Exemple : implémentation d’une page de propriétés](../../atl/example-implementing-a-property-page.md)
