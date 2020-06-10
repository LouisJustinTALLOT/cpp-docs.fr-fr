---
title: "Contrôles ActiveX MFC : création d'un serveur Automation"
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: f2c941e43e810845560b4c35c558ec70248c21ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622382"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Contrôles ActiveX MFC : création d'un serveur Automation

Vous pouvez développer un contrôle ActiveX MFC en tant que serveur Automation afin d’incorporer par programmation ce contrôle dans une autre application et d’appeler des méthodes dans le contrôle à partir de l’application. Ce type de contrôle serait toujours disponible pour être hébergé dans un conteneur de contrôles ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Pour créer un contrôle en tant que serveur Automation

1. [Créez](reference/mfc-activex-control-wizard.md) le contrôle.

1. [Ajoutez des méthodes](mfc-activex-controls-methods.md).

1. Remplacez [IsInvokeAllowed](reference/colecontrol-class.md#isinvokeallowed).

1. Générez le contrôle.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Pour accéder par programmation aux méthodes d’un serveur Automation

1. Créer une application, par exemple un [exe MFC](reference/mfc-application-wizard.md).

1. Au début de la `InitInstance` fonction, ajoutez la ligne suivante :

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. Dans Affichage de classes, cliquez avec le bouton droit sur le nœud du projet, puis sélectionnez **Ajouter une classe à partir d’une TypeLib** pour importer la bibliothèque de types.

   Cette opération ajoute les fichiers portant les extensions de nom de fichier. h et. cpp au projet.

1. Dans le fichier d’en-tête de la classe où vous allez appeler une ou plusieurs méthodes dans le contrôle ActiveX, ajoutez la ligne suivante : `#include filename.h` , où nom de fichier est le nom du fichier d’en-tête qui a été créé lorsque vous avez importé la bibliothèque de types.

1. Dans la fonction où un appel est effectué à une méthode dans le contrôle ActiveX, ajoutez le code qui crée un objet de la classe wrapper du contrôle et créez l’objet ActiveX. Par exemple, le code MFC suivant instancie un `CCirc` contrôle, obtient la propriété Caption et affiche le résultat lorsque l’utilisateur clique sur le bouton OK dans une boîte de dialogue :

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Si vous ajoutez des méthodes au contrôle ActiveX après l’avoir utilisé dans une application, vous pouvez commencer à utiliser la version la plus récente du contrôle dans l’application en supprimant les fichiers qui ont été créés lors de l’importation de la bibliothèque de types. Ensuite, importez à nouveau la bibliothèque de types.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
