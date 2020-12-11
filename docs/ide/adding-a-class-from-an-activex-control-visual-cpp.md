---
description: 'En savoir plus sur : ajouter une classe à partir d’un contrôle ActiveX'
title: Ajouter une classe à partir d’un contrôle ActiveX
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
- ActiveX Control Wizard
- add class from ActiveX control wizard [C++]
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: 3a5ad387abb061ca554074002d4a8fab87fd529a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160231"
---
# <a name="add-a-class-from-an-activex-control"></a>Ajouter une classe à partir d’un contrôle ActiveX

Utilisez cet Assistant pour créer une classe MFC à partir d’une interface dans un contrôle ActiveX disponible. Vous pouvez ajouter une classe MFC à une [application MFC](../mfc/reference/creating-an-mfc-application.md), une [DLL MFC](../mfc/reference/creating-an-mfc-dll-project.md) ou un [contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).

> [!WARNING]
> Dans Visual Studio 2017 version 15.9, Microsoft a déprécié cet Assistant Code, et nous le supprimerons dans une version ultérieure de Visual Studio. Cet Assistant est rarement utilisé. La prise en charge générale d’ATL et MFC n’est pas affectée par la suppression de cet Assistant. Si vous souhaitez partager vos commentaires sur cette dépréciation, veuillez remplir [cette enquête](https://www.surveymonkey.com/r/QDWKKCN). Vos commentaires sont précieux pour nous.
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> Il n’est pas nécessaire de créer un projet MFC avec l’option Automation activée pour ajouter une classe à partir d’un contrôle ActiveX.

Un contrôle ActiveX est un composant logiciel réutilisable qui repose sur le modèle COM (Component Object Model) et prend en charge une large gamme de fonctionnalités OLE. Il peut être personnalisé pour répondre à de nombreux besoins logiciels. Vous pouvez utiliser des contrôles ActiveX dans des conteneurs de contrôles ActiveX ordinaires ou sur Internet dans des pages web.

**Pour ajouter une classe MFC à partir d’un contrôle ActiveX**

1. Dans **l’Explorateur de solutions** ou dans [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter la classe du contrôle ActiveX.

1. Dans le menu contextuel, choisissez **Ajouter**, puis **Ajouter une classe**.

1. Dans la boîte de dialogue [Ajouter une classe](./adding-a-class-visual-cpp.md#add-class-dialog-box), dans le volet **Modèles**, choisissez **Classe MFC à partir du contrôle ActiveX**, puis **Ouvrir** pour afficher l’[Assistant Ajout d’une classe à partir d’un contrôle ActiveX](#add-class-from-activex-control-wizard).

Dans l’Assistant, vous pouvez ajouter plusieurs interfaces dans un contrôle ActiveX. Vous pouvez également créer des classes à partir de plusieurs contrôles ActiveX dans une même session d’Assistant.

Vous pouvez ajouter des classes à partir des contrôles ActiveX inscrits dans votre système ou situés dans des fichiers bibliothèques de types (.tlb, .olb, .dll, .ocx ou .exe) sans avoir à les inscrire au préalable dans votre système. Pour plus d’informations sur l’inscription des contrôles ActiveX, consultez [Inscription des contrôles OLE](../mfc/reference/registering-ole-controls.md).

L’Assistant crée une classe MFC, dérivée de [CWnd](../mfc/reference/cwnd-class.md) ou de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), pour chaque interface que vous ajoutez à partir du contrôle ActiveX sélectionné.

## <a name="in-this-section"></a>Dans cette section

- [Assistant Ajouter une classe à partir d’un contrôle ActiveX](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>Assistant Ajout d’une classe à partir d’un contrôle ActiveX

Utilisez cet Assistant pour ajouter une classe MFC à partir d’un contrôle ActiveX disponible. L’Assistant crée une classe pour chaque interface que vous ajoutez à partir du contrôle ActiveX sélectionné.

- **Ajouter une classe à partir de**

  Spécifie l’emplacement de la bibliothèque de types à partir de laquelle la classe est créée.

  |Option|Description|
  |------------|-----------------|
  |**Registre**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Contrôles ActiveX disponibles**.|
  |**File**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais elle est stockée dans un fichier. Spécifiez l’emplacement du fichier dans **Emplacement**.|

- **Contrôles ActiveX disponibles**

  Spécifie les contrôles ActiveX actuellement inscrits dans le système. Sélectionnez un contrôle ActiveX dans cette liste pour afficher ses interfaces dans la liste **Interfaces**. Pour plus d’informations sur l’inscription des contrôles ActiveX, consultez [Contrôles ActiveX MFC : distribution de contrôles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md).

  Si vous sélectionnez **Fichier** sous **Ajouter une classe à partir de**, cette zone n’est pas modifiable.

- **Lieu**

  Spécifie l’emplacement du contrôle ActiveX. Si vous sélectionnez **Fichier** sous **Ajouter une classe à partir de**, vous pouvez indiquer l’emplacement du fichier contenant la bibliothèque de types. Pour accéder à l’emplacement du fichier, sélectionnez le bouton de sélection (...).

  Si vous sélectionnez **Registre** sous **Ajouter une classe à partir de**, cette zone n’est pas modifiable.

- **Interfaces**

  Spécifie les interfaces dans le contrôle ActiveX. L’Assistant utilise les interfaces de la sélection actuelle dans **Contrôles ActiveX disponibles**, ou il utilise celles du fichier de bibliothèque de types spécifié dans **Emplacement**.

  |Bouton de transfert|Description|
  |---------------------|-----------------|
  |**>**|Ajoute l’interface actuellement sélectionnée à la liste **Interfaces**. N’est pas disponible si aucune interface n’est sélectionnée.|
  |**>>**|Ajoute toutes les interfaces dans le contrôle ActiveX. L’Assistant utilise les interfaces de la sélection actuelle dans **Contrôles ActiveX disponibles**, ou il utilise celles du fichier de bibliothèque de types spécifié dans **Emplacement**.|
  |**\<**|Supprime la classe actuellement sélectionnée de la liste **Classes générées**. N’est pas disponible si aucune classe n’est actuellement sélectionnée dans la liste **Classes générées**.|
  |**\<\<**|Supprime toutes les classes de la liste **Classes générées**. N’est pas disponible si la liste **Classes générées** est vide.|

- **Classes générées**

  Spécifie les noms de classes à générer à partir des interfaces ajoutées à l’aide du **>** **>>** bouton ou. Vous pouvez cocher cette case pour sélectionner une classe, puis utiliser les touches Haut et Bas pour faire défiler la liste. Quand vous sélectionnez **Terminer**, vous pouvez afficher chaque nom de classe générée dans la zone **Classe** et chaque nom de fichier généré dans la zone **Fichier .h**. Vous ne pouvez sélectionner qu’une seule classe à la fois dans cette zone.

  Vous pouvez supprimer une classe en la sélectionnant dans cette liste et en sélectionnant **<** . Vous n’avez pas besoin de sélectionner une classe dans la zone **Classes générées** pour supprimer toutes les classes. En sélectionnant **<<** , vous supprimez toutes les classes dans la zone **classes générées** .

- **Classe**

   Spécifie le nom de la classe sélectionnée dans la zone **Classes générées**. Cette classe est ajoutée par l’Assistant quand vous sélectionnez **Terminer**. Vous pouvez modifier le nom dans la zone **Class**.

- **Fichier .h**

  Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui fourni dans **Classes générées**. Sélectionnez le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous sélectionniez **Terminer** pour l’enregistrer à l’emplacement sélectionné.

  L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant puis **Terminer**, l’Assistant vous invite à préciser s’il faut ajouter la déclaration de la classe au contenu du fichier. Sélectionnez **Oui** pour l’ajouter au fichier ou **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

  Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui fourni dans **Classes générées**. Sélectionnez le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous sélectionniez **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

  L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant puis **Terminer**, l’Assistant vous invite à préciser s’il faut ajouter l’implémentation de la classe au contenu du fichier. Sélectionnez **Oui** pour l’ajouter au fichier ou **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.
