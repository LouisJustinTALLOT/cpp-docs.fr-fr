---
title: Assistant Ajout d’une classe à partir d’un contrôle ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.axcontrol
dev_langs:
- C++
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45615762bc84f30c9c4caee568ef99c244cc99cf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391122"
---
# <a name="add-class-from-activex-control-wizard"></a>Assistant Ajout d’une classe à partir d’un contrôle ActiveX

Utilisez cet Assistant pour ajouter une classe MFC à partir d’un contrôle ActiveX disponible. L’Assistant crée une classe pour chaque interface que vous ajoutez à partir du contrôle ActiveX sélectionné.

- **Ajouter une classe à partir de**

   Spécifie l’emplacement de la bibliothèque de types à partir de laquelle la classe est créée.

   |Option|Description|
   |------------|-----------------|
   |**Registry**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Contrôles ActiveX disponibles**.|
   |**Fichier**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Vous devez indiquer l’emplacement du fichier dans **Emplacement**.|

- **Contrôles ActiveX disponibles**

   Spécifie les contrôles ActiveX actuellement inscrits dans le système. Sélectionnez un contrôle ActiveX dans cette liste pour afficher ses interfaces dans la liste **Interfaces**. Pour plus d’informations sur l’inscription des contrôles ActiveX, consultez [Contrôles ActiveX MFC : distribution de contrôles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md).

   Si vous cliquez sur **Fichier** sous **Ajouter une classe à partir de**, cette zone n’est pas modifiable.

- **Emplacement**

   Spécifie l’emplacement du contrôle ActiveX. Si vous cliquez sur **Fichier** sous **Ajouter une classe à partir de**, vous pouvez indiquer l’emplacement du fichier contenant la bibliothèque de types. Pour accéder à l’emplacement du fichier, cliquez sur le bouton de sélection (...).

   Si vous cliquez sur **Registre** sous **Ajouter une classe à partir de**, cette zone n’est pas modifiable.

- **Interfaces**

   Spécifie les interfaces dans le contrôle ActiveX actuellement sélectionné dans **Contrôles ActiveX disponibles** ou dans la bibliothèque de types dans le fichier spécifié dans **Emplacement**.

   |Bouton de transfert|Description|
   |---------------------|-----------------|
   |**>**|Ajoute l’interface actuellement sélectionnée à la liste **Interfaces**. N’est pas disponible si aucune interface n’est sélectionnée.|
   |**>>**|Ajoute toutes les interfaces dans le contrôle ActiveX actuellement sélectionné dans **Contrôles ActiveX disponibles** ou dans la bibliothèque de types dans le fichier spécifié dans **Emplacement**.|
   |**\<**|Supprime la classe actuellement sélectionnée de la liste **Classes générées**. N’est pas disponible si aucune classe n’est actuellement sélectionnée dans la liste **Classes générées**.|
   |**\<\<**|Supprime toutes les classes de la liste **Classes générées**. N’est pas disponible si la liste **Classes générées** est vide.|

- **Classes générées**

   Spécifie les noms de classe à générer à partir des interfaces ajoutées à l’aide du bouton **>** ou **>>**. Cliquez dans cette zone pour sélectionner une classe, puis utilisez les touches Haut ou bas pour faire défiler la liste. Le nom de chaque classe apparaît dans la zone `Class`, et le nom du fichier, généré par l’Assistant quand vous cliquez sur **Terminer**, apparaît dans la zone **Fichier .h**. Vous ne pouvez sélectionner qu’une seule classe à la fois dans cette zone.

   Pour supprimer une classe, sélectionnez-la dans cette liste et cliquez sur **<**. Vous n’êtes pas obligé de sélectionner une classe dans la zone **Classes générées** pour supprimer toutes les classes. Cliquez sur **<<** pour supprimer toutes les classes de la zone **Classes générées**.

- **Classe**

   Spécifie le nom de la classe sélectionnée dans la zone **Classes générées**. Cette classe est ajoutée par l’Assistant quand vous cliquez sur **Terminer**. Vous pouvez modifier le nom dans la zone **Class**.

- **Fichier .h**

   Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui fourni dans **Classes générées**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui fourni dans **Classes générées**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

   L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe à partir d’un contrôle ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)<br>
[Clients Automation : utilisation des bibliothèques de types](../mfc/automation-clients-using-type-libraries.md)