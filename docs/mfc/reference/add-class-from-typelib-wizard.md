---
title: Ajout de classes d’une Typelib, Assistant | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a54948fd98b5a5445aa1fdfafcf0fcd015bbf08
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250378"
---
# <a name="add-class-from-typelib-wizard"></a>Assistant Ajout de classes d'une Typelib

Utilisez cet Assistant pour ajouter une classe MFC à partir d’une bibliothèque de types disponibles. L’Assistant crée une classe pour chaque interface que vous ajoutez à partir de la bibliothèque de types sélectionnée.

> [!WARNING]
> Dans Visual Studio 2017 version 15.9 cet Assistant code est déconseillé et sera supprimé dans une future version de Visual Studio. Cet Assistant est rarement utilisé. Prise en charge générale pour ATL et MFC n’est pas affectée par la suppression de cet Assistant. Si vous souhaitez partager vos commentaires sur cette utilisation déconseillée, veuillez remplir [cette enquête](https://www.surveymonkey.com/r/QDWKKCN). Vos commentaires est important pour nous.

- **Ajouter une classe à partir de**

   Spécifie l’emplacement de la bibliothèque de types à partir de laquelle la classe est créée.

   |Option|Description|
   |------------|-----------------|
   |**Registry**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Bibliothèques de types disponibles**.|
   |**Fichier**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Vous devez fournir l’emplacement du fichier dans **Emplacement**.|

- **Bibliothèques de types disponibles**

   Répertorie les bibliothèques de types actuellement inscrits dans le système. Sélectionnez une bibliothèque de types à partir de cette liste pour afficher ses interfaces dans les **Interfaces** liste.

   Consultez « À l’intérieur de Distributed COM : Type de bibliothèques et langue intégration » dans la bibliothèque MSDN pour plus d’informations sur l’inscription des bibliothèques de types.

- **Emplacement**

   Spécifie l’emplacement de la bibliothèque de types. Si vous cliquez sur **Fichier** sous **Ajouter une classe à partir de**, vous pouvez indiquer l’emplacement du fichier contenant la bibliothèque de types. Pour accéder à l’emplacement du fichier, cliquez sur le bouton de sélection (...).

- **Interfaces**

   Répertorie les interfaces dans la bibliothèque de types actuellement sélectionné dans le **bibliothèques de types disponibles** liste.

   |Bouton de transfert|Description|
   |---------------------|-----------------|
   |**>**|Ajoute l’interface actuellement sélectionnée à la liste **Interfaces**. Estompé si aucune interface n’est sélectionnée.|
   |**>>**|Ajoute toutes les interfaces dans la bibliothèque de types actuellement sélectionnée dans le **bibliothèques de types disponibles** liste.|
   |**\<**|Supprime la classe actuellement sélectionnée de la liste **Classes générées**. Estompé si aucune classe n’est sélectionnée dans le **classes générées** liste.|
   |**\<\<**|Supprime toutes les classes de la liste **Classes générées**. If estompé le **classes générées** liste est vide.|

- **Classes générées**

   Spécifie les noms de classe à générer à partir des interfaces ajoutées à l’aide du bouton **>** ou **>>**. Vous pouvez cliquer sur cette case pour sélectionner une classe et puis utilisez le haut ou bas pour faire défiler la liste, afficher chaque nom de classe dans le **classe** boîte et nom de fichier dans le **fichier** zone que l’Assistant génère lorsque vous Cliquez sur **Terminer**. Vous ne pouvez sélectionner qu’une seule classe à la fois dans cette zone.

   Pour supprimer une classe, sélectionnez-la dans cette liste et cliquez sur **<**. Vous n’avez pas besoin de sélectionner une classe dans la zone de classes générées pour supprimer toutes les classes ; en cliquant sur **<<**, vous supprimez toutes les classes dans le **classes générées** boîte.

- **Classe**

   Spécifie le nom de la classe sélectionnée dans la zone **Classes générées**. Cette classe est ajoutée par l’Assistant quand vous cliquez sur **Terminer**. Vous pouvez modifier le nom dans la **classe** boîte.

- **Fichier**

   Définit le nom du fichier d’en-tête de la nouvelle classe. Par défaut, ce nom est basé sur celui fourni dans **Classes générées**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

## <a name="see-also"></a>Voir aussi

[Classe MFC à partir d’une bibliothèque de types](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Clients Automation : utilisation des bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)

