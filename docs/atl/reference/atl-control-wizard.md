---
description: 'En savoir plus sur : Assistant contrôle ATL'
title: Assistant Contrôle ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: 3dd36e9ad2e14a87b86a56b8c035c4d4f8407430
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165431"
---
# <a name="atl-control-wizard"></a>Assistant Contrôle ATL

Insère dans un projet ATL (ou un projet MFC avec prise en charge ATL) un contrôle ATL. Vous pouvez utiliser cet Assistant pour insérer l’un des trois types de contrôles :

- Contrôle standard

- Contrôle composite

- Contrôle DHTML

En outre, vous pouvez spécifier un contrôle minimal, en supprimant les interfaces de la liste des [interfaces](../../atl/reference/interfaces-atl-control-wizard.md) , qui sont fournies comme valeurs par défaut pour que les contrôles s’ouvrent dans la plupart des conteneurs. Vous pouvez définir les interfaces que vous souhaitez voir prises en charge pour le contrôle dans la page **interfaces** de l’Assistant.

## <a name="remarks"></a>Notes

Le script d’inscription produit par cet Assistant inscrira ses composants COM sous HKEY_CURRENT_USER au lieu de HKEY_LOCAL_MACHINE. Pour modifier ce comportement, définissez l’option **Inscrire le composant pour tous les utilisateurs** de l’Assistant ATL.

## <a name="names"></a>Noms

Spécifiez les noms de l’objet, de l’interface et des classes à ajouter à votre projet. À l’exception de **Short Name**, toutes les autres zones peuvent être modifiées indépendamment. Si vous modifiez le contenu du champ **Nom court**, la modification se reflète dans les noms de tous les autres champs de cette page. Si vous modifiez le nom de **coclasse** dans la section com, la modification est reflétée dans la zone **type** , mais le nom d' **interface** et le **ProgID** ne changent pas. Ce comportement de nommage est conçu pour rendre tous les noms faciles à identifier lors du développement de votre contrôle.

> [!NOTE]
> La **coclasse** est modifiable uniquement sur les contrôles non attributs. Si votre projet est attribué, vous ne pouvez pas modifier **Coclasse**.

### <a name="c"></a>C++

Fournit des informations pour la classe C++ créée pour implémenter l’objet.

- **Nom court**

   Définit le nom abrégé de l’objet. Le nom que vous fournissez détermine les noms de classe et de **coclasse** , le fichier (. CPP et. H), le nom de l’interface et les noms de **type** , sauf si vous modifiez ces champs individuellement.

- **Classe**

   Définit le nom de la classe qui implémente l’objet. Ce nom est basé sur le nom que vous renseignez dans **Nom court**, précédé de « C », préfixe typique d’un nom de classe.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’Assistant ne l’enregistre pas à l’emplacement sélectionné tant que vous n’avez pas cliqué sur **Terminer**.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Avec attributs**

   Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL avec des attributs, cette option est sélectionnée et ne peut pas être modifiée. Autrement dit, vous pouvez uniquement ajouter des objets avec des attributs à un projet créé avec prise en charge d’attributs.

   Vous pouvez ajouter un objet attribué uniquement à un projet ATL qui utilise des attributs. Si vous sélectionnez cette option pour un projet ATL qui ne prend pas en charge les attributs, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge d’attributs au projet.

   Par défaut, tous les objets que vous ajoutez après avoir défini cette option sont désignés comme attribués (la case est cochée). Vous pouvez effacer ce champ pour y ajouter un objet qui n’utilise pas d’attributs.

   Pour plus d’informations, consultez Paramètres de l' [application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [mécanismes de base des attributs](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>COM

Fournit des informations sur la fonctionnalité COM de l’objet.

- **Coclasse**

   Définit le nom de la classe du composant qui contient une liste d’interfaces prises en charge par l’objet.

   > [!NOTE]
   > Si vous créez votre projet à l’aide d’attributs ou si vous indiquez sur cette page de l’Assistant que le contrôle utilise des attributs, vous ne pouvez pas modifier cette option, car ATL n’inclut pas l’attribut **coclass** .

- **Interface**

   Définit le nom de l’interface pour l’objet. Par défaut, un nom d’interface est ajouté avec « I ».

- **Type**

   Définit la description de l’objet qui s’affiche dans le registre

- **ProgID**

   Définit le nom que les conteneurs peuvent utiliser au lieu du CLSID de l’objet. Ce champ n’est pas rempli automatiquement. Si vous ne remplissez pas ce champ manuellement, le contrôle peut ne pas être disponible pour d’autres outils. Par exemple, les contrôles ActiveX qui sont générés sans ne `ProgID` sont pas disponibles dans la boîte de dialogue **Insérer un contrôle ActiveX** . Pour plus d’informations sur la boîte de dialogue, consultez [Insérer des contrôles ActiveX](../../windows/adding-editing-or-deleting-controls.md#insert-activex-controls).

## <a name="see-also"></a>Voir aussi

[Contrôle ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Ajout de fonctionnalités au contrôle composite](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)
