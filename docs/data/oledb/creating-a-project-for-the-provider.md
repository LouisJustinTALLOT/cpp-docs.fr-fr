---
title: Création d’un projet pour le fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f4049190ac30cfff634d4cfef82410ccfdf1314
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063079"
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