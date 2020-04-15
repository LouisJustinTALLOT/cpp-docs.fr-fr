---
title: Ordre des opérations pour la création d'applications de base de données
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372774"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Ordre des opérations pour la création d'applications de base de données

Le tableau suivant montre votre rôle et le rôle du cadre dans la rédaction d’applications de base de données.

> [!NOTE]
> L’environnement visuel et les assistants ne prennent pas en charge DAO (bien que les classes DAO soient incluses et que vous puissiez toujours les utiliser). Microsoft vous recommande d’utiliser ODBC pour de nouveaux projets MFC. Vous ne devez utiliser DAO que pour maintenir les applications existantes.

### <a name="creating-database-applications"></a>Création d’applications de base de données

|Tâche|Ce que vous devez faire|Ce que le framework fait|
|----------|------------|------------------------|
|Décider d’utiliser ou non les classes MFC ODBC ou DAO.|Utilisez ODBC pour de nouveaux projets MFC. Utilisez DAO uniquement pour maintenir les applications existantes. Pour plus d’informations générales, voir l’article [Data Access Programming](../data/data-access-programming-mfc-atl.md).|Le cadre fournit des classes qui soutiennent l’accès aux bases de données.|
|Créez votre application squelette avec des options de base de données.|Exécutez l'Assistant Application MFC. Sélectionnez les options sur la page de support de base de données. Si vous choisissez une option qui crée une vue d’enregistrement, spécifiez également :<br /><br />- Source de données et nom de table<br />- Nom ou nom de requête.|L’assistant d’application MFC crée des fichiers et spécifie les incluts nécessaires. Selon les options que vous spécifiez, les fichiers peuvent inclure une classe de documents.|
|Concevez votre formulaire ou formulaire de base de données.|Utilisez l’éditeur de dialogue Visual CMD pour placer des contrôles sur les ressources du modèle de dialogue pour vos classes de vision d’enregistrement.|Le MFC Application Wizard crée une ressource de modèle de dialogue vide pour vous de remplir.|
|Créez des cours supplémentaires de vue d’enregistrement et de nombre d’enregistrements au besoin.|Utilisez Class View pour créer les classes et l’éditeur de dialogue pour concevoir les vues.|Class View crée des fichiers supplémentaires pour vos nouvelles classes.|
|Créez des objets de recordet au besoin dans votre code. Utilisez chaque ensemble d’enregistrements pour manipuler les enregistrements...|Vos enregistrements sont basés sur les classes dérivées de [CRecordset](../mfc/reference/crecordset-class.md) avec les sorciers.|ODBC utilise l’échange de records sur le terrain (RFX) pour échanger des données entre la base de données et les membres de vos données sur le terrain de votre dossier. Si vous utilisez une vue d’enregistrement, l’échange de données de dialogue (DDX) échange des données entre le jeu d’enregistrement et les contrôles sur la vue d’enregistrement.|
|... ou créez une [base CData](../mfc/reference/cdatabase-class.md) explicite dans votre code pour chaque base de données que vous souhaitez ouvrir.|Basez vos objets d’enregistrement sur les objets de base de données.|L’objet de base de données fournit une interface à la source de données.|
|Liez les colonnes de données à votre dossier dynamiquement.|Dans ODBC, ajoutez du code à votre classe de jeu d’enregistrement dérivé pour gérer la liaison. Voir l’article [Recordset: Dynamically Binding Data Columns (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Voir aussi

[S’appuyer sur le Cadre](../mfc/building-on-the-framework.md)<br/>
[Ordre des opérations pour la génération d’applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Ordre des opérations pour la création d’applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Ordre des opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
