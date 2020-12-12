---
description: 'En savoir plus sur : séquence d’opérations pour la création d’applications de base de données'
title: Ordre des opérations pour la création d'applications de base de données
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: 86f06ae5200fc8646ccb80bfec4e2814b94f9225
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217586"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Ordre des opérations pour la création d'applications de base de données

Le tableau suivant montre votre rôle et le rôle de l’infrastructure dans l’écriture d’applications de base de données.

> [!NOTE]
> L’environnement et les assistants de Visual C++ ne prennent pas en charge DAO (bien que les classes DAO soient incluses et vous puissiez toujours les utiliser). Microsoft recommande d’utiliser ODBC pour les nouveaux projets MFC. Vous ne devez utiliser que DAO pour gérer les applications existantes.

### <a name="creating-database-applications"></a>Création d’applications de base de données

|Tâche|Ce que vous devez faire|Ce que le framework fait|
|----------|------------|------------------------|
|Décidez s’il faut utiliser les classes ODBC ou DAO de MFC.|Utilisez ODBC pour les nouveaux projets MFC. Utilisez DAO uniquement pour gérer les applications existantes. Pour obtenir des informations générales, consultez l’article programmation de l' [accès aux données](../data/data-access-programming-mfc-atl.md).|L’infrastructure fournit des classes qui prennent en charge l’accès aux bases de données.|
|Créez votre application squelette avec les options de base de données.|Exécutez l'Assistant Application MFC. Sélectionnez Options sur la page prise en charge de la base de données. Si vous choisissez une option qui crée une vue d’enregistrement, spécifiez également :<br /><br />-Source de données et nom ou noms de table<br />-Nom ou nom de la requête.|L’Assistant Application MFC crée des fichiers et spécifie les includes nécessaires. Selon les options que vous spécifiez, les fichiers peuvent inclure une classe Recordset.|
|Concevez votre formulaire ou vos formulaires de base de données.|Utilisez l’éditeur de boîtes de dialogue Visual C++ pour placer des contrôles sur les ressources du modèle de boîte de dialogue pour vos classes d’affichage d’enregistrement.|L’Assistant Application MFC crée une ressource de modèle de boîte de dialogue vide que vous pouvez renseigner.|
|Créez des classes d’affichage des enregistrements et des jeux d’enregistrements supplémentaires si nécessaire.|Utilisez Affichage de classes pour créer les classes et l’éditeur de boîtes de dialogue pour concevoir les vues.|Affichage de classes crée des fichiers supplémentaires pour vos nouvelles classes.|
|Créez des objets Recordset en fonction des besoins dans votre code. Utiliser chaque Recordset pour manipuler les enregistrements...|Vos recordsets sont basés sur les classes dérivées de [CRecordset](../mfc/reference/crecordset-class.md) avec les assistants.|ODBC utilise RFX (Record Field Exchange) pour échanger des données entre la base de données et les membres de données de champ de votre Recordset. Si vous utilisez une vue d’enregistrement, l’échange de données de boîtes de dialogue (DDX) échange des données entre le Recordset et les contrôles de la vue de l’enregistrement.|
|... vous pouvez également créer une [CDatabase](../mfc/reference/cdatabase-class.md) explicite dans votre code pour chaque base de données que vous souhaitez ouvrir.|Basez vos objets Recordset sur les objets de base de données.|L’objet de base de données fournit une interface à la source de données.|
|Liez dynamiquement des colonnes de données à votre jeu d’enregistrements.|Dans ODBC, ajoutez du code à votre classe de Recordset dérivée pour gérer la liaison. Consultez l’article [Recordset : liaison dynamique des colonnes de données (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Voir aussi

[Génération sur le Framework](../mfc/building-on-the-framework.md)<br/>
[Séquence d’opérations pour la génération d’applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Séquence d’opérations pour la création d’applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Séquence d’opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
