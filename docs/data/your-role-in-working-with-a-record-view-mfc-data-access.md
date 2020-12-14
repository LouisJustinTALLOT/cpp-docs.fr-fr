---
description: 'En savoir plus sur : votre rôle dans l’utilisation d’une vue de l’enregistrement (accès aux données MFC)'
title: Votre rôle dans l'utilisation d'une vue de l'enregistrement (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: f1eff5db930859ca1956286a9364c72b02f2b473
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302606"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Votre rôle dans l'utilisation d'une vue de l'enregistrement (Accès aux données MFC)

Le tableau suivant montre ce que vous devez généralement faire pour travailler avec une vue d'enregistrement et ce que l'infrastructure effectue pour vous.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Utilisation d'une vue d'enregistrement : l'infrastructure et vous

|Vous|L'infrastructure|
|---------|-------------------|
|Utiliser l'éditeur de boîte de dialogue Visual C++ pour concevoir le formulaire.|Crée une ressource de modèle de boîte de dialogue avec des contrôles.|
|Utilisez l ['Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md) pour créer des classes dérivées de [CRecordView](../mfc/reference/crecordview-class.md) et de [CRecordset](../mfc/reference/crecordset-class.md).|Écrit les classes pour vous.|
|Mapper les contrôles de vue d'enregistrement à des données membres de champ de recordset.|Fournit DDX entre les contrôles et les champs du recordset.|
||Fournit des gestionnaires de commandes par défaut pour **déplacer en premier**, **déplacer en dernier**, **déplacer suivant** et déplacer les commandes **précédentes** à partir des menus ou des boutons de la barre d’outils.|
||Met à jour les modifications apportées à la source de données.|
|[Facultatif] Écrire du code pour remplir les zones de liste ou zones de liste déroulante ou d'autres contrôles avec des données à partir d'un second recordset.||
|[Facultatif] Écrire du code pour les validations spéciales.||
|[Facultatif] Écrire du code pour ajouter ou supprimer des enregistrements.||

La programmation basée sur formulaire n'est qu'une approche parmi d'autres de l'utilisation d'une base de données. Pour plus d’informations sur les applications utilisant une autre interface utilisateur, ou sur aucune interface utilisateur, consultez [MFC : utilisation de classes de base de données avec des documents et des vues](../data/mfc-using-database-classes-with-documents-and-views.md) et [MFC : utilisation de classes de base de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md). Pour connaître les autres approches d’affichage des enregistrements de base de données, consultez les classes [CListView](../mfc/reference/clistview-class.md) et [CTreeView](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Voir aussi

[Vues des enregistrements (accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste des pilotes ODBC](../data/odbc/odbc-driver-list.md)
