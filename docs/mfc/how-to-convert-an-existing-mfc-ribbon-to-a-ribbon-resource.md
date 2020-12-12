---
description: 'En savoir plus sur : Comment : convertir un ruban MFC existant en ressource de ruban'
title: 'Comment : convertir un ruban MFC existant en ressource du ruban'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 825b8b4e3322afd8919ffad0f5e0f73c9d52be78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290282"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Comment : convertir un ruban MFC existant en ressource du ruban

Les ressources du ruban sont plus faciles à visualiser, à modifier et à gérer que les rubans codés manuellement. Cette rubrique explique comment convertir un ruban codé manuellement dans un projet MFC en ressource de ruban.

Vous devez disposer d’un projet MFC existant contenant du code qui utilise les classes de ruban MFC, par exemple, la [classe CMFCRibbonBar](reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Pour convertir un ruban MFC en ressource de ruban

1. Dans Visual Studio, dans un projet MFC existant, ouvrez le fichier source dans lequel l' `CMFCRibbonBar` objet est initialisé. En règle générale, le fichier est MainFrm. cpp. Ajoutez le code suivant après le code d’initialisation pour le ruban.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Enregistrez et fermez le fichier.

1. Générez et exécutez l’application MFC, puis, dans le bloc-notes, ouvrez RibbonOutput.txt et copiez son contenu.

1. Dans Visual Studio, dans le menu **projet** , cliquez sur **Ajouter une ressource**. Dans la boîte de dialogue **Ajouter une ressource** , sélectionnez **ruban** , puis cliquez sur **nouveau**.

   Visual Studio crée une ressource de ruban et l’ouvre en mode Design. L’ID de ressource du ruban est IDR_RIBBON1, qui est affiché dans **affichage des ressources**. Le ruban est défini dans le fichier XML Ribbon1. mfcribbon-ms.

1. Dans Visual Studio, ouvrez Ribbon1. mfcribbon-ms, supprimez son contenu, puis collez le contenu de RibbonOutput.txt que vous avez copié précédemment. Enregistrez et fermez Ribbon1. mfcribbon-ms.

1. Ouvrez de nouveau le fichier source dans lequel l’objet CMFCRibbonBar est initialisé (en général, MainFrm. cpp) et commentez le code de ruban existant. Ajoutez le code suivant après le code que vous avez mis en commentaire.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Générez le projet et exécutez le programme.

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](ribbon-designer-mfc.md)
