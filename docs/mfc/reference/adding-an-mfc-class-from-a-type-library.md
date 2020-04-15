---
title: Ajout d'une classe MFC à partir d'une bibliothèque de types
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371723"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Ajout d'une classe MFC à partir d'une bibliothèque de types

Utilisez cet assistant pour créer une classe MFC à partir d’une interface dans une bibliothèque de type disponible. Vous pouvez ajouter une classe MFC à une [application MFC](../../mfc/reference/creating-an-mfc-application.md), une [DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md) ou un [contrôle ActiveX MFC](../../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
> Vous n’avez pas besoin de créer votre projet MFC avec Automation activé pour ajouter une classe à partir d’une bibliothèque de type.

Une bibliothèque de type contient une description binaire des interfaces exposées par un composant, définissant les méthodes avec leurs paramètres et les types de retour. Votre bibliothèque de type doit être enregistrée pour qu’elle apparaisse dans la liste **des bibliothèques de type disponible** dans la classe Add de Typelib Wizard. Voir « Inside Distributed COM: Type Libraries and Language Integration » dans la bibliothèque MSDN pour plus d’informations.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Pour ajouter une classe MFC à partir d’une bibliothèque de type

1. Dans **solution Explorer** ou [Class View](/visualstudio/ide/viewing-the-structure-of-code), cliquez à droite sur le nom du projet auquel vous souhaitez ajouter la classe.

1. À partir du menu raccourci, cliquez sur **Ajouter,** puis cliquez sur **Ajouter classe**.

1. Dans la boîte de dialogue [Add Class,](../../ide/add-class-dialog-box.md) dans le volet Templates, cliquez sur **MFC Class de Typelib**, puis cliquez sur **Open** pour afficher la classe Add [de Typelib Wizard](../../mfc/reference/add-class-from-typelib-wizard.md).

Dans l’assistant, vous pouvez ajouter plus d’une classe dans une bibliothèque de type. De même, vous pouvez ajouter des classes de plus d’une bibliothèque de type dans une seule session de sorcier.

L’assistant crée une classe MFC, dérivée de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), pour chaque interface que vous ajoutez à partir de la bibliothèque de type sélectionnée. `COleDispatchDriver`met en œuvre le côté client de l’automatisation OLE.

## <a name="see-also"></a>Voir aussi

[Clients Automation](../../mfc/automation-clients.md)<br/>
[Clients Automation : utilisation des bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)
