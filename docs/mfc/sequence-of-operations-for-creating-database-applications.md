---
title: Ordre des opérations pour la création d’Applications de base de données | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbe18e9733388cc6e43f6ca3de520596c713b783
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381327"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Ordre des opérations pour la création d'applications de base de données
Le tableau suivant indique votre rôle et l’infrastructure dans l’écriture d’applications de base de données.  
  
> [!NOTE]
>  Les Assistants et l’environnement Visual C++ ne prennent pas en charge les DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser ODBC pour les nouveaux projets MFC. Vous devez uniquement utiliser DAO dans la maintenance des applications existantes.  
  
### <a name="creating-database-applications"></a>Création d’Applications de base de données  
  
|Tâche|Ce que vous devez faire|Ce que le framework fait|  
|----------|------------|------------------------|  
|Décidez s’il faut utiliser les classes ODBC MFC ou DAO.|Utilisation de ODBC pour les nouveaux projets MFC. Utilisez DAO uniquement aux applications existantes. Pour plus d’informations, consultez l’article [programmation d’accès aux données](../data/data-access-programming-mfc-atl.md).|Le framework fournit des classes qui prennent en charge l’accès de base de données.|  
|Créer votre application squelette avec les options de base de données.|Exécutez l’Assistant Application MFC. Sélectionnez les options dans la page prise en charge de la base de données. Si vous choisissez une option qui crée une vue d’enregistrement, spécifiez également :<br /><br /> -Les données source et la table ou les noms<br />-Les noms des requêtes.|L’Assistant Application MFC crée des fichiers et spécifie que les nécessaires inclut. Selon les options que vous spécifiez, les fichiers peuvent inclure une classe de recordset.|  
|Concevoir votre base de données ou les formes.|Utilisez l’éditeur de boîte de dialogue Visual C++ pour placer des contrôles sur les ressources de modèle de boîte de dialogue pour vos classes d’affichage de l’enregistrement.|L’Assistant Application MFC crée une ressource de modèle de boîte de dialogue vide pour vous renseigner.|  
|Créer des classes d’affichage et le jeu d’enregistrements enregistrement supplémentaires en fonction des besoins.|Utilisez l’affichage de classes pour créer les classes et la boîte de dialogue Éditeur pour concevoir les vues.|Affichage de classes crée des fichiers supplémentaires pour vos nouvelles classes.|  
|Créer des objets de jeu d’enregistrements en fonction des besoins dans votre code. Chaque jeu d’enregistrements permet de manipuler des enregistrements...|Les jeux d’enregistrements est basés sur les classes dérivées de [CRecordset](../mfc/reference/crecordset-class.md) avec les Assistants.|ODBC utilise l’échange de champs d’enregistrements (RFX) pour échanger des données entre la base de données et les membres de données de champ de votre recordset. Si vous utilisez une vue d’enregistrement, échange de données de boîtes de dialogue (DDX) échange des données entre le jeu d’enregistrements et les contrôles sur la vue de l’enregistrement.|  
|.. ou créer explicite [CDatabase](../mfc/reference/cdatabase-class.md) dans votre code pour chaque base de données que vous souhaitez ouvrir.|Votre jeu d’enregistrements des objets de base sur les objets de base de données.|L’objet de base de données fournit une interface pour la source de données.|  
|Lier dynamiquement des colonnes de données à votre jeu d’enregistrements.|Dans ODBC, ajoutez le code à votre classe de recordset dérivée pour gérer la liaison. Consultez l’article [Recordset : liaison dynamique des colonnes de données (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir de l’infrastructure](../mfc/building-on-the-framework.md)   
 [Ordre des opérations pour la génération d’Applications MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Ordre des opérations pour la création d’Applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Ordre des opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
