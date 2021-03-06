---
description: 'En savoir plus sur : ajout d’une classe MFC à partir d’une bibliothèque de types'
title: Ajout d'une classe MFC à partir d'une bibliothèque de types
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: b5a9979e2581eb3a560736c57c4b1eac4a7e1e81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248370"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Ajout d'une classe MFC à partir d'une bibliothèque de types

Utilisez cet Assistant pour créer une classe MFC à partir d’une interface dans une bibliothèque de types disponible. Vous pouvez ajouter une classe MFC à une [application MFC](../../mfc/reference/creating-an-mfc-application.md), une [DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md) ou un [contrôle ActiveX MFC](../../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
> Vous n’avez pas besoin de créer votre projet MFC avec l’automatisation activée pour ajouter une classe à partir d’une bibliothèque de types.

Une bibliothèque de types contient une description binaire des interfaces exposées par un composant, en définissant les méthodes ainsi que leurs paramètres et types de retour. Vous devez inscrire votre bibliothèque de types pour qu’elle s’affiche dans la liste **bibliothèques de types disponibles** dans l’Assistant Ajouter une classe à partir d’une TypeLib.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Pour ajouter une classe MFC à partir d’une bibliothèque de types

1. Dans **Explorateur de solutions** ou [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter la classe.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

1. Dans le volet modèles de la boîte de dialogue [Ajouter une classe](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) , cliquez sur **classe MFC à partir d’une TypeLib**, puis cliquez sur **ouvrir** pour afficher l' [Assistant Ajout d’une classe à partir d’une TypeLib](../../mfc/reference/add-class-from-typelib-wizard.md).

Dans l’Assistant, vous pouvez ajouter plusieurs classes dans une bibliothèque de types. De même, vous pouvez ajouter des classes à partir de plusieurs bibliothèques de types dans une session d’Assistant unique.

L’Assistant crée une classe MFC, dérivée de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), pour chaque interface que vous ajoutez à partir de la bibliothèque de types sélectionnée. `COleDispatchDriver` implémente le côté client d’OLE Automation.

## <a name="see-also"></a>Voir aussi

[Clients Automation](../../mfc/automation-clients.md)<br/>
[Clients Automation : utilisation des bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)
