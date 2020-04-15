---
title: Assistant Contrôle ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321697"
---
# <a name="atl-control-wizard"></a>Assistant Contrôle ATL

Insère dans un projet ATL (ou un projet MFC avec support ATL) un contrôle ATL. Vous pouvez utiliser cet assistant pour insérer l’un des trois types de contrôles:

- Contrôle standard

- Contrôle composite

- Contrôle DHTML

En outre, vous pouvez spécifier un contrôle minimal, en supprimant les interfaces de la liste [Interfaces,](../../atl/reference/interfaces-atl-control-wizard.md) qui sont fournis comme défauts pour les contrôles à ouvrir dans la plupart des conteneurs. Vous pouvez définir les interfaces que vous souhaitez prendre en charge pour le contrôle dans la page **Interfaces** de l’assistant.

## <a name="remarks"></a>Notes

Le script d’enregistrement produit par cet assistant enregistrera ses composants COM sous HKEY_CURRENT_USER au lieu de HKEY_LOCAL_MACHINE. Pour modifier ce comportement, définissez l’option **Inscrire le composant pour tous les utilisateurs** de l’Assistant ATL.

## <a name="names"></a>noms

Spécifiez les noms de l’objet, de l’interface et des classes à ajouter à votre projet. À **l’exception du nom court,** toutes les autres boîtes peuvent être modifiées indépendamment. Si vous modifiez le contenu du champ **Nom court**, la modification se reflète dans les noms de tous les autres champs de cette page. Si vous modifiez le nom **Coclass** dans la section COM, le changement est reflété dans la boîte **type,** mais le nom **interface** et **ProgID** ne changent pas. Ce comportement de nommage est conçu pour rendre tous les noms faciles à identifier lors du développement de votre contrôle.

> [!NOTE]
> **La coclasse** est modifiable uniquement sur les contrôles non attribués. Si votre projet est attribué, vous ne pouvez pas modifier **Coclasse**.

### <a name="c"></a>C++

Fournit des informations pour la classe C++ créée pour implémenter l’objet.

- **Nom court**

   Définit le nom abrégé de l’objet. Le nom que vous fournissez détermine les noms de classe et **de coclasse,** le fichier (. RPC et . H) noms, le nom de l’interface, et les noms **de type,** sauf si vous changez ces champs individuellement.

- **Classe**

   Définit le nom de la classe qui implémente l’objet. Ce nom est basé sur le nom que vous renseignez dans **Nom court**, précédé de « C », préfixe typique d’un nom de classe.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous sélectionnez un fichier existant, l’assistant ne l’enregistrera pas à l’emplacement sélectionné jusqu’à ce que vous cliquez sur **Finition**.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom court**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Avec attributs**

   Indique si l’objet utilise des attributs. Si vous ajoutez un objet à un projet ATL avec des attributs, cette option est sélectionnée et ne peut pas être modifiée. Autrement dit, vous pouvez uniquement ajouter des objets avec des attributs à un projet créé avec prise en charge d’attributs.

   Vous pouvez ajouter un objet attribué uniquement à un projet ATL qui utilise des attributs. Si vous sélectionnez cette option pour un projet ATL qui ne prend pas en charge les attributs, l’Assistant vous invite à spécifier si vous souhaitez ajouter la prise en charge d’attributs au projet.

   Par défaut, tous les objets que vous ajoutez après avoir défini cette option sont désignés comme attribués (la case est cochée). Vous pouvez effacer ce champ pour y ajouter un objet qui n’utilise pas d’attributs.

   Consultez [Paramètre d’application, Assistant Projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) et [Mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.

### <a name="com"></a>COM

Fournit des informations sur la fonctionnalité COM de l’objet.

- **CoClasse**

   Définit le nom de la classe du composant qui contient une liste d’interfaces prises en charge par l’objet.

   > [!NOTE]
   > Si vous créez votre projet à l’aide d’attributs, ou si vous indiquez sur cette page d’assistant que le contrôle utilise des attributs, vous ne pouvez pas modifier cette option parce qu’ATL n’inclut pas l’attribut **de coclasse.**

- **Interface**

   Définit le nom de l’interface pour l’objet. Par défaut, un nom d’interface est prépendi avec "je".

- **Type**

   Définit la description de l’objet qui s’affiche dans le registre

- **Progid**

   Définit le nom que les conteneurs peuvent utiliser au lieu du CLSID de l’objet. Ce champ n’est pas automatiquement peuplé. Si vous ne peuplez pas manuellement ce champ, le contrôle peut ne pas être disponible pour d’autres outils. Par exemple, les contrôles ActiveX `ProgID` qui sont générés sans a ne sont pas disponibles dans la boîte de dialogue **Insert ActiveX Control.** Pour plus d’informations sur cette boîte de dialogue, consultez [Insérer un contrôle ActiveX, boîte de dialogue](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Voir aussi

[Contrôle ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Ajout de fonctionnalités au contrôle composite](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Principes fondamentaux des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)
