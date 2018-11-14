---
title: 'Comment : convertir un ruban MFC existant en ressource du ruban'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 627c50758b10ad18e45fc1432340c0eb2dad7b19
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524350"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Comment : convertir un ruban MFC existant en ressource du ruban

Ressources de ruban sont plus faciles à visualiser, modifier et à gérer que les rubans codés manuellement. Cette rubrique décrit comment convertir un ruban codé manuellement dans un projet MFC dans une ressource de ruban.

Vous devez disposer d’un projet MFC existant qui comporte du code qui utilise les classes de ruban MFC, par exemple, [classe CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Pour convertir un ruban MFC à une ressource de ruban

1. Dans Visual Studio, dans un projet MFC existant, ouvrez le fichier source où la `CMFCRibbonBar` objet est initialisé. En règle générale, le fichier est mainfrm.cpp. Ajoutez le code suivant après le code d’initialisation pour le ruban.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Enregistrez et fermez le fichier.

1. Générer et exécuter l’application MFC, puis dans le bloc-notes, ouvrez RibbonOutput.txt et copiez son contenu.

1. Dans Visual Studio, sur le **projet** menu, cliquez sur **ajouter une ressource**. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **ruban** puis cliquez sur **New**.

   Visual Studio crée une ressource de ruban et s’ouvre en mode design. L’ID de ressource de ruban est IDR_RIBBON1, qui s’affiche dans **affichage des ressources**. Le ruban est défini dans le fichier XML de ribbon1.mfcribbon-ms.

1. Dans Visual Studio, ouvrez ribbon1.mfcribbon-ms, supprimez son contenu, puis collez le contenu du RibbonOutput.txt, ce qui vous avez copiée précédemment. Enregistrez et fermez ribbon1.mfcribbon-ms.

1. Ouvrez à nouveau le fichier source où l’objet CMFCRibbonBar est initialisé (en règle générale, mainfrm.cpp) et mettez en commentaire existant code du ruban. Ajoutez le code suivant après le code qui vous commenté.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Générez le projet et exécutez le programme.

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

