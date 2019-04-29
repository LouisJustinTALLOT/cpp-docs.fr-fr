---
title: Création d'un projet pour le fournisseur
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: dc085b1f663369033947ed2a5577f334dd79c0aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361990"
---
# <a name="creating-a-project-for-the-provider"></a>Création d'un projet pour le fournisseur

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>Pour créer un projet dans lequel résidera le fournisseur OLE DB

1. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

1. Dans le **Types de projets** volet, cliquez sur le **installé** > **Visual C++** > **MFC/ATL** dossier. Dans le **modèles** volet, cliquez sur **projet ATL**.

    > [!NOTE]
    > Dans les versions précédentes de Visual Studio, recherchez le type de projet sous **installé** > **modèles** > **Visual C++**  >  **ATL**.

1. Dans le **nom** zone, entrez un nom pour le projet, puis cliquez sur **OK**.

   Le **Assistant Projet ATL** s’affiche.

1. Dans le **Assistant Projet ATL**, choisissez **bibliothèque de liens dynamiques (DLL)** pour **Type d’Application**.

1. Cliquez sur **Terminer**.

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)