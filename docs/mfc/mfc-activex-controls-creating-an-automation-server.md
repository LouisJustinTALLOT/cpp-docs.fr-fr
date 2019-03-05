---
title: 'Contrôles ActiveX MFC : Création d’un serveur Automation'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: 01f0162e124c5c49d45ce4a90f5243c88b09b5a0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303727"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Contrôles ActiveX MFC : Création d’un serveur Automation

Vous pouvez développer un contrôle ActiveX MFC en tant que serveur Automation pour les besoins de l’incorporation de ce contrôle dans une autre application et en appelant des méthodes dans le contrôle de l’application par programme. Un tel contrôle serait toujours disponible pour être hébergé dans un conteneur de contrôles ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Pour créer un contrôle en tant que serveur Automation

1. [Créer](../mfc/reference/mfc-activex-control-wizard.md) le contrôle.

1. [Ajouter des méthodes](../mfc/mfc-activex-controls-methods.md).

1. Substituer [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed).

1. Générer le contrôle.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Pour accéder par programme les méthodes dans un serveur Automation

1. Créer une application, par exemple, un [exe MFC](../mfc/reference/mfc-application-wizard.md).

1. Au début de la `InitInstance` de fonction, ajoutez la ligne suivante :

   [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. Dans l’affichage de classes, cliquez sur le nœud du projet et sélectionnez **Ajout de classes d’une typelib** pour importer la bibliothèque de types.

   Cette opération ajoute des fichiers avec le .cpp et .h d’extensions de nom de fichier au projet.

1. Dans le fichier d’en-tête de la classe où vous appellerez une ou plusieurs méthodes dans le contrôle ActiveX, ajoutez la ligne suivante : `#include filename.h`, où le nom de fichier est le nom du fichier d’en-tête qui a été créé lorsque vous avez importé de la bibliothèque de types.

1. Dans la fonction où un appel ne sera passé à une méthode dans le contrôle ActiveX, ajoutez le code qui crée un objet de la classe du contrôle wrapper et créer l’objet ActiveX. Par exemple, le code MFC suivant instancie un `CCirc` contrôle, obtient la propriété de légende et affiche le résultat de cas de clic sur le bouton OK dans une boîte de dialogue :

   [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Si vous ajoutez des méthodes pour le contrôle ActiveX une fois que vous l’utilisez dans une application, vous pouvez commencer à l’aide de la dernière version du contrôle dans l’application en supprimant les fichiers qui ont été créés lors de l’importation de la bibliothèque de types. Puis importez de nouveau la bibliothèque de types.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
