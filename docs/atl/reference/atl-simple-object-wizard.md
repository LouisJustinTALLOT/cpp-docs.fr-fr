---
title: Assistant objet Simple ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 871e27b4a28299e6a3c96f7249f4636f412001d8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723617"
---
# <a name="atl-simple-object-wizard"></a>Assistant Objet simple ATL

Cet Assistant insère dans le projet un objet COM minimal. Utilisez cette page de l’Assistant pour spécifier les noms qui identifient les fichiers pour votre objet et ses fonctionnalités de COM et classe C++.

Utilisez le [Options](../../atl/reference/options-atl-simple-object-wizard.md) prennent en charge de la page de cet Assistant pour spécifier le modèle de thread de l’objet, son agrégation, et si elle prend en charge les interfaces doubles et l’automatisation. Vous pouvez également indiquer la prise en charge de l’interface d’informations d’erreur, points de connexion, prise en charge d’Internet Explorer et marshaling libre de threads.

## <a name="remarks"></a>Notes

À compter de Visual Studio 2008, le script d’inscription produit par cet Assistant inscrira ses composants COM sous **HKEY_CURRENT_USER** au lieu de **HKEY_LOCAL_MACHINE**. Pour modifier ce comportement, définissez la **inscrire le composant pour tous les utilisateurs** option de l’Assistant ATL.

## <a name="names"></a>Noms

Spécifiez les noms de l’objet, interface et les classes à ajouter à votre projet. À l’exception de **nom court**, toutes les autres zones peuvent être modifiées indépendamment des autres. Si vous modifiez le texte de **nom court**, la modification est répercutée dans les noms de tous les autres zones de cette page. Si vous modifiez le **coclasse** nom dans la section COM, la modification est répercutée dans le **Type** et **ProgID** cases, mais la **Interface** nom ne change pas. Ce comportement d’affectation de noms est conçu pour rendre tous les noms facilement identifiable pour vous lorsque vous développez votre contrôle.

> [!NOTE]
>  **Coclasse** est modifiable uniquement les projets sans attributs. Si votre projet avec attributs, vous ne pouvez pas modifier **coclasse**.

## <a name="c"></a>C++

Fournit des informations pour la classe C++ créée pour l’objet.

- **Nom court**

   Définit le nom abrégé pour l’objet. Le nom que vous fournissez détermine le `Class` et `Coclass` noms, le **fichier .cpp** et **fichier .h** noms, le **Interface** nom, le **Type** noms et le **ProgID**, sauf si vous modifiez ces champs individuellement.

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

   Vous pouvez ajouter un objet avec attributs qu’à un projet ATL qui utilise des attributs. Si vous sélectionnez cette option pour un projet ATL qui n’a pas d’attribut prennent en charge, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge de l’attribut au projet.

   Par défaut, les objets que vous ajoutez après avoir défini cette option sont désignés avec attributs (la case à cocher est sélectionnée). Vous pouvez désactiver cette case pour ajouter un objet qui n’utilise pas d’attributs.

   Consultez [paramètres d’Application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.

## <a name="com"></a>COM

Fournit des informations sur les fonctionnalités COM pour l’objet.

- **Coclasse**

   Définit le nom de la classe de composant qui contient une liste des interfaces prises en charge par l’objet.

   > [!NOTE]
   > Si vous créez votre projet à l’aide d’attributs, ou si vous indiquez sur cette page d’Assistant que l’objet utilise des attributs, vous ne pouvez pas modifier cette option, car ATL n’inclut pas le `coclass` attribut.

- **Type**

   Définit la description de l’objet qui apparaîtra dans le Registre

- **Interface**

   Définit l’interface que vous créez pour votre objet. Cette interface contient vos méthodes personnalisées.

- **ProgID**

   Définit le nom que les conteneurs peuvent utiliser au lieu du CLSID de l’objet.

## <a name="see-also"></a>Voir aussi

[Objet simple ATL](../../atl/reference/adding-an-atl-simple-object.md)

