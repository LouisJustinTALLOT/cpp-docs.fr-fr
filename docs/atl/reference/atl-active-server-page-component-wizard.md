---
title: Assistant Composant ASP ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ASP components, creating in ATL
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: 3e29d049c50f0410daf16b4bd1322676fd499fd2
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352672"
---
# <a name="atl-active-server-page-component-wizard"></a>Assistant Composant ASP ATL

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=vs-2017"

Cet Assistant insère un composant Active Server Pages (ASP) dans le projet. Le logiciel Microsoft Internet Information Services (IIS) utilise des composants ASP pour son architecture de développement de pages Web améliorée.

À l’aide de cet Assistant, vous pouvez spécifier le modèle de thread du composant et sa prise en charge d’agrégation. Vous pouvez également indiquer la prise en charge de l’interface d’informations d’erreur, des points de connexion et du marshaling à threads libres.

## <a name="remarks"></a>Notes

À partir de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrit ses composants COM sous **HKEY_CURRENT_USER** et non plus **HKEY_LOCAL_MACHINE**. Pour modifier ce comportement, définissez l’option **Inscrire le composant pour tous les utilisateurs** de l’Assistant ATL.

## <a name="names"></a>Noms

Spécifiez les noms de l’objet, de l’interface et des classes à ajouter à votre projet. À l’exception du champ **Nom court**, tous les autres peuvent être modifiés de manière indépendante. Si vous modifiez le contenu du champ **Nom court**, la modification se reflète dans les noms de tous les autres champs de cette page.

Si vous modifiez le nom **CoClasse** dans la section COM, la modification se reflète dans les champs **Type** et **ProgID**. Toutefois, le nom dans le champ **Interface** n’est pas modifié. Ce comportement de nommage est conçu pour rendre tous les noms faciles à identifier lors du développement de votre contrôle.

### <a name="c"></a>C++

Fournit des informations pour la classe C++ créée pour l’objet.

- **Nom court**

   Définit le nom racine de l’objet. Le nom que vous renseignez détermine les noms `Class` et **CoClasse**, les noms de **fichier .cpp** et de **fichier .h**, le nom du champ **Interface**, les noms du champ **Type** et le nom du champ **ProgID**, sauf si vous modifiez ces champs individuellement.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Classe**

   Définit le nom de la classe à créer. Ce nom est basé sur le nom que vous renseignez dans **Nom court**, précédé de « C », préfixe typique d’un nom de classe.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Avec attributs**

   Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL avec des attributs, cette option est sélectionnée et ne peut pas être modifiée. Autrement dit, vous pouvez uniquement ajouter des objets avec des attributs à un projet créé avec prise en charge d’attributs.

   Si vous sélectionnez cette option pour un projet ATL qui ne prend pas en charge les attributs, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge d’attributs au projet.

   Par défaut, pour les projets sans attributs, tous les objets que vous ajoutez après avoir défini cette option sont désignés comme ayant des attributs (la case est cochée). Vous pouvez effacer ce champ pour y ajouter un objet qui n’utilise pas d’attributs.

   Pour plus d’informations, consultez Paramètres de l' [application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [mécanismes de base des attributs](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>COM

Fournit des informations sur la fonctionnalité COM de l’objet.

- **Coclasse**

   Définit le nom de la classe du composant qui contient une liste d’interfaces prises en charge par l’objet. Si votre projet ou cet objet utilise des attributs, vous ne pouvez pas modifier cette option, car ATL n’inclut pas l’attribut **CoClasse**.

- **Type**

   Définit la description de l’objet qui s’affiche dans le registre pour la coclasse.

- **Interface**

   Définit l’interface que vous créez pour votre objet. Cette interface contient vos méthodes personnalisées.

- **ProgID**

   Définit le nom que les conteneurs peuvent utiliser au lieu du CLSID de l’objet.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
