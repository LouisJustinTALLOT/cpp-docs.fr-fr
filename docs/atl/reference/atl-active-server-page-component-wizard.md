---
title: Assistant Composant ASP ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.overview
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: f020ed9b58f631bfff09fe54c70e36146eb03368
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249013"
---
# <a name="atl-active-server-page-component-wizard"></a>Assistant Composant ASP ATL

Cet Assistant insère dans le projet un composant Active Server Pages (ASP). Microsoft Internet Information Services (IIS) utilise des composants ASP dans le cadre de son architecture de développement de pages Web améliorée.

À l’aide de cet Assistant, vous pouvez spécifier que le composant de modèle de thread et sa prise en charge d’agrégation. Vous pouvez également indiquer la prise en charge de l’interface d’informations d’erreur, points de connexion et marshaling libre de threads.

> [!WARNING]
> Dans Visual Studio 2017 version 15.9, cet Assistant Code est déprécié et sera supprimé dans une version ultérieure de Visual Studio. Cet Assistant est rarement utilisé. La prise en charge générale d’ATL et MFC n’est pas affectée par la suppression de cet Assistant. Si vous souhaitez partager vos commentaires sur cette dépréciation, veuillez remplir [cette enquête](https://www.surveymonkey.com/r/QDWKKCN). Vos commentaires sont précieux pour nous.

## <a name="remarks"></a>Notes

À compter de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrira ses composants COM sous **HKEY_CURRENT_USER** au lieu de **HKEY_LOCAL_MACHINE**. Pour modifier ce comportement, définissez la **inscrire le composant pour tous les utilisateurs** option de l’Assistant ATL.

## <a name="names"></a>Noms

Spécifiez les noms de l’objet, interface et les classes à ajouter à votre projet. À l’exception de **nom court**, toutes les autres zones peuvent être modifiées indépendamment des autres. Si vous modifiez le texte de **nom court**, la modification est répercutée dans les noms de tous les autres zones de cette page.

Si vous modifiez le **coclasse** nom dans la section COM, la modification est répercutée dans le **Type** et **ProgID** cases, mais la **Interface** nom ne change pas. Ce comportement d’affectation de noms est conçu pour rendre tous les noms facilement identifiable pour vous lorsque vous développez votre contrôle.

### <a name="c"></a>C++

Fournit des informations pour la classe C++ créée pour l’objet.

- **Nom court**

   Définit le nom de la racine de l’objet. Le nom que vous fournissez détermine le `Class` et **coclasse** noms, le **fichier .cpp** et **fichier .h** noms, le **Interface**nom, le **Type** noms et le **ProgID**, sauf si vous modifiez ces champs individuellement.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’Assistant pas enregistrera à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Classe**

   Définit le nom de la classe à créer. Ce nom est basé sur le nom que vous fournissez dans **nom court**, précédé de « C », le préfixe classique pour un nom de classe.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur le nom que vous fournissez dans **nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Attribué**

   Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL avec attributs, cette option est sélectionnée et indisponible à modifier. Autrement dit, vous pouvez ajouter uniquement les objets attribués à un projet créé avec prise en charge de l’attribut.

   Si vous sélectionnez cette option pour un projet ATL qui n’a pas d’attribut prennent en charge, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge de l’attribut au projet.

   Par défaut pour les projets sans attributs, les objets que vous ajoutez après avoir défini cette option sont désignés avec attributs (la case à cocher est sélectionnée). Vous pouvez désactiver cette case pour ajouter un objet qui n’utilise pas d’attributs.

   Consultez [paramètres d’Application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.

### <a name="com"></a>COM

Fournit des informations sur les fonctionnalités COM pour l’objet.

- **Coclass**

   Définit le nom de la classe de composant qui contient une liste des interfaces prises en charge par l’objet. Si votre projet ou cet objet utilise des attributs, vous ne pouvez pas modifier cette option, car ATL n’inclut pas le **coclasse** attribut.

- **Type**

   Définit la description de l’objet qui apparaîtra dans le Registre pour la coclasse.

- **Interface**

   Définit l’interface que vous créez pour votre objet. Cette interface contient vos méthodes personnalisées.

- **ProgID**

   Définit le nom que les conteneurs peuvent utiliser au lieu du CLSID de l’objet.

## <a name="see-also"></a>Voir aussi

[Composant ASP ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
